# Gabarito comentado — 60 exercícios

Tente resolver antes de consultar. Cada seção pressupõe a preparação e o exemplo do módulo correspondente. Os notebooks de soluções são independentes.


## 01 • Sua primeira tabela

### 01.1 — Execute p.head(3). Usando a saída, diga o que representa uma linha e qual é a massa do primeiro animal.

```python
print(p.head(3))
# Uma linha representa a observação de um animal.
print('Massa do primeiro animal (g):', p.iloc[0]['body_mass_g'])
```

### 01.2 — Mostre p.shape. Depois exiba apenas o número de linhas e apenas o número de colunas.

```python
print(p.shape)
print('Linhas:', p.shape[0])
print('Colunas:', p.shape[1])
# shape não usa parênteses; seus elementos começam na posição zero.
```

### 01.3 — Selecione species e mostre três valores. Depois selecione species e island juntas e compare os formatos.

```python
print(p['species'].head(3))
print(p[['species','island']].head(3))
# Uma coluna por nome devolve Series; uma lista de nomes devolve DataFrame.
```

### 01.4 — Mostre as quatro últimas linhas com tail. Explique por que o índice do resultado não começa em zero.

```python
print(p.tail(4))
# tail preserva os rótulos das linhas originais; não cria uma numeração nova.
```

### 01.5 — Execute p.info(). Compare os valores presentes de body_mass_g com o total de linhas. Quantas massas faltam?

```python
p.info()
# O relatório informa 342 massas presentes entre 344 linhas.
print('Massas ausentes:', p['body_mass_g'].isna().sum())
# isna e sum serão explicados em detalhe na aula 3; aqui servem para conferir a leitura do relatório.
```


## 02 • Selecionar, filtrar e ordenar

### 02.1 — Liste apenas pinguins da ilha Dream.

```python
print(p.loc[p['island'].eq('Dream')])
```

### 02.2 — Selecione species, sex e body_mass_g, nessa ordem.

```python
print(p[['species','sex','body_mass_g']].head())
```

### 02.3 — Encontre animais Adelie ou Chinstrap com massa de pelo menos 4.000 g.

```python
print(p.loc[p['species'].isin(['Adelie','Chinstrap']) & p['body_mass_g'].ge(4000)])
```

### 02.4 — Mostre os cinco animais com maior comprimento de nadadeira.

```python
print(p.sort_values('flipper_length_mm', ascending=False).head(5))
```

### 02.5 — Pegue as posições 10 a 14, inclusive. Explique por que o limite usado é 15.

```python
print(p.iloc[10:15])
# O limite superior de iloc fica fora da seleção.
```


## 03 • Tipos, ausências e qualidade

### 03.1 — Quais colunas possuem pelo menos uma ausência?

```python
n = p.isna().sum(); print(n[n.gt(0)])
```

### 03.2 — Calcule a porcentagem de massas ausentes.

```python
print(p['body_mass_g'].isna().mean()*100)
```

### 03.3 — Crie uma tabela apenas com massa e comprimento de nadadeira presentes. Conte a perda de linhas.

```python
completos = p.dropna(subset=['body_mass_g','flipper_length_mm'])
print('Removidas:',len(p)-len(completos))
```

### 03.4 — Converta a Series didática ["10", "erro", None] para número e conte ausências resultantes.

```python
s = pd.Series(['10','erro',None]); n = pd.to_numeric(s, errors='coerce')
print(n); print(n.isna().sum())
# Uma falha de conversão e uma ausência original.
```

### 03.5 — Conte duplicatas exatas, sem removê-las. Por que isso não basta para excluir observações?

```python
print(p.duplicated().sum())
# Sem um identificador individual, medições iguais não provam duplicação indevida.
```


## 04 • Criar colunas e tratar textos

### 04.1 — Crie bill_length_cm a partir de bill_length_mm, preservando p.

```python
q = p.assign(bill_length_cm=p['bill_length_mm']/10)
print(q[['bill_length_mm','bill_length_cm']].head())
```

### 04.2 — Padronize a Series didática [" Dream ", "BISCOE", None] em minúsculas e sem espaços externos.

```python
s = pd.Series([' Dream ','BISCOE',None], dtype='string')
print(s.str.strip().str.lower())
```

### 04.3 — Traduza male/female para masculino/feminino em uma nova coluna. Preserve ausências.

```python
q = p.assign(sexo_pt=p['sex'].map({'male':'masculino','female':'feminino'}))
print(q[['sex','sexo_pt']].head())
```

### 04.4 — Selecione espécies cujo nome contém a sequência literal elie, sem diferenciar caixa.

```python
print(p.loc[p['species'].str.contains('elie', case=False, regex=False, na=False)])
```

### 04.5 — Crie a razão entre comprimento e profundidade do bico, protegendo denominadores iguais a zero.

```python
den = p['bill_depth_mm'].where(p['bill_depth_mm'].ne(0))
print(p.assign(razao_bico=p['bill_length_mm']/den).head())
```


## 05 • Resumir dados com groupby

### 05.1 — Conte animais por espécie.

```python
print(p.groupby('species', observed=True).size())
```

### 05.2 — Calcule mediana e desvio padrão da massa por espécie.

```python
print(p.groupby('species', observed=True)['body_mass_g'].agg(['median','std']))
```

### 05.3 — Conte animais por ilha e sexo, incluindo sexo ausente.

```python
print(p.groupby(['island','sex'], dropna=False, observed=True).size())
```

### 05.4 — Crie uma coluna com a média de massa da espécie de cada animal e outra com seu desvio dessa média.

```python
media = p.groupby('species', observed=True)['body_mass_g'].transform('mean')
q = p.assign(media_especie=media, desvio_g=p['body_mass_g']-media)
print(q.head())
```

### 05.5 — Compare size e count para a massa por espécie. Interprete diferenças.

```python
print(p.groupby('species', observed=True)['body_mass_g'].agg(['size','count']))
# size inclui observações sem massa; count não.
```


## 06 • Cruzar tabelas e mudar o formato

### 06.1 — Cruze as traduções e confirme que a quantidade de linhas permaneceu igual.

```python
q = p.merge(nomes, on='species', how='left', validate='many_to_one')
assert len(q)==len(p)
print(q[['species','nome_pt']].head())
```

### 06.2 — Construa uma tabela de massa média por espécie (linhas) e sexo (colunas).

```python
print(p.pivot_table(index='species', columns='sex', values='body_mass_g', aggfunc='mean', observed=True))
```

### 06.3 — Transforme bill_length_mm e bill_depth_mm em linhas, preservando species como identificador.

```python
print(p.melt(id_vars=['species'], value_vars=['bill_length_mm','bill_depth_mm'], var_name='medida', value_name='mm').head())
```

### 06.4 — Divida p em dois blocos e una novamente. Confirme que os dados são iguais.

```python
q = pd.concat([p.iloc[:100],p.iloc[100:]], ignore_index=True)
pd.testing.assert_frame_equal(p,q)
print('Reconstrução correta')
```

### 06.5 — Duplique uma chave da tabela de tradução e demonstre que validate impede a multiplicação silenciosa.

```python
ruim = pd.concat([nomes,nomes.iloc[:1]], ignore_index=True)
try:
    p.merge(ruim, on='species', validate='many_to_one')
except pd.errors.MergeError as erro:
    print(type(erro).__name__, str(erro))
```


## 07 • Dados reais de comércio: diagnóstico e regras

### 07.1 — Conte faturas distintas e compare com a quantidade de linhas brutas.

```python
print('Linhas:',len(r),'Faturas:',r['InvoiceNo'].nunique())
```

### 07.2 — Conte linhas de cancelamento, quantidade negativa, preço não positivo e cliente ausente. As categorias podem se sobrepor.

```python
print(pd.Series({'canceladas':cancelada.sum(), 'quantidade_negativa':r['Quantity'].lt(0).sum(), 'preco_nao_positivo':r['UnitPrice'].le(0).sum(), 'sem_cliente':r['CustomerID'].isna().sum()}))
```

### 07.3 — Calcule o valor total da visão positiva e declare moeda e definição.

```python
print('Receita bruta elegível (GBP):', round(v['valor'].sum(),2))
# Não desconta devoluções nem mede lucro.
```

### 07.4 — Liste os dez países de maior receita nessa visão.

```python
print(v.groupby('Country')['valor'].sum().sort_values(ascending=False).head(10))
```

### 07.5 — Calcule ticket médio por fatura; não use a média das linhas de itens.

```python
pedidos = v.groupby('InvoiceNo')['valor'].sum()
print('Ticket médio de faturas elegíveis (GBP):',pedidos.mean())
```


## 08 • Datas, calendário e janelas

### 08.1 — Some receita elegível por ano e mês usando dt.to_period.

```python
print(v.groupby(v['InvoiceDate'].dt.to_period('M'))['valor'].sum())
```

### 08.2 — Calcule a receita por dia e complete o calendário com zero, documentando a hipótese.

```python
diario = v.groupby(v['InvoiceDate'].dt.normalize())['valor'].sum()
diario = diario.reindex(pd.date_range(diario.index.min(),diario.index.max(),freq='D'), fill_value=0)
print(diario.head())
# Hipótese: dias não registrados dentro da cobertura tiveram zero venda elegível.
```

### 08.3 — Calcule a média móvel de sete dias, exigindo sete dias para produzir resultado.

```python
print(diario.rolling(7,min_periods=7).mean().head(10))
```

### 08.4 — Calcule variação mensal e substitua resultados com denominador anterior zero por ausência.

```python
anterior = mensal.shift(1)
crescimento = mensal.div(anterior.where(anterior.ne(0))).sub(1).mul(100)
print(crescimento)
# Avalie cobertura antes de interpretar dezembro.
```

### 08.5 — Converta ["31/01/2026", "data ruim"] com formato brasileiro e conte falhas.

```python
datas = pd.to_datetime(pd.Series(['31/01/2026','data ruim']),format='%d/%m/%Y',errors='coerce')
print(datas); print('Falhas:',datas.isna().sum())
```


## 09 • Indicadores e segmentação de clientes

### 09.1 — Mostre dez clientes com maior valor monetário.

```python
print(rfm.sort_values('monetario',ascending=False).head(10))
```

### 09.2 — Calcule a porcentagem da receita elegível sem identificação de cliente.

```python
print(v.loc[v['CustomerID'].isna(),'valor'].sum()/v['valor'].sum()*100)
```

### 09.3 — Selecione clientes com recência até 30 dias e pelo menos cinco faturas. A regra é didática, não um modelo validado.

```python
print(rfm.loc[rfm['recencia_dias'].le(30) & rfm['frequencia'].ge(5)].head())
```

### 09.4 — Calcule a participação acumulada dos clientes na receita identificada, em ordem decrescente.

```python
ordenado = rfm.sort_values('monetario',ascending=False)
print(ordenado.assign(participacao_acumulada=ordenado['monetario'].cumsum()/ordenado['monetario'].sum()).head())
```

### 09.5 — Valide que a soma monetária por cliente coincide com o total identificado.

```python
import math
assert math.isclose(rfm['monetario'].sum(),identificados['valor'].sum(),rel_tol=1e-10)
print('Totais reconciliados')
```


## 10 • Desempenho, arquivos e limites

### 10.1 — Leia apenas Country, Quantity e UnitPrice das primeiras cem linhas do CSV da loja.

```python
mini = pd.read_csv(DADOS/'online_retail.csv',usecols=['Country','Quantity','UnitPrice'],nrows=100)
print(mini.head())
```

### 10.2 — Mostre a memória total de r em MiB.

```python
print(r.memory_usage(deep=True).sum()/1024**2)
```

### 10.3 — Compare massa média pela divisão soma/contagem com mean.

```python
s = p['body_mass_g']
assert abs(s.sum()/s.count()-s.mean())<1e-10
print(s.mean())
```

### 10.4 — Some quantidades brutas por país em blocos de cem mil linhas. Compare com leitura completa.

```python
parciais=[]
for bloco in pd.read_csv(DADOS/'online_retail.csv',usecols=['Country','Quantity'],chunksize=100000):
    parciais.append(bloco.groupby('Country')['Quantity'].sum())
total_blocos=pd.concat(parciais).groupby(level=0).sum().sort_index()
total_completo=r.groupby('Country')['Quantity'].sum().sort_index()
pd.testing.assert_series_equal(total_blocos,total_completo)
print('Agregação por blocos conferida')
```

### 10.5 — Exporte o resumo por espécie para CSV sem gravar o índice. Releia e confira as dimensões.

```python
destino = SAIDAS/'resumo_especies.csv'
resumo.to_csv(destino,index=False)
relido=pd.read_csv(destino)
assert relido.shape==resumo.shape
print(destino)
```


## 11 • Análises reproduzíveis e validação

### 11.1 — Confirme que preparar_vendas não modifica a tabela de entrada.

```python
copia = r.copy(deep=True)
_ = preparar_vendas(r)
pd.testing.assert_frame_equal(r,copia)
print('Entrada preservada')
```

### 11.2 — Demonstre a falha de contrato ao remover Country.

```python
try:
    preparar_vendas(r.drop(columns='Country'))
except ValueError as erro:
    print(erro)
```

### 11.3 — Valide quantidade, preço, data e valor nas vendas elegíveis.

```python
assert v['Quantity'].gt(0).all()
assert v['UnitPrice'].gt(0).all()
assert v['InvoiceDate'].notna().all()
pd.testing.assert_series_equal(v['valor'],(v['Quantity']*v['UnitPrice']).rename('valor'))
print('Regras conferidas')
```

### 11.4 — Reconcilie a receita mensal com a receita total.

```python
assert math.isclose(mensal.sum(),v['valor'].sum(),rel_tol=1e-10)
print('Resumo mensal reconciliado')
```

### 11.5 — Produza um registro com versão do pandas, linhas lidas, linhas elegíveis e intervalo observado.

```python
registro = {'pandas':pd.__version__,'linhas_brutas':len(r),'linhas_elegiveis':len(v),'inicio':str(r['InvoiceDate'].min()),'fim':str(r['InvoiceDate'].max())}
print(registro)
```


## 12 • Comunicação e entrega profissional

### 12.1 — Prepare uma tabela com receita, faturas e ticket médio por país.

```python
por_pais=v.groupby('Country').agg(receita_GBP=('valor','sum'),faturas=('InvoiceNo','nunique'))
por_pais['ticket_GBP']=por_pais['receita_GBP']/por_pais['faturas']
print(por_pais.sort_values('receita_GBP',ascending=False).head())
```

### 12.2 — Exporte os indicadores por país e o RFM para arquivos separados.

```python
por_pais.to_csv(SAIDAS/'indicadores_paises.csv')
rfm.to_csv(SAIDAS/'rfm.csv')
print('Relatórios exportados')
```

### 12.3 — Desenhe barras horizontais dos cinco maiores países com eixo em GBP.

```python
import matplotlib
matplotlib.use('Agg')
import matplotlib.pyplot as plt
ax=paises.sort_values().plot.barh(title='Top 5 países — vendas positivas elegíveis')
ax.set_xlabel('Receita bruta elegível (GBP)'); ax.set_ylabel('País')
plt.tight_layout(); plt.savefig(SAIDAS/'top_paises.png',dpi=130); plt.close()
print('Gráfico salvo')
```

### 12.4 — Escreva uma conclusão factual com participação do maior país e uma limitação.

```python
participacao=paises.iloc[0]/v['valor'].sum()*100
print(f'{paises.index[0]} representa {participacao:.1f}% da receita elegível. Não reconciliamos cancelamentos e o período final está incompleto.')
```

### 12.5 — Crie um checklist de publicação e explique quando impedir a entrega.

```python
checklist = ['Fonte e período registrados','Regras de elegibilidade documentadas','Totais reconciliados','Ausências auditadas','Unidades e granularidade explícitas','Execução do início ao fim','Limitações apresentadas']
print('\n'.join(checklist))
# Impeça a entrega quando uma falha de qualidade alterar o significado dos indicadores ou a reconciliação falhar.
```

