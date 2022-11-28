## Korean LExico-Grammatical Analyzer (KLEGA)

A Korean lexical diversity analyzer with following features:
- Remove typos from the raw texts automatically
- Tokenize using one of the six tokenizers (okt, komoran, mecab, kkma, hannanum from [konlpy](https://konlpy.org/en/latest/), [stanza](https://stanfordnlp.github.io/stanza/tokenize.html))
- Calculate lexical diversity using the package [taaled](https://github.com/kristopherkyle/TAALED)
- Analyze with and without function words

----------

## Setup
Currently, the execution of the code is available only on Windows environment with the Microsoft Office installed. (Microsoft Office is needed to remove typos from the raw text.)  

### Basic setup
Install the required packages using:
```angular2html
pip install -r requirements.txt
```

### Mecab tokenizer installation (optional)
Manual installation is needed to use the mecab tokenizer on Windows.  
Follow this instruction: [Korean](https://uwgdqo.tistory.com/363), [English(translated)](https://uwgdqo-tistory-com.translate.goog/363?_x_tr_sl=ko&_x_tr_tl=en&_x_tr_hl=ko&_x_tr_pto=wapp
)  
Default Mecab path is 'C:/mecab/mecab-ko-dic'  
To change the mecab path, change the path in the source code:  
https://github.com/hksyir/klega_lexdiv/blob/2e0d1a8b8bf03abfdbce62d445ce03d7a45fcf09/src/korean_tokenizer.py#L65

----------
## Data


----------
## Usage


----------
## Web Demo
A [web demo version](http://sooyeoncho.pythonanywhere.com) of Korean LExico-Grammatical Analyzer KLEGA is available now.  
Currently optimized for the Chrome browser on PC.


---------------

### To be updated
- analyze without typo removal option (for running on the other OS)

Please create a GitHub issue if you have any questions or bug-reports.