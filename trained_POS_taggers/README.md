# trained_POS_taggers

Pasta com os taggers treinados. É recomendado o uso do `POS_tagger_brill.pkl` ou `POS_tagger_trigram.pkl`, pois eles tem a melhor acurácia e uma taxa satisfatória de palavras taggeadas por segundo (Palavras/s).

| Tagger                 | Acurácia | Palavras/s | Tamanho  |
|------------------------|----------|------------|----------|
| POS_tagger_affix6.pkl  | 36.71%   | 72k        | 386 kB   |
| POS_tagger_unigram.pkl | 83.70%   | **82k**        | 790 kB   |
| POS_tagger_bigram.pkl  | 85.18%   | 67k        | 1.37 MB  |
| POS_tagger_trigram.pkl | 85.19%   | 61k        | 2.05 MB  |
| POS_tagger_brill.pkl   | **92.19%**   | 30k        | 2.09 MB  |
| POS_tagger_naive.pkl   | 83.97%   | 787        | 22.43 MB |

----

## Carregando arquivo pkl para uso dos POS-taggers treinados

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
