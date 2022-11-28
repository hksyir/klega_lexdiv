## Korean LExico-Grammatical Analyzer (KLEGA)

A Korean lexical diversity analyzer with following features:
- Remove typos from the raw texts automatically
- Tokenize using one of the six tokenizers (okt, komoran, mecab, kkma, hannanum from [konlpy](https://konlpy.org/en/latest/), [stanza](https://stanfordnlp.github.io/stanza/tokenize.html))
- Calculate lexical diversity using the package [taaled](https://github.com/kristopherkyle/TAALED)
- Analyze with and without function words


## Setup
Currently, the execution of the code is available only on Windows environment with Microsoft Office installed. (Microsoft Office is needed to remove typos from the raw text.)  

### Basic setup
Install the required packages using:
```angular2html
pip install -r requirements.txt
```

### Mecab tokenizer installation (optional)
Manual installation is needed to use the mecab tokenizer on Windows. 
Follow this instruction to install Mecab: [Korean](https://uwgdqo.tistory.com/363), [English(translated)](https://uwgdqo-tistory-com.translate.goog/363?_x_tr_sl=ko&_x_tr_tl=en&_x_tr_hl=ko&_x_tr_pto=wapp
)  

Default Mecab path in the source code is set to: 'C:/mecab/mecab-ko-dic'  
You can change the path in the source code directly if you installed Mecab in different path:  
https://github.com/hksyir/klega_lexdiv/blob/2e0d1a8b8bf03abfdbce62d445ce03d7a45fcf09/src/korean_tokenizer.py#L65


## Data (Input)
The Korean texts (input data) for analyzing the lexical diversity must be in plain text files with the extension ```.txt```.
You can process multiple files, which are stored in one ```data``` directory.  
e.g. ```data/file1.txt``` ```data/file2.txt``` ```data/file3.txt```


## Usage
For the basic usage, run:
```angular2html
python src/main.py -i [INPUT_DIR]
```
This will process your texts in your ```INPUT_DIR``` using ```okt``` tokenizer and save the output in the ```result``` directory, without parallel analysis, processing contents words only (without processing functional words)   

### Tokenizers
To choose tokenizers, use the argument ```-t```. You can process same inputs multiple times using different tokenizers.  
e.g. To use ```okt``` and ```mecab```, run this command:
```angular2html
python src/main.py -i [INPUT_DIR] -t okt mecab
```
Currently available tokenizers are: ```okt``` ```mecab``` ```hannanum``` ```komoran``` ```kkma``` ```stanza```

### Processing functional words
To process functional words as well (contents words and functional words), add ```-f``` flag in the command:
```angular2html
python src/main.py -i [INPUT_DIR] -f
```

### Parallel analysis
To do parallel analysis, add ```-p``` flag in the command:
```angular2html
python src/main.py -i [INPUT_DIR] -p
```

### Run with all options
If you want to run multiple times with all options (processing functional words Y/N and parallel analysis Y/N), run this command:
```angular2html
python src/main.py -i [INPUT_DIR] -a
```
This will use ```okt``` tokenizer to run all the options.  
You still need to specify tokenizers you want. e.g. :
```angular2html
python src/main.py -i [INPUT_DIR] -a -t mecab okt hannanum
```

## Result (Output)
result files

## Web Demo
A [web demo version](http://sooyeoncho.pythonanywhere.com) of Korean LExico-Grammatical Analyzer KLEGA is available now.  
Currently optimized for the Chrome browser on PC.




### To be updated
- analyze without typo removal option (for running on the other OS)

Please create a GitHub issue if you have any questions or bug-reports.