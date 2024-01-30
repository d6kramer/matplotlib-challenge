# matplotlib-challenge
Module 5 Challenge Repo

For this challenge, the completed submission file is included as "pymaceuticals_final.ipynb."

I have included some commentary in various areas of the final submission to assist with my thought process. This is mostly within the "Quartiles, Outliers, and Boxplots" segment of the assignment.

I have left in my working file (like the last assingment) that includes hashed/commented material, and is not cleaned up for presentation. This is to provide insight to some other thoughts/ideas/experiments conducted while completing the assignment.


Resources:

Fixing the histogram x-ticks alignment:

https://stackoverflow.com/questions/27083051/matplotlib-xticks-not-lining-up-with-histogram

-----------

## Xpert Learning Assistant exchange to properly write  for loop accessing a dataframe:

--why doesnt this code work: for row in tumor_volumes: if ["Drug Regimen"] == "Capomulin": capomulin_tumor.append(["Tumor Volume (mm3)"]) elif ["Drug Regimen"] == "Ramicane": ramicane_tumor.append(["Tumor Volume (mm3)"]) elif ["Drug Regimen"] == "Infubinol": infubinol_tumor.append(["Tumor Volume (mm3)"]) elif ["Drug Regimen"] == "Ceftamin": ceftamin_tumor.append(["Tumor Volume (mm3)"])
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

--Student User Logo
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

--Student User Logo
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

--how do you drop rows from a dataframe if they have a specific value in a column
Xpert User Logo

To drop rows from a DataFrame based on a specific value in a column, you can use the drop() method along with a condition. Here's an example:

import pandas as pd

Create a sample DataFrame
data = {'Name': ['John', 'Alice', 'Bob', 'Jane'],
        'Age': [25, 30, 35, 40],
        'City': ['New York', 'London', 'Paris', 'Tokyo']}
df = pd.DataFrame(data)

Drop rows where the 'City' column has the value 'Paris'
df = df.drop(df[df['City'] == 'Paris'].index)

Print the updated DataFrame
print(df)


Output:

   Name  Age      City
0  John   25  New York
1 Alice   30    London
3  Jane   40     Tokyo


In this example, the drop() method is used with the condition df['City'] == 'Paris' to drop the rows where the 'City' column has the value 'Paris'. The index attribute is used to specify the indices of the rows to be dropped. Finally, the updated DataFrame is assigned back to the variable df.

--Student User Logo
I get ValueError: Unable to coerce list of <class 'pandas.core.series.Series'> to Series/DataFrame
Xpert User Logo

I apologize for the confusion. It seems that you are trying to drop rows based on a specific value in a column using the drop() method, but encountering a ValueError related to the data type.

To drop rows based on a specific value in a column, you can use boolean indexing. Here's an example:

import pandas as pd

Create a sample DataFrame
data = {'Name': ['John', 'Alice', 'Bob', 'Jane'],
        'Age': [25, 30, 35, 40],
        'City': ['New York', 'London', 'Paris', 'Tokyo']}
df = pd.DataFrame(data)

Drop rows where the 'City' column has the value 'Paris'
df = df[~(df['City'] == 'Paris')]

Print the updated DataFrame
print(df)


Output:

   Name  Age      City
0  John   25  New York
1 Alice   30    London
3  Jane   40     Tokyo


In this example, the ~ operator is used to negate the condition df['City'] == 'Paris', which creates a boolean mask. This mask is then used to select the rows where the condition is True, effectively dropping the rows where the 'City' column has the value 'Paris'. The updated DataFrame is assigned back to the variable df.

------------

### Xpert Learning Assistant helping with box and whisker plot chart elements:

--Student User Logo
how do I change the color of an outlier on a box and whisker plot graph?
Xpert User Logo

To change the color of an outlier on a box and whisker plot graph, you can use the marker parameter in the plotting function. Here's an example using Python's matplotlib library:

import matplotlib.pyplot as plt

# Generate some sample data
data = [10, 12, 15, 17, 20, 22, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95, 100]

# Create a box and whisker plot
plt.boxplot(data, showfliers=True, flierprops={'marker': 'o', 'markerfacecolor': 'red', 'markersize': 8})

# Set the title and labels
plt.title("Box and Whisker Plot")
plt.xlabel("Data")
plt.ylabel("Values")

# Show the plot
plt.show()


--------------

In this example, the flierprops parameter is used to customize the appearance of the outliers. The 'marker' property is set to 'o' to use a circle marker, 'markerfacecolor' is set to 'red' to change the color to red, and 'markersize' is set to 8 to adjust the size of the marker. You can modify these properties to achieve the desired appearance for the outliers in your box and whisker plot.



I received help from my tutor, Justin, with a cleaner method of calculating final tumor volumes. He explained to me how to change a .groupby into a dataframe using .reset_index(), which allows for a new data merge. This was a much simpler way of approaching the problem than I had worked out on my own.  

Justin also assisted me with creating a second "for loop" that fit with my existing code to determine the outliers range for each treatment. 

Finally, Justin showed me a method of calculating a mean by two different columns using a .groupby method before creating a scatter plot. This was done in a single line, rather than doing two variables.

--------------

One of my classmates, Tianyue, informed me of the .duplicated and subset method in the 3rd cell in order to locate the correct duplicate mouse.

--------------