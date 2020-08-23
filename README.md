## Why the insurance was not affected by Covid

### 1. Installations
  For this analysis I a used anaconda distribution and the downloaded files of [SUSEP](http://www2.susep.gov.br/menuestatistica/SES/principal.aspx).
  To download the files, click in the link, scroll the page until you find the download link like in the image below:
  
![](HOW-DOWNLOAD.png)

### 2. Motivation
  This analyze is motivated by my Udacity nanodegree of Data Scientist. The theme for the project was based in my field of work which is life insurance.
  
### 3. File Descriptions
  The only file in this git is the jupyter notebook with the code and instructions for the gather, cleaning and plotting steps I took to write my article 
  at Medium.
  
### 4. How to Use this Notebook
  You should download the files from SUSEP and add the path of the folder you saved in the second code cell of the notebook. After that, feel free to run 
  each cell as you wish and on your own time.

### 5. Process and Results (CRISP-DM)
#### 5.1 Business Understanding
  The main goal of this effort is to see any major changes in the brasilian insurance market. For this reason, I will try to answer the 3 questions below:
  
  1. Is there any difference in premium collected?
  2. Do companies reduce their employees expanses?
  3. Does it has any changes in how companies donate?
  
  For a better understanding of particular change in any branch , It would be necessary to analyse a whole set of factors that are not in the escope of this work. 
  
#### 5.2 Data Understanding
 
 ##### Premium base
 The premium base is the core of our dataset and holds several importate rubrics for our analysis separated by branch. It has the following columns of interest:
   - damesano: year-month 202005
   - coenti: companies code
   - cogrupo: insurancer holding
   - coramo: branch's code :first 2 digits are the branch group and the last 2 are the specific branch
   - premio_emitido2: the premium 
   - premio_ganho: Earned Premium, according to the National Insurance brokers association (NIBA) glossary:
        
        "Insurance policies usually run for a period of 12 months. An insured
         can cancel a policy at any time and request a refund of premium.
         Therefore, insurers must only take into the books of account that
         portion of premium which corresponds to actual elapsed time on risk.
         That portion of premium which can be taken up in the accounts is
         called earned premium. That portion of premium yet to expire is"
        
   - sinistro_ocorrido: insurances claimed
   - desp_com: comercial expanses, like comission
 
 ##### Forsight base
 
  The forsight dataset is for acessing the forsight data which has a special ensurance type. The columns avalibe are:
    - coenti
    - noenti
    - tipoProd: product type. We want the "PrevTrad" which stands by traditional foresight
    - contrib: premium
    - benef: insuranced claimed
    
 ##### Income Statment base  
  The income_statment dataset contains:
    - coenti: companies code
    - damesano: year-month 202005
    - cmpid: field code in the income_statment
    - valor: values
    - seq: order of the field in the income_statment
    - quadro: type of accounting statement
 
  This dataset is that it is all in cumulative values and it has only one field that should be of type float, which is 'values'
 
 ##### Company Group base
  The company_group dataset contains:
    - coenti
    - damesano: year-month of that group info to the company
    - noenti: name of company
    - cogrupo: code of company group
    - nogrupo: name of company group
 
 ##### Fields base
 - The fields base has a end of term column. The last end of term is 210001 which stand for year 2020 and month 01 (janary)
 
#### 5.3 Data Preparation
  
  The premium base needed to change the decimal separator for the numerical values before get converted to numeric (brasilian decimal separator is ','). After conversion, the values should be transformed to absolute values once they have mixed sines for categories in the incame statment where there are no logic to change sine. For example, adminstrative expanses should not change sine. Finally the dataset was grouped by company and year.
  
  The Forsight base had the same steps of the premium base.
  
  For the income_statment base I filter the column 'quadro' to bring only the ones with ' 23' because this the code for the sheet of the income statment. Also, I    filtered values after 2016. The the rubrics we need for the analyses are:
    - 4069: that is the administrative expense (ae)
    - 6314: employee expenses 
    - 6315: third-party spending
    - 6317: publicity
    - 6319: donations
   Since this dataset has cumulative values, I changed it so each month represents the month alone. This way the final transformed dataset could merge with the rest.
  
  In the company group base I selected only the most update comany group. The table have the full history of each comapny holding name and we just need the most recent.
  
#### 5.4 Modeling
  There was no modeling, only a analysis guided by the statistical summaries and plotting.
#### 5.5 Evaluation
  The analisys is summarized in my [Medium Post](https://medium.com/@lukec.correa/why-the-insurance-was-not-affected-by-covid-775014ca0032) 

### 6. Licensing, Authors, Acknowledgements, etc.
  Special thanks to the stack overflow community.
