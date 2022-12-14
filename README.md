## Korean LExico-Grammatical Analyzer (KLEGA)

A Korean lexical diversity analyzer with following features:
- Remove typos from the raw texts automatically
- Tokenize using one of the six tokenizers (okt, komoran, mecab, kkma, hannanum from [konlpy](https://konlpy.org/en/latest/), [stanza](https://stanfordnlp.github.io/stanza/tokenize.html))
- Calculate lexical diversity using the package [taaled](https://github.com/kristopherkyle/TAALED)
- Analyze with and without function words


## Setup
Note: The typo removal function is available only on Windows environment with Microsoft Office installed. To be able to execute the code on other OS environments, the typo removal function must be off by using the flag ```no-typo-removal```. Refer below for the usage.
### Basic setup
Install the required packages using:
```angular2html
pip install -r requirements.txt
```

[//]: # (### Mecab tokenizer installation &#40;optional, only for Windows&#41;)

[//]: # (Manual installation is needed to use the mecab tokenizer on Windows. )

[//]: # (Follow this instruction to install Mecab: [Korean]&#40;https://uwgdqo.tistory.com/363&#41;, [English&#40;translated&#41;]&#40;https://uwgdqo-tistory-com.translate.goog/363?_x_tr_sl=ko&_x_tr_tl=en&_x_tr_hl=ko&_x_tr_pto=wapp)

[//]: # (&#41;  )

[//]: # ()
[//]: # (Default Mecab path in the source code is set to: ```C:/mecab/mecab-ko-dic```   )

[//]: # (You can change the path in the source code directly if you installed Mecab in different path:  )

[//]: # (https://github.com/hksyir/klega_lexdiv/blob/2e0d1a8b8bf03abfdbce62d445ce03d7a45fcf09/src/korean_tokenizer.py#L65)

[//]: # ()

## Data (Input)
The Korean texts (input data) for analyzing the lexical diversity must be in plain text files with the extension ```.txt```.
You can process multiple files, which are stored in one ```data``` directory.  
e.g. ```data/text1.txt``` ```data/text2.txt``` ```data/text3.txt```


## Usage
For the basic usage, run:
```angular2html
python src/klega/main.py -i [INPUT_DIR]
```
This will process your texts in your ```INPUT_DIR``` using (default) ```okt``` tokenizer and save the output in the ```result``` directory, processing contents words only.
```[INPUT_DIR]``` must be a directory where all the text files to process are stored.  

### Tokenizers
To choose different tokenizers, use the argument ```-t```. You can process the same input multiple times using different tokenizers. E.g. To use ```okt``` and ```mecab```, run this command:
```angular2html
python src/klega/main.py -i [INPUT_DIR] -t okt mecab
```
Currently available tokenizers are: ```okt``` ```mecab``` ```hannanum``` ```komoran``` ```kkma``` ```stanza```

### Processing functional words
To process functional words as well (contents words and functional words), add ```-f``` flag in the command:
```angular2html
python src/klega/main.py -i [INPUT_DIR] -f
```
Note: For ```stanza``` tokenizer, ```-f``` must be always added. ```stanza``` does not have an option to extract content words only.


### Changing output directory
The default output directory is ```result```. If you want to change the output directory, use the flag ```-o```:
```angular2html
python src/klega/main.py -i [INPUT_DIR] -o [OUTPUT_DIR]
```

### Turning off the typo removal function (for Mac and Linux)
Currently, the typo removal function is available only on Windows environment with Microsoft Office installed. To be able to execute the code on other OS environments, the typo removal function must be off by using the flag ```-no-typo-removal```:
```angular2html
python src/klega/main.py -i [INPUT_DIR] -no-typo-removal
```

### Example usage
If you want to process the files in the directory ```input``` using the tokenizer set ```hannanum``` and ```komoran```, processing contents words only, and save the output to the directory ```output```:
```angular2html
python src/klega/main.py -i input -o output -t hannanum komoran 
```

## Result (Output)
Three kinds of output files are saved after a successful run. 
### Logfile   
The log file ```log_[yymmdd]_[hhmm].log``` shows the configuration of your run, e.g. selected tokenizer, processed files, etc.
### Processed Files
The tsv file ```processed_data.tsv``` includes raw texts (column ```raw```), list of typos removed (column ```typo```) and processed texts (column ```processed```) to tokenize and calculate lexical diversity. This file is useful when you want to reuse the processed texts for other text manipulation or evaluation. Note: If ```no-typo-removal``` set, this file is not generated.
### Lexical Diversity Values
The list of lexical diversity values are stored as a tsv format in the file ```[TOKENIZER]_[FUNCTION_WORD_OPTION].tsv```.
E.g. the configuration of the output file ```hannanum_content_only.tsv``` is ```hannanum```, without function words.  
This is an example result file:

![](image/result.png)

## Web Demo
A [web demo version](http://sooyeoncho.pythonanywhere.com) of Korean LExico-Grammatical Analyzer KLEGA is available now.  
Currently optimized for the Chrome browser on PC. (under development)



Please create a GitHub issue if you have any questions or bug-reports.  
Email to the writers: [Sooyeon Cho](mailto:sooyeon.cho@uzh.ch) & [Hakyung Sung](mailto:hsung@uoregon.edu)
