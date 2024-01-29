# matplotlib-challenge
Module 5 Challenge Repo


Resources:

Fixing the histogram x-ticks alignment:

https://stackoverflow.com/questions/27083051/matplotlib-xticks-not-lining-up-with-histogram

-----------

## Xpert Learning Assistant exchange to properly write  for loop accessing a dataframe:

why doesnt this code work: for row in tumor_volumes: if ["Drug Regimen"] == "Capomulin": capomulin_tumor.append(["Tumor Volume (mm3)"]) elif ["Drug Regimen"] == "Ramicane": ramicane_tumor.append(["Tumor Volume (mm3)"]) elif ["Drug Regimen"] == "Infubinol": infubinol_tumor.append(["Tumor Volume (mm3)"]) elif ["Drug Regimen"] == "Ceftamin": ceftamin_tumor.append(["Tumor Volume (mm3)"])
Xpert User Logo

There are a few issues with the code you provided. 

First, when checking the value of the "Drug Regimen" column, you should use the variable row instead of ["Drug Regimen"]. 

Second, when appending the tumor volume to the respective lists, you should append the value of the "Tumor Volume (mm3)" column from the current row, not a list containing the column name.

Here's the corrected code:

for row in tumor_volumes:
    if row["Drug Regimen"] == "Capomulin":
        capomulin_tumor.append(row["Tumor Volume (mm3)"])
    elif row["Drug Regimen"] == "Ramicane":
        ramicane_tumor.append(row["Tumor Volume (mm3)"])
    elif row["Drug Regimen"] == "Infubinol":
        infubinol_tumor.append(row["Tumor Volume (mm3)"])
    elif row["Drug Regimen"] == "Ceftamin":
        ceftamin_tumor.append(row["Tumor Volume (mm3)"])


Make sure to replace tumor_volumes with the appropriate variable that contains the data you want to iterate over.

Student User Logo
string indices must be integers
Xpert User Logo

I apologize for the confusion. It seems like you are trying to access the values of the "Drug Regimen" and "Tumor Volume (mm3)" columns in each row of the tumor_volumes dataset.

To access the values of specific columns in a row, you should use square brackets [] with the column name as the key. However, the error message you encountered suggests that the variable row is a string, and string indices must be integers.

To resolve this issue, please ensure that the tumor_volumes variable is a list of dictionaries, where each dictionary represents a row of data with column names as keys and corresponding values.

For example:

tumor_volumes = [
    {"Drug Regimen": "Capomulin", "Tumor Volume (mm3)": 45.0},
    {"Drug Regimen": "Ramicane", "Tumor Volume (mm3)": 40.0},
    {"Drug Regimen": "Infubinol", "Tumor Volume (mm3)": 55.0},
    {"Drug Regimen": "Ceftamin", "Tumor Volume (mm3)": 50.0}
]

capomulin_tumor = []
ramicane_tumor = []
infubinol_tumor = []
ceftamin_tumor = []

for row in tumor_volumes:
    if row["Drug Regimen"] == "Capomulin":
        capomulin_tumor.append(row["Tumor Volume (mm3)"])
    elif row["Drug Regimen"] == "Ramicane":
        ramicane_tumor.append(row["Tumor Volume (mm3)"])
    elif row["Drug Regimen"] == "Infubinol":
        infubinol_tumor.append(row["Tumor Volume (mm3)"])
    elif row["Drug Regimen"] == "Ceftamin":
        ceftamin_tumor.append(row["Tumor Volume (mm3)"])


Please make sure that the tumor_volumes variable is in the correct format, and let me know if you have any further questions.

Student User Logo
what if tumor_volumes is a dataframe
Xpert User Logo

If tumor_volumes is a DataFrame, you can use the iterrows() method to iterate over the rows and access the values of the "Drug Regimen" and "Tumor Volume (mm3)" columns.

Here's an example of how you can modify the code to work with a DataFrame:

capomulin_tumor = []
ramicane_tumor = []
infubinol_tumor = []
ceftamin_tumor = []

for index, row in tumor_volumes.iterrows():
    if row["Drug Regimen"] == "Capomulin":
        capomulin_tumor.append(row["Tumor Volume (mm3)"])
    elif row["Drug Regimen"] == "Ramicane":
        ramicane_tumor.append(row["Tumor Volume (mm3)"])
    elif row["Drug Regimen"] == "Infubinol":
        infubinol_tumor.append(row["Tumor Volume (mm3)"])
    elif row["Drug Regimen"] == "Ceftamin":
        ceftamin_tumor.append(row["Tumor Volume (mm3)"])


In this code, iterrows() is used to iterate over each row of the DataFrame. The index variable represents the index of the row, and the row variable represents the values of the row as a Series. You can access the values of specific columns using square brackets [] with the column name as the key.

Make sure to replace tumor_volumes with the actual name of your DataFrame.

---------

## Learning the mask technique from Xpert Learning Assistant to drop undesired rows from a Dataframe:

how do you drop rows from a dataframe if they have a specific value in a column
Xpert User Logo

To drop rows from a DataFrame based on a specific value in a column, you can use the drop() method along with a condition. Here's an example:

import pandas as pd

### Create a sample DataFrame
data = {'Name': ['John', 'Alice', 'Bob', 'Jane'],
        'Age': [25, 30, 35, 40],
        'City': ['New York', 'London', 'Paris', 'Tokyo']}
df = pd.DataFrame(data)

### Drop rows where the 'City' column has the value 'Paris'
df = df.drop(df[df['City'] == 'Paris'].index)

### Print the updated DataFrame
print(df)


Output:

   Name  Age      City
0  John   25  New York
1 Alice   30    London
3  Jane   40     Tokyo


In this example, the drop() method is used with the condition df['City'] == 'Paris' to drop the rows where the 'City' column has the value 'Paris'. The index attribute is used to specify the indices of the rows to be dropped. Finally, the updated DataFrame is assigned back to the variable df.

Student User Logo
I get ValueError: Unable to coerce list of <class 'pandas.core.series.Series'> to Series/DataFrame
Xpert User Logo

I apologize for the confusion. It seems that you are trying to drop rows based on a specific value in a column using the drop() method, but encountering a ValueError related to the data type.

To drop rows based on a specific value in a column, you can use boolean indexing. Here's an example:

import pandas as pd

### Create a sample DataFrame
data = {'Name': ['John', 'Alice', 'Bob', 'Jane'],
        'Age': [25, 30, 35, 40],
        'City': ['New York', 'London', 'Paris', 'Tokyo']}
df = pd.DataFrame(data)

### Drop rows where the 'City' column has the value 'Paris'
df = df[~(df['City'] == 'Paris')]

### Print the updated DataFrame
print(df)


Output:

   Name  Age      City
0  John   25  New York
1 Alice   30    London
3  Jane   40     Tokyo


In this example, the ~ operator is used to negate the condition df['City'] == 'Paris', which creates a boolean mask. This mask is then used to select the rows where the condition is True, effectively dropping the rows where the 'City' column has the value 'Paris'. The updated DataFrame is assigned back to the variable df.

------------

