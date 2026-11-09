# Pandas: do primeiro DataFrame à prática profissional

Material em português • edição de estudo de 9 de novembro de 2026.


## Preparação para quem já tem Jupyter Notebook

Você já tem Jupyter Notebook? Comece por esta opção. Não precisa instalar o JupyterLab nem usar o VS Code para fazer o curso.

1. Descompacte o pacote completo. Abra a pasta curso_pandas no Jupyter.
2. Abra notebooks/00_comecar_aqui.ipynb. Ele orienta a execução, a localização dos dados e a primeira leitura.
3. Execute uma célula por vez com Shift + Enter. Aguarde a execução terminar e observe a saída antes de continuar.
4. Se faltar pandas ou matplotlib, use a célula de instalação opcional explicada no notebook e reinicie o kernel.
5. Siga para 01_pratica.ipynb. Os nomes das pastas devem permanecer como vieram no pacote.

Kernel é o processo Python que mantém suas variáveis enquanto você trabalha. Reiniciar o kernel apaga essas variáveis da memória, mas não apaga seus arquivos. Depois de reiniciar, execute novamente as células, de cima para baixo. Se aparecer NameError, uma variável pode ainda não ter sido criada nesta sessão. Se aparecer FileNotFoundError, confira a pasta e o caminho dos dados. Essas situações são diferentes de um erro na análise.

### Como os códigos e resultados aparecem no material

Blocos marcados como python são comandos para executar. Tabelas e frases de “resultado esperado” descrevem o que você deve observar; não são comandos para copiar. Execute os blocos de uma aula na ordem em que aparecem. Os exemplos usam dados reais, exceto quando um exemplo fictício é explicitamente identificado para isolar uma ideia. Não é necessário executar a seção de instalação a cada aula.

Na primeira leitura, siga as aulas 1, 2 e 3 antes de estudar o dicionário completo da base comercial. O dicionário fica disponível para consulta; você não precisa memorizar nomes de oito colunas antes de abrir sua primeira tabela.


## Como usar este curso

Este curso começa sem conhecimento prévio de pandas. É recomendável reconhecer variáveis, listas, dicionários e funções em Python; o primeiro módulo revisa o necessário para ler os exemplos. O objetivo é você conseguir investigar, limpar, combinar e entregar dados com critérios de qualidade. Não é uma promessa de emprego nem substitui experiência em projetos reais.

**O que você recebe:** 12 módulos, 60 exercícios com gabarito comentado, dois conjuntos reais de dados locais, notebooks para praticar, resultados de referência e três projetos de portfólio com critérios de avaliação.

### Como estudar

Leia a explicação, execute o exemplo e tente os cinco exercícios sem consultar a solução. Registre sua hipótese antes de rodar o código. Compare forma, valores, tipos e interpretação; soluções equivalentes são válidas. Se travar, divida a pergunta: quais linhas, quais colunas, qual agrupamento, qual medida? Só avance quando conseguir explicar seu código e resolver ao menos quatro dos cinco exercícios sem copiar.

Sugestão flexível: 8 a 12 semanas, de 4 a 6 horas por semana. Semanas 1–2: módulos 1–3; 3–4: módulos 4–6; 5–6: módulos 7–9; 7–8: módulos 10–12. Reserve semanas adicionais para refazer exercícios e concluir os projetos. O ritmo depende da sua familiaridade com Python.

### Alternativa: criar um ambiente novo com JupyterLab

Descompacte o pacote inteiro antes de abrir os notebooks. Uma opção simples é usar JupyterLab no computador. Com uma instalação funcional de Python, abra um terminal na pasta do curso e execute:

```text
python -m venv .venv
.venv\Scripts\activate
python -m pip install -r requirements.txt
python -m jupyter lab
```

Se o comando python não funcionar, instale Python e confirme que está disponível no terminal. No Windows, a ativação pode depender da configuração do terminal; também é possível usar diretamente `.venv\Scripts\python.exe -m jupyter lab` após instalar as dependências com esse mesmo executável. No macOS/Linux, a ativação é `source .venv/bin/activate`.

Abra primeiro `notebooks/00_comecar_aqui.ipynb` e depois siga para `01_pratica.ipynb`. Cada notebook é independente: execute as células iniciais para preparar os dados necessários. Há um notebook de prática e outro de soluções para cada módulo. Os notebooks de soluções também trazem resultados conferidos nesta entrega. Para trabalhar no Google Colab, envie os arquivos CSV e ajuste DADOS para a pasta em que foram enviados. Colab não está configurado automaticamente neste pacote.

Todos os exemplos da apostila pressupõem o preparo comum abaixo e a execução dos módulos anteriores. Nos notebooks, isso já está incluído:

```python
from pathlib import Path
import pandas as pd
DADOS = Path('dados')
SAIDAS = Path('resultados')
SAIDAS.mkdir(exist_ok=True)
```

### Dicionário das bases reais

**Palmer Penguins:** 344 observações, oito colunas. species = espécie; island = ilha; bill_length_mm e bill_depth_mm = comprimento e profundidade do bico em milímetros; flipper_length_mm = comprimento da nadadeira em milímetros; body_mass_g = massa corporal em gramas; sex = sexo registrado; year = ano de coleta. Há ausências reais. A base simplificada não tem uma chave individual explícita. Dados de Kristen Gorman e Palmer Station LTER, distribuídos pelo projeto palmerpenguins sob CC0. Fonte e referências: https://allisonhorst.github.io/palmerpenguins/ .

**Online Retail:** 541.909 linhas de itens de transações, oito colunas, período de dezembro de 2010 a dezembro de 2011. InvoiceNo = código de fatura, com prefixo C sinalizando cancelamento; StockCode = código de produto; Description = descrição; Quantity = quantidade; InvoiceDate = data/hora; UnitPrice = preço unitário em GBP; CustomerID = código do cliente; Country = país. Dados disponibilizados por Daqing Chen, UCI Machine Learning Repository, 2015, DOI https://doi.org/10.24432/C5BW33, licença CC BY 4.0. O CSV incluído foi convertido do XLSX original, sem filtrar linhas. Os tipos precisam ser definidos ao reler o CSV.

As bases são históricas e públicas. Tabelas auxiliares construídas nas aulas são identificadas como didáticas. As soluções operam sobre os arquivos locais; a internet não é necessária para resolver os exercícios.

## Índice

- 01 • Sua primeira tabela
- 02 • Selecionar, filtrar e ordenar
- 03 • Tipos, ausências e qualidade
- 04 • Criar colunas e tratar textos
- 05 • Resumir dados com groupby
- 06 • Cruzar tabelas e mudar o formato
- 07 • Dados reais de comércio: diagnóstico e regras
- 08 • Datas, calendário e janelas
- 09 • Indicadores e segmentação de clientes
- 10 • Desempenho, arquivos e limites
- 11 • Análises reproduzíveis e validação
- 12 • Comunicação e entrega profissional


## 01 • Sua primeira tabela

### O que vamos aprender nesta aula

Você vai abrir uma tabela real, reconhecer suas partes e selecionar uma coluna. Ainda não vamos limpar dados, fazer filtros nem discutir desempenho. Ao terminar, você deve conseguir explicar o que cada linha e coluna representa.

### 1. Antes do pandas: o que é uma tabela?

Imagine uma planilha com três colunas: nome, idade e cidade. Cada coluna descreve uma característica. Cada linha reúne informações de uma pessoa. A linha de Ana não deve conter a idade de outra pessoa: os valores de uma mesma linha pertencem ao mesmo registro.

No nosso primeiro conjunto real, cada linha representa uma observação de um pinguim. As colunas descrevem espécie, ilha, medidas do corpo, sexo e ano. Não precisamos entender biologia para começar; precisamos entender o significado e a unidade de cada coluna.

### 2. Biblioteca, importação e apelido

Uma biblioteca reúne ferramentas prontas que podemos usar no Python. Pandas oferece ferramentas para trabalhar com tabelas. Execute primeiro:

```python
import pandas as pd
```

Leia assim: “carregue a biblioteca pandas e permita que eu a chame de pd”. `pd` é apenas um apelido convencional. Essa linha não abre uma tabela e normalmente não mostra nada na tela. Isso é esperado. Se aparecer um erro dizendo que pandas não existe, consulte a preparação do ambiente antes de continuar.

### 3. Abrir nosso arquivo real

O arquivo CSV guarda texto organizado em linhas, com campos separados por vírgulas. Um arquivo não é ainda um DataFrame: precisamos lê-lo. No notebook do curso, DADOS já aponta para a pasta dos arquivos.

```python
p = pd.read_csv(DADOS / 'penguins.csv')
```

Vamos ler por partes. `pd.read_csv(...)` pede ao pandas que leia o arquivo informado. Os parênteses contêm a informação de que a leitura precisa: onde está o arquivo. `DADOS / 'penguins.csv'` constrói esse caminho; aqui a barra une partes de um caminho porque DADOS é um objeto Path, não faz uma divisão numérica. O sinal `=` guarda o resultado no nome `p`. Daqui em diante, `p` é o nome da nossa tabela na memória.

Uma variável é um nome que você usa para se referir a um valor. Poderíamos ter escolhido `pinguins` em vez de `p`. Usaremos p para manter os códigos curtos. Se você mudar o nome, precisa mudá-lo nos comandos seguintes também. O arquivo original continua no disco; a leitura cria uma tabela para trabalhar no Python.

### 4. Ver uma pequena parte antes de fazer contas

```python
print(p.head(3))
```

`head` significa “começo”: ele mostra as primeiras linhas. O número 3 pede três linhas. `print(...)` mostra o resultado na tela. No Jupyter, escrever apenas `p.head(3)` como última expressão de uma célula também mostra a tabela, geralmente com uma apresentação mais bonita.

Aqui está um recorte das primeiras observações reais, com só três colunas para facilitar a leitura:

| índice | species | island | body_mass_g |
|---|---|---|---:|
| 0 | Adelie | Torgersen | 3750.0 |
| 1 | Adelie | Torgersen | 3800.0 |
| 2 | Adelie | Torgersen | 3250.0 |

`species` significa espécie; `island`, ilha; `body_mass_g`, massa corporal em gramas. O valor 3750.0 corresponde a 3.750 gramas. O ponto indica a parte decimal no Python. Não confunda esse número com 3,75 gramas.

A primeira coluna sem nome, à esquerda, é o índice criado na leitura. Os rótulos 0, 1 e 2 identificam essas linhas dentro da tabela. Não são uma medição e não constituem um código científico de cada animal. Mais adiante veremos que índice e posição podem ser diferentes.

### 5. O nome DataFrame

DataFrame é o nome que pandas dá a esse objeto de tabela com duas dimensões: linhas e colunas. Portanto, p é uma variável; o valor guardado nela é um DataFrame. Não é necessário aprender programação orientada a objetos para usá-lo.

```python
print(p.shape)
```

Resultado esperado: `(344, 8)`. A primeira quantidade é o número de linhas; a segunda é o número de colunas. Os parênteses indicam um par de valores, chamado tupla em Python.

```python
print(p.shape[0])
print(p.shape[1])
```

Resultados: 344 e 8. Aqui os colchetes pegam um elemento do par. A posição 0 é o primeiro elemento; a posição 1 é o segundo. Python começa a contagem de posições em zero.

### 6. Uma coluna: a Series

```python
print(p['species'].head(3))
```

Os colchetes com o nome da coluna pedem apenas aquela coluna. As aspas indicam que species é texto, exatamente como está no cabeçalho. O resultado é uma Series: uma sequência de valores acompanhados de seus índices. Neste exemplo, os valores são nomes de espécies.

```python
print(p[['species', 'island']].head(3))
```

Agora há uma lista de dois nomes dentro dos colchetes. O resultado é uma tabela com essas duas colunas, portanto um DataFrame. Não decore “colchete simples ou duplo” sem entender: `['species', 'island']` é a lista de colunas que você passou para a seleção.

Uma lista com uma única coluna também preserva o formato de tabela: `p[['species']]` devolve um DataFrame. Já `p['species']` devolve uma Series. Para conferir isso, use `type(p['species'])` e `type(p[['species']])`; type informa o tipo de um valor.

### 7. Método, atributo e o ponto

Compare `p.head(3)` com `p.shape`. O ponto acessa algo ligado à tabela. head é uma ação disponível, chamada método: usamos parênteses para executá-la. shape é uma informação disponível, chamada atributo: consultamos sem parênteses. Escrever `p.shape()` tenta executar um par de números como se fosse uma função e dá erro.

Também podemos consultar os nomes das colunas com `p.columns`. O complemento `.tolist()` transforma esses nomes em uma lista comum do Python. Não é obrigatório usá-lo para analisar a tabela; serve apenas para apresentar os nomes de uma forma familiar.

### 8. Duas ferramentas para conhecer antes dos exercícios

`p.tail(4)` mostra as últimas quatro linhas; é o equivalente de head para o final da tabela. `p.info()` imprime um relatório com as colunas, seus tipos e quantos valores estão presentes. Textos e números são tipos diferentes; faremos conversões somente na aula 3. Se uma coluna tem menos de 344 valores presentes, faltam informações em algumas observações.

O método info já imprime o relatório e não devolve uma nova tabela. Portanto, use `p.info()` sozinho. Se fizer `p = p.info()`, substituirá a tabela pelo valor None. Para recuperar, execute novamente a célula que lê o CSV.

### 9. Criar uma tabela minúscula para entender a estrutura

```python
estudo = pd.DataFrame({'pessoa': ['Ana', 'Bia'], 'horas': [2, 3]})
print(estudo)
```

Estes são dados fictícios, apenas para visualizar a construção. As chaves do dicionário, pessoa e horas, viram colunas. As listas de valores preenchem as linhas: Ana tem 2 horas; Bia tem 3. As listas precisam ter o mesmo comprimento. Usaremos os arquivos reais nos exercícios principais.

### Antes de continuar

Responda sem executar código: o que p representa? O que significa `(344, 8)`? Por que `p['species']` é diferente de `'species'` sozinho? A primeira expressão busca dados na tabela; a segunda é apenas um texto. Se isso ainda estiver confuso, refaça os passos 3 a 6 e observe os resultados um de cada vez.

### Exemplo guiado

```python
p = pd.read_csv(DADOS / 'penguins.csv')
print(p.head(3).to_string(index=False))
print('Dimensões:', p.shape)
print('Colunas:', p.columns.tolist())
print(type(p['species']).__name__)
```

### Exercícios

1. **01.1** — Execute p.head(3). Usando a saída, diga o que representa uma linha e qual é a massa do primeiro animal.
2. **01.2** — Mostre p.shape. Depois exiba apenas o número de linhas e apenas o número de colunas.
3. **01.3** — Selecione species e mostre três valores. Depois selecione species e island juntas e compare os formatos.
4. **01.4** — Mostre as quatro últimas linhas com tail. Explique por que o índice do resultado não começa em zero.
5. **01.5** — Execute p.info(). Compare os valores presentes de body_mass_g com o total de linhas. Quantas massas faltam?

## 02 • Selecionar, filtrar e ordenar

### Objetivo: transformar uma pergunta em seleção de dados

Nesta aula você vai responder “quais animais são da ilha Dream?” e “quais têm massa acima de 4.000 g?”. Primeiro construiremos cada condição separadamente; só depois combinaremos condições.

### 1. Comparar uma coluna inteira

```python
print(p['island'].head(3))
condicao = p['island'] == 'Dream'
print(condicao.head(3))
```

`==` pergunta se dois valores são iguais. É diferente de `=`, que guarda um resultado em uma variável. Como a coluna tem vários valores, pandas compara cada um com Dream. Para as primeiras três linhas, o resultado é False, False, False, porque elas pertencem a Torgersen. True significa verdadeiro; False significa falso. A sequência inteira de respostas é chamada máscara booleana.

```python
dream = p.loc[condicao]
print(dream.head(3))
```

Leia: “na tabela p, mantenha as linhas em que condicao é verdadeira”. As primeiras linhas do resultado têm índices 30, 31 e 32. Isso não significa que existem 30 linhas escondidas antes da primeira linha exibida: os rótulos originais foram preservados.

### 2. Selecionar linhas e colunas na mesma operação

```python
print(p.loc[condicao, ['species', 'island', 'body_mass_g']].head(3))
```

Dentro de loc, a parte antes da vírgula escolhe linhas; a parte depois escolhe colunas. Não confunda a vírgula que separa os dois critérios com as vírgulas dentro da lista de nomes. Se quiser todas as linhas de certas colunas, use `p.loc[:, ['species', 'island']]`: os dois-pontos significam “todas” nessa posição.

### 3. Condições numéricas e combinações

```python
da_ilha = p['island'] == 'Dream'
pesados = p['body_mass_g'] > 4000
selecao = da_ilha & pesados
print(p.loc[selecao, ['species', 'island', 'body_mass_g']].head())
```

O símbolo `&` exige que as duas respostas sejam verdadeiras na mesma linha. Uma massa acima de 4.000 fora de Dream não passa. Um animal de Dream com massa de 3.500 também não passa. Só a interseção passa.

Também podemos escrever sem as variáveis intermediárias, mas mantendo os parênteses de cada comparação:

```python
print(p.loc[(p['island'] == 'Dream') & (p['body_mass_g'] > 4000)].head())
```

Use `|` para “uma condição ou a outra”, e `~` para inverter uma condição. Não use and/or do Python entre Series; eles não fazem essa combinação linha por linha. Comparações com massa ausente não selecionam uma observação como “pesada”; a aula seguinte mostrará como contar essas ausências.

### 4. A mesma comparação com outros nomes

Você encontrará duas formas de escrever as mesmas operações. Comece pelos símbolos e consulte a tabela quando ler os gabaritos:

| Operação | Símbolo | Método equivalente |
|---|---|---|
| Igual | == | eq(valor) |
| Diferente | != | ne(valor) |
| Maior | > | gt(valor) |
| Maior ou igual | >= | ge(valor) |
| Menor | < | lt(valor) |
| Menor ou igual | <= | le(valor) |

Assim, `p['body_mass_g'].gt(4000)` produz a mesma condição que `p['body_mass_g'] > 4000` nesta base. `isin(['Adelie', 'Chinstrap'])` pergunta se cada espécie pertence à lista informada. É uma maneira de aceitar várias opções para uma coluna.

### 5. Posição não é rótulo

```python
print(dream.iloc[:2][['species', 'island']])
print(dream.loc[30, ['species', 'island']])
```

iloc usa a posição no resultado: `:2` pega as primeiras duas linhas, nas posições 0 e 1. loc usa o rótulo: 30 identifica uma linha que preservou esse índice da tabela original. Portanto, a primeira linha de dream está na posição zero, mas tem rótulo 30.

Nas fatias por posição, o limite final fica fora: `p.iloc[10:15]` pega as posições 10, 11, 12, 13 e 14. Não tente decorar isso ao mesmo tempo que filtros complexos; teste uma seleção pequena e conte suas linhas. Uma fatia por rótulos em loc pode incluir o limite final.

### 6. Ordenar e pegar os maiores

```python
ordenados = p.sort_values('flipper_length_mm', ascending=False)
print(ordenados[['species', 'flipper_length_mm']].head(5))
```

sort_values reorganiza linhas pelo valor de uma coluna. ascending=False pede ordem decrescente. head(5) pega as primeiras cinco linhas dessa tabela ordenada. Cada linha continua inteira: a espécie acompanha a medição do mesmo animal. A operação devolve uma nova tabela; o código acima não substitui p.

### Cuidado ao alterar dados

Nesta aula só consultamos dados. Quando precisar alterar, evite uma seleção seguida de outra como `p[condicao]['coluna'] = valor`. Use `p.loc[condicao, 'coluna'] = valor` para uma alteração explícita. Faremos criação de colunas na aula 4. Primeiro garanta que sabe quais linhas a condição seleciona.

### Exemplo guiado

```python
mascara = p['species'].eq('Adelie') & p['body_mass_g'].gt(4000)
print(p.loc[mascara, ['species', 'island', 'body_mass_g']].head())
print(p.iloc[:3, :2])
```

### Exercícios

1. **02.1** — Liste apenas pinguins da ilha Dream.
2. **02.2** — Selecione species, sex e body_mass_g, nessa ordem.
3. **02.3** — Encontre animais Adelie ou Chinstrap com massa de pelo menos 4.000 g.
4. **02.4** — Mostre os cinco animais com maior comprimento de nadadeira.
5. **02.5** — Pegue as posições 10 a 14, inclusive. Explique por que o limite usado é 15.

## 03 • Tipos, ausências e qualidade

### Objetivo: distinguir valor conhecido, valor ausente e valor inválido

Uma tabela pode abrir sem erros e ainda conter dados inadequados para uma análise. Nesta aula, vamos responder: “em quais colunas faltam dados?” e “quais linhas posso usar para estudar a massa corporal?”.

### 1. O que significa um valor ausente?

```python
print(p[['species', 'body_mass_g']].head(4))
```

Na quarta observação, a massa aparece como NaN. Isso indica ausência de uma medição nessa coluna. Não significa que o animal pesa zero e não autoriza inventar sua massa. Em outras colunas ou tipos, a ausência pode aparecer como None, <NA> ou NaT. Use isna para detectar ausências; não tente comparar com o texto 'NaN'.

```python
falta_massa = p['body_mass_g'].isna()
print(falta_massa.head(4))
print(falta_massa.sum())
```

O começo da condição é False, False, False, True. A soma conta True como 1 e False como 0. O total da base é 2: há duas observações sem massa. Isso deixa 342 medições presentes, não 344.

### 2. De contagem a porcentagem

```python
quantidade = falta_massa.sum()
total = len(p)
percentual = quantidade / total * 100
print(quantidade, total, round(percentual, 2))
```

len(p) é a quantidade de linhas. A conta é 2 dividido por 344, multiplicado por 100: aproximadamente 0,58%. round(..., 2) arredonda apenas o número apresentado para duas casas. Outra forma é `falta_massa.mean() * 100`, porque a média dos zeros e uns representa a proporção de ausências.

```python
print(p.isna().sum())
```

Aplicado à tabela inteira, isna cria uma tabela de respostas; sum conta por coluna. Nesta base, sex tem 11 ausências e body_mass_g tem 2. Depois de entender isso, podemos reunir contagem e porcentagem em um relatório, como no exemplo guiado ao final.

### 3. Remover somente o que a pergunta exige

```python
com_massa = p.dropna(subset=['body_mass_g']).copy()
print(len(com_massa))
```

dropna remove linhas com ausência nas colunas indicadas em subset. O resultado tem 342 linhas. A chamada copy deixa explícito que trabalharemos com uma tabela separada. A base p permanece com 344 linhas. Não use simplesmente `p.dropna()` sem pensar: isso exige informação presente em todas as colunas e pode descartar animais por falta de sexo, mesmo quando você só quer estudar massa.

Se a pergunta envolver massa e nadadeira, use `subset=['body_mass_g', 'flipper_length_mm']`. Documente a perda de observações. Preencher por média ou mediana é uma escolha metodológica, não uma etapa obrigatória de limpeza; não faremos isso automaticamente.

### 4. Tipos: o que a coluna permite fazer?

```python
print(p.dtypes)
```

dtypes informa o tipo de cada coluna. O tipo numérico permite fazer contas. Um tipo de texto guarda nomes ou códigos; sua aparência exata pode variar entre versões. Um número que veio como texto precisa ser convertido antes de uma operação numérica. Porém, um código como '0012' deve continuar texto para preservar seus zeros e seu significado. Ter apenas dígitos não transforma um identificador em medida.

Para listar colunas reconhecidas como numéricas, use `p.select_dtypes(include='number').columns`. Essa operação seleciona por tipo, não por significado: ainda cabe a você decidir se faz sentido calcular uma média daquela coluna.

### 5. Converter e contar os problemas

```python
entrada = pd.Series(['10', 'erro', None])
numeros = pd.to_numeric(entrada, errors='coerce')
print(numeros)
```

Este é um exemplo fictício de importação problemática. O primeiro valor vira 10. O texto erro não pode virar número. Com errors='coerce', ele vira ausência em vez de interromper a conversão. A ausência original também continua ausente. Ao final há duas ausências, mas só uma foi criada por falha de conversão:

```python
novas_falhas = entrada.notna() & numeros.isna()
print(novas_falhas.sum())
```

notna é o contrário de isna. A condição procura valores que estavam presentes antes e ficaram ausentes depois. O resultado esperado é 1. Usar coerce sem medir esse efeito pode esconder erros importantes. astype é útil quando você já sabe que a conversão deve funcionar, como `.astype('Int64')` para inteiros que aceitam ausências. Datas terão uma aula própria.

### 6. Duplicatas exigem uma definição

```python
print(p.duplicated().sum())
```

duplicated marca linhas iguais a uma anterior, considerando todas as colunas por padrão. O total encontrado não é uma autorização para apagar. Dois animais podem ter as mesmas medidas registradas, e a base simplificada não tem um identificador individual explícito. drop_duplicates remove essas repetições, mas só deve ser usado depois de justificar o que caracteriza um registro duplicado no seu problema.

### O que guardar desta aula

Ausência não é zero; converter não é corrigir; remover exige justificativa. Antes de uma limpeza, registre o tamanho original. Depois, registre quantas linhas foram removidas e por qual motivo. Preserve o arquivo bruto para conseguir revisar suas decisões.

### Exemplo guiado

```python
qualidade = pd.DataFrame({'ausentes':p.isna().sum(), 'percentual':p.isna().mean().mul(100)})
print(qualidade)
medidos = p.dropna(subset=['body_mass_g']).copy()
print('Observações com massa:', len(medidos))
```

### Exercícios

1. **03.1** — Quais colunas possuem pelo menos uma ausência?
2. **03.2** — Calcule a porcentagem de massas ausentes.
3. **03.3** — Crie uma tabela apenas com massa e comprimento de nadadeira presentes. Conte a perda de linhas.
4. **03.4** — Converta a Series didática ["10", "erro", None] para número e conte ausências resultantes.
5. **03.5** — Conte duplicatas exatas, sem removê-las. Por que isso não basta para excluir observações?

## 04 • Criar colunas e tratar textos

### Antes dos exercícios: uma transformação por vez

Para entender uma operação vetorizada, faça primeiro `print(p['body_mass_g'].head(3))`: os valores são 3750, 3800 e 3250 gramas. Depois execute `print((p['body_mass_g'] / 1000).head(3))`: você verá 3.75, 3.80 e 3.25. A divisão foi aplicada a cada valor, sem um for. Crie então uma nova coluna: `q = p.assign(body_mass_kg=p['body_mass_g'] / 1000)`. O nome antes do sinal de igual dentro de assign define a nova coluna; a expressão depois define seus valores. q contém a tabela enriquecida e p preserva suas colunas originais.

Para texto, pense em uma sequência de etapas: Series → str → operação. Em `s.str.strip().str.lower()`, strip devolve os textos sem espaços externos; lower transforma o resultado em minúsculas. O encadeamento é apenas uma maneira compacta de escrever dois passos que você pode executar separadamente. Uma lista de valores entre colchetes vira uma Series com `pd.Series(...)`.

No exercício de tradução, map recebe um dicionário como `{'male': 'masculino', 'female': 'feminino'}`. Para cada valor da coluna, procura a chave e devolve a tradução correspondente. Antes de confiar no resultado, use `p['sex'].value_counts(dropna=False)` para conhecer as entradas. A chamada value_counts conta ocorrências de cada valor; dropna=False inclui as ausências no relatório.

### Aprofundamento e cuidados

Operações vetorizadas trabalham com uma coluna inteira: dividir a massa em gramas por mil cria quilogramas. `assign` devolve uma nova tabela, útil para preservar a anterior. Em uma sequência de assign, as expressões com lambda recebem a tabela daquele passo. Aqui lambda é uma função curta.

O acessor `str` oferece operações de texto: `strip` remove espaços nas extremidades, `lower` padroniza caixa e `contains` encontra padrões. Para buscas literais use `regex=False`; para valores ausentes escolha explicitamente `na=False` quando a regra for tratá-los como não correspondentes. `map` aplica um dicionário; chaves não encontradas viram ausências. Audite-as.

Evite `apply(axis=1)` quando soma, divisão, map, operações de texto ou condições vetorizadas resolvem. Antes de otimizar velocidade, confirme se unidades e regra estão corretas. Não some gramas com quilogramas e não calcule razões com denominador zero sem uma regra explícita.

### Exemplo guiado

```python
enriquecido = p.assign(body_mass_kg=p['body_mass_g']/1000)
print(enriquecido[['body_mass_g','body_mass_kg']].head())
print(p['species'].astype('string').str.lower().head())
```

### Exercícios

1. **04.1** — Crie bill_length_cm a partir de bill_length_mm, preservando p.
2. **04.2** — Padronize a Series didática [" Dream ", "BISCOE", None] em minúsculas e sem espaços externos.
3. **04.3** — Traduza male/female para masculino/feminino em uma nova coluna. Preserve ausências.
4. **04.4** — Selecione espécies cujo nome contém a sequência literal elie, sem diferenciar caixa.
5. **04.5** — Crie a razão entre comprimento e profundidade do bico, protegendo denominadores iguais a zero.

## 05 • Resumir dados com groupby

### Enxergando o agrupamento em três passos

Considere a pergunta “qual é a massa média de cada espécie?”. Primeiro escolha a chave: species. Depois escolha a medida: body_mass_g. Por fim escolha o cálculo: mean. A expressão é `p.groupby('species')['body_mass_g'].mean()`. O resultado tem uma entrada por espécie, em vez de uma por animal. O groupby sozinho prepara o agrupamento; a média é calculada na chamada mean.

O resultado esperado para Adelie é aproximadamente 3700,66 g, baseado em 151 massas presentes, embora existam 152 observações da espécie. mean ignora as massas ausentes. Por isso a média deve vir acompanhada de count. A mediana, chamada median, é o valor central dos valores ordenados; std mede dispersão, com desvio padrão amostral por padrão. Não interprete std como erro da média.

No exemplo guiado, `massa_media_g=('body_mass_g', 'mean')` significa: “chame a saída de massa_media_g; use a coluna body_mass_g; aplique mean”. as_index=False mantém a chave como uma coluna comum do relatório. Para um resumo, use agg. Para anexar a média da espécie a cada animal, use transform: ele repete a média apropriada em cada linha, preservando o alinhamento. Subtrair essa média da massa mostra quanto cada animal está acima ou abaixo da média de seu grupo.

### Aprofundamento e cuidados

Agrupar significa separar observações por uma ou mais chaves e calcular um resumo de cada grupo. `agg` reduz os grupos; `transform` devolve um resultado alinhado às linhas originais. Use agregações nomeadas para dar nomes claros ao relatório.

`size` conta linhas; `count` conta valores presentes em uma coluna; `nunique` conta valores distintos, excluindo ausências por padrão. Essas perguntas são diferentes. Em grupos por sexo, `dropna=False` preserva o grupo sem informação. `observed=True` explicita que categorias não observadas não precisam aparecer.

Médias sem tamanho de amostra escondem fragilidade. Publique ao menos número de observações e número de medições válidas. Uma diferença entre espécies não demonstra causalidade. Correlação entre massa e nadadeira também não prova que uma medida causa a outra.

### Exemplo guiado

```python
resumo = p.groupby('species', as_index=False, observed=True).agg(
    observacoes=('body_mass_g','size'),
    massas_validas=('body_mass_g','count'),
    massa_media_g=('body_mass_g','mean'))
print(resumo)
```

### Exercícios

1. **05.1** — Conte animais por espécie.
2. **05.2** — Calcule mediana e desvio padrão da massa por espécie.
3. **05.3** — Conte animais por ilha e sexo, incluindo sexo ausente.
4. **05.4** — Crie uma coluna com a média de massa da espécie de cada animal e outra com seu desvio dessa média.
5. **05.5** — Compare size e count para a massa por espécie. Interprete diferenças.

## 06 • Cruzar tabelas e mudar o formato

### Como pensar antes de um merge

Imagine uma tabela de medições com várias linhas Adelie e um pequeno cadastro com uma única tradução para Adelie. Cada observação deve encontrar exatamente uma tradução. Essa relação é many_to_one: muitas observações para um cadastro. Em `p.merge(nomes, on='species', how='left', validate='many_to_one')`, nomes é a tabela da direita, on indica a coluna comum e left preserva as observações da esquerda. Se o cadastro repetir Adelie, cada observação dessa espécie poderá aparecer duas vezes. A validação interrompe a operação para você investigar.

Confira três coisas depois do cruzamento: quantidade de linhas, valores sem correspondência e somas das medidas que deveriam permanecer iguais. Apenas conferir o tamanho não detecta todos os problemas de correspondência. indicator=True cria a coluna _merge; both indica correspondência, left_only indica que não houve par à direita.

Ao reorganizar dados, pergunte se quer mudar somente o formato ou também resumir. A pivot_table de massa por espécie e sexo calcula médias: ela agrega várias observações em uma célula. Já melt não calcula médias; transforma duas colunas de medidas em uma coluna de nomes de medidas e outra de valores. Se você derrete duas medidas de 344 animais, o resultado terá 688 linhas. Essas linhas agora representam animal–medida, e não animais distintos.

### Aprofundamento e cuidados

`merge` cruza tabelas por chaves. Um left join preserva todas as linhas da esquerda, mas pode multiplicá-las se a chave da direita se repetir. Defina a granularidade de cada lado e use `validate="many_to_one"` quando várias linhas da esquerda devem encontrar uma única linha na direita. `indicator=True` ajuda a localizar chaves sem correspondência. No pandas, chaves ausentes podem corresponder entre si; valide-as antes se isso não fizer sentido no seu processo.

`concat` empilha tabelas; `ignore_index=True` cria novos rótulos de linha. Ele não resolve duplicatas ou diferenças de significado. `pivot` reorganiza e exige combinações únicas; `pivot_table` permite agregar duplicatas. `melt` transforma colunas de medidas em linhas, formando uma tabela longa.

A tabela auxiliar de nomes de espécies usada aqui é DIDÁTICA. As medições de pinguins continuam sendo reais. Não apresente a tradução construída como um novo levantamento científico.

### Exemplo guiado

```python
nomes = pd.DataFrame({'species':['Adelie','Chinstrap','Gentoo'],
                      'nome_pt':['Adélia','Barbicha','Papua']})
cruzado = p.merge(nomes, on='species', how='left', validate='many_to_one', indicator=True)
print(cruzado['_merge'].value_counts())
```

### Exercícios

1. **06.1** — Cruze as traduções e confirme que a quantidade de linhas permaneceu igual.
2. **06.2** — Construa uma tabela de massa média por espécie (linhas) e sexo (colunas).
3. **06.3** — Transforme bill_length_mm e bill_depth_mm em linhas, preservando species como identificador.
4. **06.4** — Divida p em dois blocos e una novamente. Confirme que os dados são iguais.
5. **06.5** — Duplique uma chave da tabela de tradução e demonstre que validate impede a multiplicação silenciosa.

## 07 • Dados reais de comércio: diagnóstico e regras

### Leitura comentada da regra comercial

Comece pela inspeção: `r.head()`, `r.info()` e `r.isna().sum()`. Não calcule receita antes de saber o que cada linha significa. Uma fatura com três produtos pode aparecer em três linhas; portanto len(r) não conta pedidos. `r['InvoiceNo'].nunique()` conta códigos distintos de fatura.

No exemplo, cancelada é uma máscara. A sequência str.upper().str.startswith('C', na=False) padroniza o código para maiúsculas e pergunta se começa com C. elegivel combina quatro exigências com &: quantidade positiva, preço positivo, data presente e ausência de cancelamento. O símbolo ~ inverte cancelada. Em seguida, loc mantém somente as linhas aprovadas, copy cria a tabela de trabalho e a multiplicação calcula o valor de cada item.

Exemplo fictício para entender a conta: uma fatura com duas linhas, uma de 2 unidades a £3 e outra de 1 unidade a £4, vale £10. A média dos valores das linhas é £5, mas o ticket dessa fatura é £10. Por isso o ticket médio exige primeiro somar itens por fatura e depois calcular a média dos totais de fatura. Não transfira valores deste exemplo fictício para os resultados reais.

### Aprofundamento e cuidados

Agora cada linha é um item de uma transação da base Online Retail. InvoiceNo identifica a transação; StockCode identifica o produto. Um pedido pode ocupar várias linhas. Quantity é a quantidade; UnitPrice é o preço unitário em libras esterlinas. CustomerID é um identificador, não uma medida para tirar média. Country é o país informado para o cliente, não prova de local de entrega.

O curso separa uma visão comercial de vendas positivas: quantidade > 0, preço > 0, data válida e código de fatura que não começa com C. O valor calculado é receita bruta dos itens elegíveis, sem reconciliar devoluções. Não é lucro, receita líquida contábil ou caixa recebido. Cancelamentos e quantidades negativas continuam na base bruta e no diagnóstico.

Linhas sem CustomerID podem entrar na visão de vendas, mas não na segmentação por cliente. Não remova duplicatas exatas automaticamente: sem um identificador único de linha não sabemos se representam repetição indevida. Inspecione a base de verdade: metadados publicados nem sempre refletem todas as ausências observadas.

### Exemplo guiado

```python
r = pd.read_csv(DADOS/'online_retail.csv', dtype={
    'InvoiceNo':'string','StockCode':'string','CustomerID':'string'})
r['InvoiceDate'] = pd.to_datetime(r['InvoiceDate'], errors='coerce')
cancelada = r['InvoiceNo'].str.upper().str.startswith('C', na=False)
elegivel = (r['Quantity'].gt(0) & r['UnitPrice'].gt(0)
            & r['InvoiceDate'].notna() & ~cancelada)
v = r.loc[elegivel].copy()
v['valor'] = v['Quantity'] * v['UnitPrice']
print('Linhas brutas:',len(r),'Linhas elegíveis:',len(v))
print(r.isna().sum())
```

### Exercícios

1. **07.1** — Conte faturas distintas e compare com a quantidade de linhas brutas.
2. **07.2** — Conte linhas de cancelamento, quantidade negativa, preço não positivo e cliente ausente. As categorias podem se sobrepor.
3. **07.3** — Calcule o valor total da visão positiva e declare moeda e definição.
4. **07.4** — Liste os dez países de maior receita nessa visão.
5. **07.5** — Calcule ticket médio por fatura; não use a média das linhas de itens.

## 08 • Datas, calendário e janelas

### Uma data é mais que um texto

O texto '2026-01-31' pode ser exibido, mas operações de calendário precisam de um tipo de data. to_datetime faz essa conversão. Depois, `v['InvoiceDate'].dt.year` extrai o ano; `.dt.to_period('M')` identifica o ano-mês. Agrupar somente por nome ou número do mês mistura janeiro de anos diferentes; use ano e mês juntos.

No exemplo guiado, set_index coloca InvoiceDate como índice temporário para resample. O código não substitui v. resample('MS') cria grupos mensais rotulados pelo início de cada mês; sum soma valores dentro de cada grupo. min_count=1 evita que um grupo totalmente sem valores presentes seja apresentado automaticamente como zero.

Para entender uma janela móvel, imagine valores diários fictícios 10, 20 e 30. Uma janela de duas observações produz primeiro ausência, depois 15 e depois 25, quando exige duas observações. Ela desliza pelo calendário. Antes de interpretar “sete linhas” como “sete dias”, confirme que existe uma linha por dia. shift(1) desloca o valor anterior para a linha atual, permitindo calcular (atual/anterior − 1) × 100. O primeiro período não tem anterior e deve ficar sem variação calculada.

### Aprofundamento e cuidados

`to_datetime` converte datas; o acessor `dt` extrai mês, dia e hora. Datas ambíguas como 03/04/2026 precisam de um formato explícito, por exemplo `%d/%m/%Y`. Na base da loja, trabalhamos com o horário registrado, sem informação de fuso; não inventamos uma conversão para UTC.

`resample` agrupa por intervalos de tempo quando o índice é de datas. Usaremos `MS`, início do mês. `rolling(7)` usa sete observações; `rolling("7D")` usa uma janela de tempo. Para comparar dias, reindexe o calendário e declare se ausência significa zero vendas ou falha na coleta. Aqui preencheremos com zero dentro do intervalo observado, como hipótese do exercício.

O primeiro e o último mês podem estar incompletos. A base termina em dezembro de 2011 antes do fim do mês; comparar seu total com novembro pode sugerir uma queda artificial. Crescimento percentual não é definido quando o valor anterior é zero. Valores monetários em float são adequados para esta exploração, mas sistemas financeiros exigem política explícita de precisão e arredondamento.

### Exemplo guiado

```python
mensal = v.set_index('InvoiceDate')['valor'].resample('MS').sum(min_count=1)
print(mensal)
print('Cobertura:',r['InvoiceDate'].min(),r['InvoiceDate'].max())
```

### Exercícios

1. **08.1** — Some receita elegível por ano e mês usando dt.to_period.
2. **08.2** — Calcule a receita por dia e complete o calendário com zero, documentando a hipótese.
3. **08.3** — Calcule a média móvel de sete dias, exigindo sete dias para produzir resultado.
4. **08.4** — Calcule variação mensal e substitua resultados com denominador anterior zero por ausência.
5. **08.5** — Converta ["31/01/2026", "data ruim"] com formato brasileiro e conte falhas.

## 09 • Indicadores e segmentação de clientes

### Fazendo o RFM sem decorar a sigla

Para cada cliente, queremos três respostas: há quantos dias ele comprou, em quantas faturas apareceu e quanto comprou na visão elegível. groupby('CustomerID') define uma linha por cliente. max da data encontra a última compra; nunique da fatura conta compras distintas; sum do valor calcula o total. A data de referência fica um dia após a última venda observada, para manter o exercício reproduzível.

Exemplo fictício: referência em 10/01; compras em 02/01 e 08/01, em duas faturas de £20 e £30. Recência = 2 dias, frequência = 2 e monetário = £50. Comprar vários itens na mesma fatura não aumenta a frequência. Baixa recência significa compra mais recente; alto monetário significa maior valor observado. Não são três medidas com a mesma direção de interpretação.

Ao calcular participação acumulada, ordene o monetário do maior para o menor. cumsum acumula os valores até cada linha; dividir pelo total transforma a soma acumulada em proporção. O último valor deve estar próximo de 1, isto é, 100%. Isso descreve concentração histórica; não é garantia de receita futura.

### Aprofundamento e cuidados

Um indicador precisa de nome, fórmula, unidade, período, população e exclusões. Receita por cliente mede valor, frequência mede número de faturas e recência mede dias desde a última compra. Este é um RFM descritivo: não vamos chamar automaticamente esses números de previsão de abandono ou de valor futuro do cliente.

Para evitar datas que mudam todos os dias, a referência será o dia seguinte à última data de venda elegível. Frequência deve contar faturas distintas, não itens. Clientes ausentes ficam fora da segmentação e sua participação na receita é reportada. Cada observação de RFM representa um cliente.

Ticket médio global é total dividido por quantidade de pedidos. A média dos tickets médios por país dá peso igual a países com volumes diferentes e em geral responde a outra pergunta. Escreva a fórmula antes de escolher mean ou sum. Uma proporção deve preservar seu denominador e uma divisão precisa tratar zero.

### Exemplo guiado

```python
identificados = v.dropna(subset=['CustomerID']).copy()
referencia = v['InvoiceDate'].max().normalize() + pd.Timedelta(days=1)
rfm = identificados.groupby('CustomerID').agg(
    ultima_compra=('InvoiceDate','max'), frequencia=('InvoiceNo','nunique'), monetario=('valor','sum'))
rfm['recencia_dias'] = (referencia-rfm['ultima_compra'].dt.normalize()).dt.days
print(rfm.head())
```

### Exercícios

1. **09.1** — Mostre dez clientes com maior valor monetário.
2. **09.2** — Calcule a porcentagem da receita elegível sem identificação de cliente.
3. **09.3** — Selecione clientes com recência até 30 dias e pelo menos cinco faturas. A regra é didática, não um modelo validado.
4. **09.4** — Calcule a participação acumulada dos clientes na receita identificada, em ordem decrescente.
5. **09.5** — Valide que a soma monetária por cliente coincide com o total identificado.

## 10 • Desempenho, arquivos e limites

### Por que ler em blocos muda a forma de calcular

Imagine um arquivo que não cabe na memória. chunksize=100000 devolve um leitor que entrega até cem mil linhas por vez. O for repete o mesmo preparo para cada bloco. A lista parciais guarda um total por país de cada pedaço; concat reúne esses totais; groupby(level=0).sum() soma países iguais no índice do resultado. Nesse exemplo, level=0 significa o primeiro nível do índice, onde está o país.

A soma das partes é a soma total. Mas a média de um bloco com 10 linhas não pode ter o mesmo peso de outro com mil linhas. Guarde soma e contagem, some ambas e só depois divida. Se estiver calculando vendas elegíveis em blocos, aplique exatamente os mesmos filtros em todos os blocos. O exercício de quantidade bruta usa deliberadamente outra medida, sem os filtros comerciais; seu resultado não é receita elegível.

O argumento index=False ao exportar CSV evita escrever o índice como uma coluna adicional. Uma releitura que preserva shape não garante sozinha que todos os valores e tipos foram preservados; para entregas críticas, compare também chaves, tipos e totais. O exercício usa shape como primeira verificação, não como contrato completo.

### Aprofundamento e cuidados

Leia só o necessário com usecols e defina tipos quando conhecer o contrato. CSV não guarda tipos de forma completa; documente a leitura. Parquet preserva melhor tipos e comprime, mas requer um mecanismo como pyarrow. Excel é útil para pessoas revisarem resultados, mas não deve ser escolhido automaticamente para grandes volumes.

Meça memória com `memory_usage(deep=True)` e tempo com `perf_counter`. `category` pode economizar memória em textos muito repetidos; teste antes, porque não é uma solução universal. Prefira operações vetorizadas e agregações em lote a laços que alteram célula a célula.

`chunksize` lê CSV em blocos. Somar totais por país de cada bloco e somar os parciais funciona; tirar média das médias de blocos pode estar errado. Para média, acumule soma e contagem. Contagens distintas também não são aditivas: o mesmo cliente pode aparecer em vários blocos. Se o volume não cabe em memória ou os cruzamentos ficam caros, considere SQL/DuckDB ou outro mecanismo apropriado e transfira apenas o resultado necessário para pandas.

### Exemplo guiado

```python
antes = p['species'].memory_usage(deep=True)
categorica = p['species'].astype('category')
print('Memória original:',antes,'bytes; categórica:',categorica.memory_usage(deep=True))
```

### Exercícios

1. **10.1** — Leia apenas Country, Quantity e UnitPrice das primeiras cem linhas do CSV da loja.
2. **10.2** — Mostre a memória total de r em MiB.
3. **10.3** — Compare massa média pela divisão soma/contagem com mean.
4. **10.4** — Some quantidades brutas por país em blocos de cem mil linhas. Compare com leitura completa.
5. **10.5** — Exporte o resumo por espécie para CSV sem gravar o índice. Releia e confira as dimensões.

## 11 • Análises reproduzíveis e validação

### Entendendo a função do exemplo

`def preparar_vendas(bruto):` define uma função chamada preparar_vendas que recebe uma tabela pelo parâmetro bruto. As linhas indentadas pertencem à função. Elas só são executadas quando você chama `preparar_vendas(r)`. return entrega a tabela preparada para quem chamou. O nome bruto é local à função e evita depender diretamente de uma variável global chamada r.

obrigatorias é um conjunto, criado com chaves; não é um dicionário, porque não contém pares chave:valor. A diferença entre conjuntos encontra os nomes que faltam no arquivo. `if faltantes:` entra no bloco quando há alguma falta. raise ValueError interrompe a transformação com uma mensagem clara. A expressão f'...' permite inserir o valor de uma variável dentro de um texto.

Um teste pequeno deve ter resposta conhecida independentemente do algoritmo. Crie manualmente quatro linhas: uma compra válida, um cancelamento, um preço zero e uma data inválida. Se só a primeira deve passar, confira o identificador e o valor esperado dessa linha. Isso verifica uma regra concreta; comparar duas cópias do mesmo cálculo pode reproduzir o mesmo erro nos dois lados. A função do exemplo verifica colunas e aplica regras, mas não é um contrato completo para qualquer entrada: antes de usá-la com outro sistema, acrescente validação e conversão explícita de Quantity e UnitPrice.

### Aprofundamento e cuidados

Um notebook profissional precisa funcionar com o ambiente recém-iniciado, na ordem documentada. Separe entrada, transformação e saída. Registre versões, fonte, data de obtenção e regras. Funções com entradas e retornos explícitos são mais fáceis de revisar do que alterações espalhadas em variáveis globais.

Um contrato define colunas obrigatórias, tipos e restrições. Valide antes de publicar. Os checks devem testar o significado: valor é quantidade vezes preço, chave tem a unicidade esperada, soma do relatório reconcilia com a base elegível. Testar apenas se uma função devolve um DataFrame é insuficiente.

Use `pd.testing` para comparações estruturais; para somas de ponto flutuante use tolerância. No código de produção prefira exceções explícitas para contratos, pois asserts podem ser desativados. Para exemplos de estudo e verificações locais, asserts deixam as condições visíveis. Não capture todas as exceções e continue silenciosamente. Registre linhas rejeitadas e motivos; não inclua dados de clientes em logs públicos.

### Exemplo guiado

```python
def preparar_vendas(bruto):
    obrigatorias = {'InvoiceNo','InvoiceDate','Quantity','UnitPrice','CustomerID','Country'}
    faltantes = obrigatorias - set(bruto.columns)
    if faltantes:
        raise ValueError(f'Colunas ausentes: {sorted(faltantes)}')
    t = bruto.copy()
    t['InvoiceDate'] = pd.to_datetime(t['InvoiceDate'], errors='coerce')
    cancelamento = t['InvoiceNo'].astype('string').str.upper().str.startswith('C', na=False)
    ok = t['Quantity'].gt(0) & t['UnitPrice'].gt(0) & t['InvoiceDate'].notna() & ~cancelamento
    saida = t.loc[ok].copy()
    saida['valor'] = saida['Quantity']*saida['UnitPrice']
    return saida

v2 = preparar_vendas(r)
pd.testing.assert_frame_equal(v, v2)
print('Transformação reproduzida')
```

### Exercícios

1. **11.1** — Confirme que preparar_vendas não modifica a tabela de entrada.
2. **11.2** — Demonstre a falha de contrato ao remover Country.
3. **11.3** — Valide quantidade, preço, data e valor nas vendas elegíveis.
4. **11.4** — Reconcilie a receita mensal com a receita total.
5. **11.5** — Produza um registro com versão do pandas, linhas lidas, linhas elegíveis e intervalo observado.

## 12 • Comunicação e entrega profissional

### Transformando um resultado em uma conclusão defensável

Escreva uma frase seguindo quatro componentes: medida, população, período e ressalva. Por exemplo: “O país X concentra Y% da receita bruta de vendas positivas elegíveis no período observado; cancelamentos não foram reconciliados”. Calcule X e Y antes de preencher a frase. Não conclua que um país é mais lucrativo: a base não inclui todos os custos necessários para calcular lucro.

No gráfico, plot.barh pede barras horizontais; o índice fornece nomes de países e os valores fornecem comprimentos. set_xlabel explica a medida e a moeda. tight_layout ajusta margens para os textos caberem; savefig grava o arquivo. Fechar a figura com close evita manter várias figuras abertas durante execuções repetidas.

Antes de publicar, peça que outra pessoa consiga responder: de onde vieram os dados, o que cada linha representa, quais registros ficaram de fora e como os totais foram conferidos? Se ela precisa adivinhar essas quatro coisas, o relatório ainda precisa de contexto. Use os projetos finais para praticar esse critério de entrega.

### Aprofundamento e cuidados

Uma análise útil responde a uma decisão concreta. Comece por pergunta, população, período e unidade de análise. Mostre o resultado com a evidência que o sustenta. Separe observação (o que foi medido), interpretação (o que pode explicar) e recomendação (o que fazer ou investigar). Não invente causas a partir de uma tabela agregada.

Para uma série temporal, um gráfico de linha costuma ajudar. Para comparar países, barras ordenadas facilitam a leitura. Inclua unidade no eixo e título com escopo. Não corte o eixo de barras para exagerar diferenças. Para pinguins, distribuições e tamanho da amostra ajudam mais do que apenas uma média.

Uma entrega profissional inclui arquivo bruto preservado, transformação reproduzível, relatório de qualidade, indicadores com definições, validações, instruções de execução e limitações. A base comercial deste curso é histórica: os padrões encontrados não representam o mercado atual. Concluir o curso desenvolve prática; experiência profissional também exige revisão, colaboração e aplicações em contextos diferentes.

### Exemplo guiado

```python
paises = v.groupby('Country')['valor'].sum().sort_values(ascending=False).head(5)
print(paises.rename('receita_bruta_elegivel_GBP'))
print('Período observado:',v['InvoiceDate'].min(),v['InvoiceDate'].max())
```

### Exercícios

1. **12.1** — Prepare uma tabela com receita, faturas e ticket médio por país.
2. **12.2** — Exporte os indicadores por país e o RFM para arquivos separados.
3. **12.3** — Desenhe barras horizontais dos cinco maiores países com eixo em GBP.
4. **12.4** — Escreva uma conclusão factual com participação do maior país e uma limitação.
5. **12.5** — Crie um checklist de publicação e explique quando impedir a entrega.

## Três projetos para consolidar e montar portfólio

### Projeto 1 — Relatório científico exploratório

**Pergunta:** como massa e comprimento de nadadeira se distribuem entre espécies e ilhas?

Use penguins.csv. Entregue um notebook reproduzível, um relatório de ausências, três tabelas e dois gráficos. Compare médias e medianas; apresente número de medições em cada grupo. Investigue se as espécies estão igualmente distribuídas nas ilhas antes de atribuir diferenças à localização. Não impute medições apenas para completar a tabela.

Tarefas: definir a unidade de observação; conferir unidades e tipos; contar observações e medições presentes por espécie; fazer uma tabela espécie × ilha; comparar massa por espécie e sexo com n explícito; explorar relação massa/nadadeira; redigir cinco achados e três limitações. Uma correlação geral pode misturar grupos distintos.

Critérios de aceite: 344 observações brutas preservadas; ausência auditada por coluna; cada gráfico com unidade e população; nenhuma conclusão causal sem desenho adequado; notebook executável do início ao fim. Extensão: comparar correlação geral com correlações por espécie, sem interpretar diferença como prova causal.

### Projeto 2 — Relatório comercial histórico

**Decisão simulada:** quais países e produtos merecem uma investigação comercial mais detalhada?

Use online_retail.csv. Entregue receita elegível mensal, top dez países, top dez produtos por valor, distribuição de ticket e um diagnóstico das exclusões. Agrupe produto por StockCode; descrições podem variar. Conte faturas distintas para pedidos e explique a presença de clientes não identificados.

Tarefas: preservar bruto; medir cancelamentos, preços não positivos e quantidades negativas; aplicar a regra do módulo 7; reconciliar totais por país e mês; avaliar concentração; sinalizar dezembro incompleto; escrever uma página com três achados, duas hipóteses e uma proposta de investigação. Não compare meses incompletos como se fossem equivalentes.

Critérios de aceite: total dos relatórios coincide com a base elegível; moeda GBP explícita; ticket calculado por fatura; nenhuma exclusão silenciosa; deduplicação apenas se houver justificativa; receita apresentada como bruta elegível. Extensão: construir uma visão separada com valores negativos e cancelamentos, preservando exceções. Não chamá-la de receita líquida contábil sem conciliação.

### Projeto 3 — Processo de dados reproduzível e RFM

**Situação:** outra pessoa precisa executar sua análise com um novo arquivo do mesmo formato.

Organize entrada, transformação, validação e exportação. Entregue uma função de preparo, contrato de colunas e tipos, relatório de qualidade, RFM por cliente e instruções de execução. Defina data de referência reproduzível. Se criar segmentos, publique seus limites e explique que são regras exploratórias.

Tarefas: ler identificadores como texto; converter e auditar datas e números; rejeitar arquivo sem colunas obrigatórias; separar registros elegíveis; calcular RFM sem perder a receita dos clientes ausentes no diagnóstico; verificar invariantes; exportar relatório e log sem dados pessoais; executar em ambiente limpo. Teste uma entrada pequena construída por você contendo compra válida, cancelamento, preço zero e data inválida. A resposta esperada dessa entrada deve ser definida manualmente.

Critérios de aceite: função não altera entrada; contrato falha claramente; execução repetida com a mesma entrada dá o mesmo resultado; soma de monetário reconcilia com vendas identificadas; recência nunca negativa; contagem de clientes fecha; versões registradas. Extensão: separar parâmetros de execução do código e comparar tempo/memória de duas estratégias com resultados equivalentes.

### Rubrica de revisão (100 pontos por projeto)

| Critério | Pontos | Evidência |
|---|---:|---|
| Correção dos cálculos | 30 | Fórmulas, granularidade e reconciliação |
| Qualidade e rastreabilidade | 25 | Fonte, bruto preservado, ausências e exclusões |
| Reprodutibilidade | 20 | Execução completa e instruções |
| Comunicação | 15 | Achados sustentados, unidades e limitações |
| Clareza do código | 10 | Nomes claros, funções úteis, pouca repetição |

Meta de estudo: 80 pontos, com cálculos reconciliados e execução completa obrigatórios. Os projetos são abertos: os gabaritos dos módulos mostram técnicas, mas não há uma única narrativa correta. Não publique os CSVs sem incluir as atribuições e licenças.

## Consulta rápida e erros comuns

| Pergunta | Ferramenta |
|---|---|
| O que há nesta tabela? | head, shape, info, describe |
| Quais linhas cumprem uma regra? | loc com máscaras |
| Quantos valores faltam? | isna().sum() |
| Como criar uma medida? | assign e operações vetorizadas |
| Como resumir por grupo? | groupby().agg() |
| Como devolver uma medida de grupo a cada linha? | transform |
| Como cruzar cadastros? | merge com validate e indicator |
| Como reorganizar? | pivot_table, melt, concat |
| Como agregar por mês? | dt.to_period ou resample |
| Como validar resultados? | pd.testing e reconciliação com tolerância |

- KeyError: confira `df.columns.tolist()`; há espaços ou diferença de maiúsculas?
- Resultado vazio: conte separadamente cada condição antes de combiná-las.
- Can only use .dt accessor: a coluna ainda precisa virar datetime.
- Falha em merge validate: investigue chaves repetidas; não remova a validação apenas para executar.
- Alteração não aplicada: substitua atribuição encadeada por loc ou assign.
- Média estranha: confira unidade, zeros artificiais, ausências e denominador.
- Valor duplicado após merge: revise a cardinalidade das chaves dos dois lados.
- Leitura de CSV brasileiro: confira `sep=';'` e `decimal=','` quando esse for realmente o formato. Não use essas opções por padrão em qualquer arquivo.
- Índices inesperados em contas: Series alinham pelos rótulos, não apenas pela posição. Inspecione os índices antes de combinar resultados.
- Código roda só às vezes: reinicie o kernel e execute todas as células em ordem.

## Próximos estudos

Depois dos projetos, estude SQL, estatística descritiva e amostragem, Git e organização de projetos Python. Aprofunde SQL para filtrar e agregar perto da origem; use pandas para análise e manipulação no contexto apropriado. Aprenda POO quando houver um problema de modelagem que justifique classes.

## Fontes e documentação

- Tutoriais oficiais: https://pandas.pydata.org/docs/getting_started/intro_tutorials/index.html
- Referência de API: https://pandas.pydata.org/docs/reference/index.html
- Guia de uso: https://pandas.pydata.org/docs/user_guide/index.html
- Palmer Penguins e referências científicas: https://allisonhorst.github.io/palmerpenguins/
- Repositório e CSV original: https://github.com/allisonhorst/palmerpenguins
- Online Retail e metadados: https://archive.ics.uci.edu/dataset/352/online+retail
- Licença CC BY 4.0: https://creativecommons.org/licenses/by/4.0/

Material autoral de estudo, com exemplos desenvolvidos para esta apostila e bases atribuídas acima. Consulte o arquivo de verificação para as versões efetivamente utilizadas. Documentação online pode evoluir.
