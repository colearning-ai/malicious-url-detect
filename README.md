# malicious-url-detect

### Using Neural Networks to classify various URLs  

<hr style=\"border:0.5px solid gray\"> </hr>

## Set-Up:  
__Pre-requisites :__ [conda](https://repo.anaconda.com/) and [git](https://git-scm.com/)     
*Please Note : All System Paths in the scripts, are coded in UNIX OS format, please convert '/' to "\\\ " for Windows OS.*
```
git clone https://github.com/Rohith-2/url_classification_dl.git
cd url_classification_dl
conda create -n pyenv python=3.8.5
conda activate pyenv
pip install -r requirements.txt
```
Feature Extraction :    
```
cd scripts/
python extract_Features.py
```
The features extracted are explained and visualised in this [Notebook](https://github.com/Rohith-2/url_classification_dl/blob/main/Notebook/DataProcessing.ipynb). The output training data after feature extraction is labbeled as [features.csv](https://github.com/Rohith-2/url_classification_dl/blob/main/FinalDataset/feature.csv) under FinalDataset. Feature extraction for each category of URLs took on an average 18-26 hours, which extends the total of 95 hours on an average.  
  
Training:
```
cd scripts/
python nn_Training.py
```
The output of the trained model is exported to the [models](https://github.com/Rohith-2/url_classification_dl/blob/main/models).  
  
Testing:
```
cd scripts/
python predict_args.py -i <url>
``` 
If you only wish to use the pre-trained model, please check [releases](https://github.com/Rohith-2/url_classification_dl/releases)    

Running the GUI locally:
```
cd GUI/
streamlit run predict.py
```
*All the above commands are from the home(url_classification_dl) folder*  
<hr style=\"border:0.5px solid gray\"> </hr>   
  
## GUI:  

![Screenshot 2021-05-21 at 12 18 06 PM](https://user-images.githubusercontent.com/55501708/119094445-a8e87280-ba2e-11eb-8241-56c580f073cb.png)  

## Data Description via Extracted Features:
| Feature Name | Feature Group | Feature Discription|
| --- | --- | --- |
| `URL Entropy` | URL String Characteristics | Entropy of URL |
| `numDigits` | URL String Characteristics | Total number of digits in URL string |
| `URL Lenght` | URL String Characteristics | Total number of characters in URL string |
| `numParameters` | URL String Characteristics | Total number of query parameters in URL |
| `numFragments` | URL String Characteristics | Total Number of Fragments in URL |
| `domainExtension` | URL String Characteristics | Domian extension |
| `num_%20` | URL String Characteristics | Number of '%20' in URL |
| `num_@` | URL String Characteristics | Number of '@' in URL |
| `has_ip` | URL String Characteristics | Occurence of IP in URL |
| `hasHTTP` |  URL domain features | Website domain has http protocol |
| `hasHTTPS` | URL domain features | Website domain has http protocol |
| `urllsLive` | URL domain features | The page is online |
| `daysSinceRegistration` | URL domain features | Number of days from today since	domain was registered |
| `daysSinceExpired` | URL domain features | Number of days from today since domain expired |
| `bodyLength` | URL page fratures | Total number of characters in URL's	HTML page |
| `numTitles` | URL page fratures | Total number of HI-H6 titles in URL's	HTML page |
| `numlmages` | URL page fratures | Total number of images embedded in URL's	HTML page |
| `numLinks` | URL page fratures | Total number of links embedded in URL's	HTML page |
| `scriptLength` | URL page fratures | Total number of characters in embedded scripts in URL's HTML page |
| `specialCharacters` | URL page fratures | Total number of special characters in URL's	HTML page |
| `scriptToSpecialCharacterRatio` | URL page fratures | The ratio of total length of embedded scripts to special characters in HTML page |
| `scriptToBodyRatio` | URL page fratures | The ratio of total length of embedded scripts to total number of characters in HTML page |  


  
#### Plot depecting numerous features normalised(ranging from 0 to 1) and the mean of all the classes. 
![download](https://user-images.githubusercontent.com/55501708/119180825-6b1b3680-ba8e-11eb-83a1-e68dc29251d6.png)

## Performance metric:  
![Screenshot 2021-05-20 at 6 32 01 PM](https://user-images.githubusercontent.com/55501708/118983160-c1f31400-b999-11eb-8fd9-dd54a204f6d0.png)  

<hr style=\"border:0.5px solid gray\"> </hr>   
