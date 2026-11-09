# Resultados de referência

Saídas obtidas nos arquivos locais incluídos. Pequenas diferenças de apresentação entre versões são possíveis. Tabelas grandes aparecem abreviadas.

## Módulo 01 — exemplo

```text
species    island  bill_length_mm  bill_depth_mm  flipper_length_mm  body_mass_g    sex  year
 Adelie Torgersen            39.1           18.7              181.0       3750.0   male  2007
 Adelie Torgersen            39.5           17.4              186.0       3800.0 female  2007
 Adelie Torgersen            40.3           18.0              195.0       3250.0 female  2007
Dimensões: (344, 8)
Colunas: ['species', 'island', 'bill_length_mm', 'bill_depth_mm', 'flipper_length_mm', 'body_mass_g', 'sex', 'year']
Series
```

## Módulo 01 — exercício 1

```text
species     island  bill_length_mm  ...  body_mass_g     sex  year
0  Adelie  Torgersen            39.1  ...       3750.0    male  2007
1  Adelie  Torgersen            39.5  ...       3800.0  female  2007
2  Adelie  Torgersen            40.3  ...       3250.0  female  2007

[3 rows x 8 columns]
Massa do primeiro animal (g): 3750.0
```

## Módulo 01 — exercício 2

```text
(344, 8)
Linhas: 344
Colunas: 8
```

## Módulo 01 — exercício 3

```text
0    Adelie
1    Adelie
2    Adelie
Name: species, dtype: str
  species     island
0  Adelie  Torgersen
1  Adelie  Torgersen
2  Adelie  Torgersen
```

## Módulo 01 — exercício 4

```text
species island  bill_length_mm  ...  body_mass_g     sex  year
340  Chinstrap  Dream            43.5  ...       3400.0  female  2009
341  Chinstrap  Dream            49.6  ...       3775.0    male  2009
342  Chinstrap  Dream            50.8  ...       4100.0    male  2009
343  Chinstrap  Dream            50.2  ...       3775.0  female  2009

[4 rows x 8 columns]
```

## Módulo 01 — exercício 5

```text
<class 'pandas.DataFrame'>
RangeIndex: 344 entries, 0 to 343
Data columns (total 8 columns):
 #   Column             Non-Null Count  Dtype  
---  ------             --------------  -----  
 0   species            344 non-null    str    
 1   island             344 non-null    str    
 2   bill_length_mm     342 non-null    float64
 3   bill_depth_mm      342 non-null    float64
 4   flipper_length_mm  342 non-null    float64
 5   body_mass_g        342 non-null    float64
 6   sex                333 non-null    str    
 7   year               344 non-null    int64  
dtypes: float64(4), int64(1), str(3)
memory usage: 21.6 KB
Massas ausentes: 2
```

## Módulo 02 — exemplo

```text
species     island  body_mass_g
7   Adelie  Torgersen       4675.0
9   Adelie  Torgersen       4250.0
14  Adelie  Torgersen       4400.0
17  Adelie  Torgersen       4500.0
19  Adelie  Torgersen       4200.0
  species     island
0  Adelie  Torgersen
1  Adelie  Torgersen
2  Adelie  Torgersen
```

## Módulo 02 — exercício 1

```text
species island  bill_length_mm  ...  body_mass_g     sex  year
30      Adelie  Dream            39.5  ...       3250.0  female  2007
31      Adelie  Dream            37.2  ...       3900.0    male  2007
32      Adelie  Dream            39.5  ...       3300.0  female  2007
33      Adelie  Dream            40.9  ...       3900.0    male  2007
34      Adelie  Dream            36.4  ...       3325.0  female  2007
..         ...    ...             ...  ...          ...     ...   ...
339  Chinstrap  Dream            55.8  ...       4000.0    male  2009
340  Chinstrap  Dream            43.5  ...       3400.0  female  2009
341  Chinstrap  Dream            49.6  ...       3775.0    male  2009
342  Chinstrap  Dream            50.8  ...       4100.0    male  2009
343  Chinstrap  Dream            50.2  ...       3775.0  female  2009

[124 rows x 8 columns]
```

## Módulo 02 — exercício 2

```text
species     sex  body_mass_g
0  Adelie    male       3750.0
1  Adelie  female       3800.0
2  Adelie  female       3250.0
3  Adelie     NaN          NaN
4  Adelie  female       3450.0
```

## Módulo 02 — exercício 3

```text
species     island  bill_length_mm  ...  body_mass_g     sex  year
7       Adelie  Torgersen            39.2  ...       4675.0    male  2007
9       Adelie  Torgersen            42.0  ...       4250.0     NaN  2007
14      Adelie  Torgersen            34.6  ...       4400.0    male  2007
17      Adelie  Torgersen            42.5  ...       4500.0    male  2007
19      Adelie  Torgersen            46.0  ...       4200.0    male  2007
35      Adelie      Dream            39.2  ...       4150.0    male  2007
39      Adelie      Dream            39.8  ...       4650.0    male  2007
43      Adelie      Dream            44.1  ...       4400.0    male  2007
45      Adelie      Dream            39.6  ...       4600.0    male  2007
49      Adelie      Dream            42.3  ...       4150.0    male  2007
51      Adelie     Biscoe            40.1  ...       4300.0    male  2008
53      Adelie     Biscoe            42.0  ...       4050.0    male  2008
61      Adelie     Biscoe            41.3  ...       4400.0    male  2008
63      Adelie     Biscoe            41.1  ...       4050.0    male  2008
67      Adelie     Biscoe            41.1  ...       4100.0    male  2008
69      Adelie  Torgersen            41.8  ...       4450.0    male  2008
73      Adelie  Torgersen            45.8  ...       4150.0    male  2008
75      Adelie  Torgersen            42.8  ...       4250.0    male  2008
79      Adelie  Torgersen            42.1  ...       4000.0    male  2008
81      Adelie  Torgersen            42.9  ...       4700.0    male  2008
83      Adelie  Torgersen            35.1  ...       4200.0    male  2008
91      Adelie      Dream            41.1  ...       4300.0    male  2008
93      Adelie      Dream            39.6  ...       4450.0    male  2008
95      Adelie      Dream            40.8  ...       4300.0    male  2008
97      Adelie      Dream            40.3  ...       4350.0    male  2008
99      Adelie      Dream            43.2  ...       4100.0    male  2008
101     Adelie     Biscoe            41.0  ...       4725.0    male  2009
103     Adelie     Biscoe            37.8  ...       4250.0    male  2009
109     Adelie     Biscoe            43.2  ...       4775.0    male  2009
111     Adelie     Biscoe            45.6  ...       4600.0    male  2009
113     Adelie     Biscoe            42.2  ...       4275.0    male  2009
115     Adelie     Biscoe            42.7  ...       4075.0    male  2009
125     Adelie  Torgersen            40.6  ...       4000.0    male  2009
127     Adelie  Torgersen            41.5  ...       4300.0    male  2009
129     Adelie  Torgersen            44.1  ...       4000.0    male  2009
133     Adelie      Dream            37.5  ...       4475.0    male  2009
139     Adelie      Dream            39.7  ...       4250.0    male  2009
146     Adelie      Dream            39.2  ...       4250.0    male  2009
151     Adelie      Dream            41.5  ...       4000.0    male  2009
284  Chinstrap      Dream            46.0  ...       4150.0  female  2007
289  Chinstrap      Dream            52.0  ...       4050.0    male  2007
291  Chinstrap      Dream            50.5  ...       4050.0    male  2007
295  Chinstrap      Dream            49.2  ...       4400.0    male  2007
301  Chinstrap      Dream            52.0  ...       4150.0    male  2007
305  Chinstrap      Dream            52.8  ...       4550.0    male  2008
307  Chinstrap      Dream            54.2  ...       4300.0    male  2008
309  Chinstrap      Dream            51.0  ...       4100.0    male  2008
313  Chinstrap      Dream            52.0  ...       4800.0    male  2008
315  Chinstrap      Dream            53.5  ...       4500.0    male  2008
321  Chinstrap      Dream            50.8  ...       4450.0    male  2009
323  Chinstrap      Dream            49.0  ...       4300.0    male  2009
329  Chinstrap      Dream            50.7  ...       4050.0    male  2009
333  Chinstrap      Dream            49.3  ...       4050.0    male  2009
339  Chinstrap      Dream            55.8  ...       4000.0    male  2009
342  Chinstrap      Dream            50.8  ...       4100.0    male  2009

[55 rows x 8 columns]
```

## Módulo 02 — exercício 4

```text
species  island  bill_length_mm  ...  body_mass_g   sex  year
215  Gentoo  Biscoe            54.3  ...       5650.0  male  2008
265  Gentoo  Biscoe            51.5  ...       5500.0  male  2009
267  Gentoo  Biscoe            55.1  ...       5850.0  male  2009
217  Gentoo  Biscoe            49.8  ...       5700.0  male  2008
227  Gentoo  Biscoe            48.6  ...       5800.0  male  2008

[5 rows x 8 columns]
```

## Módulo 02 — exercício 5

```text
species     island  bill_length_mm  ...  body_mass_g     sex  year
10  Adelie  Torgersen            37.8  ...       3300.0     NaN  2007
11  Adelie  Torgersen            37.8  ...       3700.0     NaN  2007
12  Adelie  Torgersen            41.1  ...       3200.0  female  2007
13  Adelie  Torgersen            38.6  ...       3800.0    male  2007
14  Adelie  Torgersen            34.6  ...       4400.0    male  2007

[5 rows x 8 columns]
```

## Módulo 03 — exemplo

```text
ausentes  percentual
species                   0    0.000000
island                    0    0.000000
bill_length_mm            2    0.581395
bill_depth_mm             2    0.581395
flipper_length_mm         2    0.581395
body_mass_g               2    0.581395
sex                      11    3.197674
year                      0    0.000000
Observações com massa: 342
```

## Módulo 03 — exercício 1

```text
bill_length_mm        2
bill_depth_mm         2
flipper_length_mm     2
body_mass_g           2
sex                  11
dtype: int64
```

## Módulo 03 — exercício 2

```text
0.5813953488372093
```

## Módulo 03 — exercício 3

```text
Removidas: 2
```

## Módulo 03 — exercício 4

```text
0    10.0
1     NaN
2     NaN
dtype: float64
2
```

## Módulo 03 — exercício 5

```text
0
```

## Módulo 04 — exemplo

```text
body_mass_g  body_mass_kg
0       3750.0          3.75
1       3800.0          3.80
2       3250.0          3.25
3          NaN           NaN
4       3450.0          3.45
0    adelie
1    adelie
2    adelie
3    adelie
4    adelie
Name: species, dtype: string
```

## Módulo 04 — exercício 1

```text
bill_length_mm  bill_length_cm
0            39.1            3.91
1            39.5            3.95
2            40.3            4.03
3             NaN             NaN
4            36.7            3.67
```

## Módulo 04 — exercício 2

```text
0     dream
1    biscoe
2      <NA>
dtype: string
```

## Módulo 04 — exercício 3

```text
sex    sexo_pt
0    male  masculino
1  female   feminino
2  female   feminino
3     NaN        NaN
4  female   feminino
```

## Módulo 04 — exercício 4

```text
species     island  bill_length_mm  ...  body_mass_g     sex  year
0    Adelie  Torgersen            39.1  ...       3750.0    male  2007
1    Adelie  Torgersen            39.5  ...       3800.0  female  2007
2    Adelie  Torgersen            40.3  ...       3250.0  female  2007
3    Adelie  Torgersen             NaN  ...          NaN     NaN  2007
4    Adelie  Torgersen            36.7  ...       3450.0  female  2007
..      ...        ...             ...  ...          ...     ...   ...
147  Adelie      Dream            36.6  ...       3475.0  female  2009
148  Adelie      Dream            36.0  ...       3450.0  female  2009
149  Adelie      Dream            37.8  ...       3750.0    male  2009
150  Adelie      Dream            36.0  ...       3700.0  female  2009
151  Adelie      Dream            41.5  ...       4000.0    male  2009

[152 rows x 8 columns]
```

## Módulo 04 — exercício 5

```text
species     island  bill_length_mm  ...     sex  year  razao_bico
0  Adelie  Torgersen            39.1  ...    male  2007    2.090909
1  Adelie  Torgersen            39.5  ...  female  2007    2.270115
2  Adelie  Torgersen            40.3  ...  female  2007    2.238889
3  Adelie  Torgersen             NaN  ...     NaN  2007         NaN
4  Adelie  Torgersen            36.7  ...  female  2007    1.901554

[5 rows x 9 columns]
```

## Módulo 05 — exemplo

```text
species  observacoes  massas_validas  massa_media_g
0     Adelie          152             151    3700.662252
1  Chinstrap           68              68    3733.088235
2     Gentoo          124             123    5076.016260
```

## Módulo 05 — exercício 1

```text
species
Adelie       152
Chinstrap     68
Gentoo       124
dtype: int64
```

## Módulo 05 — exercício 2

```text
median         std
species                      
Adelie     3700.0  458.566126
Chinstrap  3700.0  384.335081
Gentoo     5000.0  504.116237
```

## Módulo 05 — exercício 3

```text
island     sex   
Biscoe     female    80
           male      83
           NaN        5
Dream      female    61
           male      62
           NaN        1
Torgersen  female    24
           male      23
           NaN        5
dtype: int64
```

## Módulo 05 — exercício 4

```text
species     island  bill_length_mm  ...  year  media_especie    desvio_g
0  Adelie  Torgersen            39.1  ...  2007    3700.662252   49.337748
1  Adelie  Torgersen            39.5  ...  2007    3700.662252   99.337748
2  Adelie  Torgersen            40.3  ...  2007    3700.662252 -450.662252
3  Adelie  Torgersen             NaN  ...  2007    3700.662252         NaN
4  Adelie  Torgersen            36.7  ...  2007    3700.662252 -250.662252

[5 rows x 10 columns]
```

## Módulo 05 — exercício 5

```text
size  count
species               
Adelie      152    151
Chinstrap    68     68
Gentoo      124    123
```

## Módulo 06 — exemplo

```text
_merge
both          344
left_only       0
right_only      0
Name: count, dtype: int64
```

## Módulo 06 — exercício 1

```text
species nome_pt
0  Adelie  Adélia
1  Adelie  Adélia
2  Adelie  Adélia
3  Adelie  Adélia
4  Adelie  Adélia
```

## Módulo 06 — exercício 2

```text
sex             female         male
species                            
Adelie     3368.835616  4043.493151
Chinstrap  3527.205882  3938.970588
Gentoo     4679.741379  5484.836066
```

## Módulo 06 — exercício 3

```text
species          medida    mm
0  Adelie  bill_length_mm  39.1
1  Adelie  bill_length_mm  39.5
2  Adelie  bill_length_mm  40.3
3  Adelie  bill_length_mm   NaN
4  Adelie  bill_length_mm  36.7
```

## Módulo 06 — exercício 4

```text
Reconstrução correta
```

## Módulo 06 — exercício 5

```text
MergeError Merge keys are not unique in right dataset; not a many-to-one merge

Duplicates in right:
 species
 Adelie ...
```

## Módulo 07 — exemplo

```text
Linhas brutas: 541909 Linhas elegíveis: 530104
InvoiceNo           0
StockCode           0
Description      1454
Quantity            0
InvoiceDate         0
UnitPrice           0
CustomerID     135080
Country             0
dtype: int64
```

## Módulo 07 — exercício 1

```text
Linhas: 541909 Faturas: 25900
```

## Módulo 07 — exercício 2

```text
canceladas               9288
quantidade_negativa     10624
preco_nao_positivo       2517
sem_cliente            135080
dtype: int64
```

## Módulo 07 — exercício 3

```text
Receita bruta elegível (GBP): 10666684.54
```

## Módulo 07 — exercício 4

```text
Country
United Kingdom    9025222.084
Netherlands        285446.340
EIRE               283453.960
Germany            228867.140
France             209715.110
Australia          138521.310
Spain               61577.110
Switzerland         57089.900
Belgium             41196.340
Sweden              38378.330
Name: valor, dtype: float64
```

## Módulo 07 — exercício 5

```text
Ticket médio de faturas elegíveis (GBP): 534.403033266533
```

## Módulo 08 — exemplo

```text
InvoiceDate
2010-12-01     823746.140
2011-01-01     691364.560
2011-02-01     523631.890
2011-03-01     717639.360
2011-04-01     537808.621
2011-05-01     770536.020
2011-06-01     761739.900
2011-07-01     719221.191
2011-08-01     759138.380
2011-09-01    1058590.172
2011-10-01    1154979.300
2011-11-01    1509496.330
2011-12-01     638792.680
Freq: MS, Name: valor, dtype: float64
Cobertura: 2010-12-01 08:26:00 2011-12-09 12:50:00
```

## Módulo 08 — exercício 1

```text
InvoiceDate
2010-12     823746.140
2011-01     691364.560
2011-02     523631.890
2011-03     717639.360
2011-04     537808.621
2011-05     770536.020
2011-06     761739.900
2011-07     719221.191
2011-08     759138.380
2011-09    1058590.172
2011-10    1154979.300
2011-11    1509496.330
2011-12     638792.680
Freq: M, Name: valor, dtype: float64
```

## Módulo 08 — exercício 2

```text
2010-12-01    58960.79
2010-12-02    47748.38
2010-12-03    46943.71
2010-12-04        0.00
2010-12-05    31774.95
Freq: D, Name: valor, dtype: float64
```

## Módulo 08 — exercício 3

```text
2010-12-01             NaN
2010-12-02             NaN
2010-12-03             NaN
2010-12-04             NaN
2010-12-05             NaN
2010-12-06             NaN
2010-12-07    48553.784286
2010-12-08    46615.097143
2010-12-09    47449.068571
2010-12-10    49197.527143
Freq: D, Name: valor, dtype: float64
```

## Módulo 08 — exercício 4

```text
InvoiceDate
2010-12-01          NaN
2011-01-01   -16.070677
2011-02-01   -24.261103
2011-03-01    37.050354
2011-04-01   -25.058650
2011-05-01    43.273274
2011-06-01    -1.141559
2011-07-01    -5.581788
2011-08-01     5.550057
2011-09-01    39.446272
2011-10-01     9.105424
2011-11-01    30.694665
2011-12-01   -57.681733
Freq: MS, Name: valor, dtype: float64
```

## Módulo 08 — exercício 5

```text
0   2026-01-31
1          NaT
dtype: datetime64[us]
Falhas: 1
```

## Módulo 09 — exemplo

```text
ultima_compra  frequencia  monetario  recencia_dias
CustomerID                                                          
12346      2011-01-18 10:01:00           1   77183.60            326
12347      2011-12-07 15:52:00           7    4310.00              3
12348      2011-09-25 13:13:00           4    1797.24             76
12349      2011-11-21 09:51:00           1    1757.55             19
12350      2011-02-02 16:01:00           1     334.40            311
```

## Módulo 09 — exercício 1

```text
ultima_compra  frequencia  monetario  recencia_dias
CustomerID                                                          
14646      2011-12-08 12:12:00          73  280206.02              2
18102      2011-12-09 11:50:00          60  259657.30              1
17450      2011-12-01 13:29:00          46  194550.79              9
16446      2011-12-09 09:15:00           2  168472.50              1
14911      2011-12-08 15:54:00         201  143825.06              2
12415      2011-11-15 14:22:00          21  124914.53             25
14156      2011-11-30 10:54:00          55  117379.63             10
17511      2011-12-07 10:12:00          31   91062.38              3
16029      2011-11-01 10:27:00          63   81024.84             39
12346      2011-01-18 10:01:00           1   77183.60            326
```

## Módulo 09 — exercício 2

```text
16.45569092026202
```

## Módulo 09 — exercício 3

```text
ultima_compra  frequencia  monetario  recencia_dias
CustomerID                                                          
12347      2011-12-07 15:52:00           7    4310.00              3
12362      2011-12-06 15:40:00          10    5226.23              4
12381      2011-12-05 12:44:00           5    1845.31              5
12388      2011-11-24 12:30:00           6    2780.66             16
12395      2011-11-20 15:21:00          12    3018.63             20
```

## Módulo 09 — exercício 4

```text
ultima_compra  ...  participacao_acumulada
CustomerID                      ...                        
14646      2011-12-08 12:12:00  ...                0.031444
18102      2011-12-09 11:50:00  ...                0.060581
17450      2011-12-01 13:29:00  ...                0.082413
16446      2011-12-09 09:15:00  ...                0.101318
14911      2011-12-08 15:54:00  ...                0.117457

[5 rows x 5 columns]
```

## Módulo 09 — exercício 5

```text
Totais reconciliados
```

## Módulo 10 — exemplo

```text
Memória original: 19256 bytes; categórica: 644
```

## Módulo 10 — exercício 1

```text
Quantity  UnitPrice         Country
0         6       2.55  United Kingdom
1         6       3.39  United Kingdom
2         8       2.75  United Kingdom
3         6       3.39  United Kingdom
4         6       3.39  United Kingdom
```

## Módulo 10 — exercício 2

```text
168.2233362197876
```

## Módulo 10 — exercício 3

```text
4201.754385964912
```

## Módulo 10 — exercício 4

```text
Agregação por blocos conferida
```

## Módulo 10 — exercício 5

```text
C:\Users\jgbra\Documents\Codex\2026-11-09\preciso-organizar-um-projeto-de-um\outputs\curso_pandas\resultados\resumo_especies.csv
```

## Módulo 11 — exemplo

```text
Transformação reproduzida
```

## Módulo 11 — exercício 1

```text
Entrada preservada
```

## Módulo 11 — exercício 2

```text
Colunas ausentes: ['Country']
```

## Módulo 11 — exercício 3

```text
Regras conferidas
```

## Módulo 11 — exercício 4

```text
Resumo mensal reconciliado
```

## Módulo 11 — exercício 5

```text
{'pandas': '3.0.1', 'linhas_brutas': 541909, 'linhas_elegiveis': 530104, 'inicio': '2010-12-01 08:26:00', 'fim': '2011-12-09 12:50:00'}
```

## Módulo 12 — exemplo

```text
Country
United Kingdom    9025222.084
Netherlands        285446.340
EIRE               283453.960
Germany            228867.140
France             209715.110
Name: receita_bruta_elegivel_GBP, dtype: float64
Período observado: 2010-12-01 08:26:00 2011-12-09 12:50:00
```

## Módulo 12 — exercício 1

```text
receita_GBP  faturas   ticket_GBP
Country                                          
United Kingdom  9025222.084    18019   500.872528
Netherlands      285446.340       94  3036.663191
EIRE             283453.960      288   984.215139
Germany          228867.140      457   500.803370
France           209715.110      392   534.987526
```

## Módulo 12 — exercício 2

```text
Relatórios exportados
```

## Módulo 12 — exercício 3

```text
Gráfico salvo
```

## Módulo 12 — exercício 4

```text
United Kingdom representa 84.6% da receita elegível. Não reconciliamos cancelamentos e o período final está incompleto.
```

## Módulo 12 — exercício 5

```text
Fonte e período registrados
Regras de elegibilidade documentadas
Totais reconciliados
Ausências auditadas
Unidades e granularidade explícitas
Execução do início ao fim
Limitações apresentadas
```
