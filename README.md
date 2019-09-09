# POS-tagger-portuguese-nltk

Conjunto de POS-taggers treinados para classificação gramatical de sentenças em português. Os taggers foram treinados utilizando ferramentas da biblioteca [NLTK](https://www.nltk.org/), treinados usando o corpus [Mac-Morpho](http://nilc.icmc.usp.br/macmorpho/). Para maiores informações das classificações do corpus, consulte o [Manual](http://nilc.icmc.usp.br/macmorpho/macmorpho-manual.pdf).

O repositório inclui o notebook onde foi feito o treinamento dos POS-taggers.

-----
## Carregando e utilizando os POS-taggers treinados

Para utilizar eles, basta carregar o arquivo `pickle` gerado, como por exemplo, usando a função `load` da biblioteca `joblib`. Outras formas de carregar o `pickle` também devem funcionar.

```python
import joblib
from nltk import word_tokenize

folder = 'trained_POS_taggers/'
teste_tagger = joblib.load(folder+'POS_tagger_brill.pkl')
phrase = 'O rato roeu a roupa do rei de Roma'
teste_tagger.tag(word_tokenize(phrase))
```

`[('O', 'ART'),
 ('rato', 'N'),
 ('roeu', 'V'),
 ('a', 'ART'),
 ('roupa', 'N'),
 ('do', 'KS'),
 ('rei', 'N'),
 ('de', 'PREP'),
 ('Roma', 'NPROP')]`

-----
## Desempenho dos taggers treinados

Comparação do desempenho dos taggers. Para efeitos de comparação na taxa de palavras processadas, esse teste foi feito em Python 3.6, em uma máquina com processador Intel i7 e 16 GB de RAM.

| Tagger                 | Acurácia | Palavras/s | Tamanho  |
|------------------------|----------|------------|----------|
| POS_tagger_affix6.pkl  | 36.71%   | 72k        | 386 kB   |
| POS_tagger_unigram.pkl | 83.70%   | **82k**        | 790 kB   |
| POS_tagger_bigram.pkl  | 85.18%   | 67k        | 1.37 MB  |
| POS_tagger_trigram.pkl | 85.19%   | 61k        | 2.05 MB  |
| POS_tagger_brill.pkl   | **92.19%**   | 30k        | 2.09 MB  |
| POS_tagger_naive.pkl   | 83.97%   | 787        | 22.43 MB |