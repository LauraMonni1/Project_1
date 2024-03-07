Project_1_README

1. Datasets on neuronal cell types in the human brain (electrophysiology and morphology data)
2. There are two main datasets in one, regarding human brain: all human cells (donor__species = "homo sapiens", so neurons cominf from either tumor or epilepsy patients) and human cells from epilepsy patients (donor__disease_state = "epilepsy")
3. I extraced the dataset with the provided API and instructions (RMA quesries and criteria). T
4. I will then to compare the different parameters regarding neuronal activity and morphology between the two conditions, brain tumor and epilepsy.

- The dataset is extracted with two functions that are defined and saved in the file "functions.py" (details below)
- The extracted raw dataset is saved as:"raw_data.csv" = raw/original DataFrame on all human cell types

- This raw dataset is then cleaned with different functions, which were defined and save in the file "functions.py"

The cleaned dataset is then saved as "cleaned_data.csv" = the copy of the raw DataFrame cleaned


 PROCESS TO EXTRACT DATA AND OBTAIN A PANDAS DATAFRAME FROM API RETURNING XML FILES (with my functions.py):

1) import pandas, numpy, requests and xml.etree.ElementTree libraries
2) import functions as fun (import the functions of functions.py, use "fun" as alias)
3) define url
4) define criteria to extract specific data (the criteria are specified in the Allen Brain website as RMA queries and are strings)
5) create a variable "response" that stores the get request taking as argument the url and as params the criteria (params = {"criteria":criteria})
6) check the status_code of "response" (has to be 200, so "approved")
7) create the variable "data" that stores the XML file ("response") as text (using the attribute .text)
8) Find the main root with ElementTree library method et.fromstring()
9) Look at the first lines of XML document to find the first tag within the root that incorporates all elements (usually the tag in the second line) -> print(data)[:10]
10) Execute the function create_dataframe() taking as argument the first tag found at point 9 as string (".//first_tag")
11) Save the dataframe as "raw_data.csv" -> df.to_csv("raw_data.csv")
12) create a copy of the raw dataframe and work on it!



The data analysis is then carried out taking advantage of the many different plots created with seaborn and matplolib.