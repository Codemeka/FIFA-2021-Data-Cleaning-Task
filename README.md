# FIFA-2021-Data-Cleaning-Task
![wp6710683-fifa-21-wallpapers](https://user-images.githubusercontent.com/100303051/235518736-8ebdd9a1-0a88-4cbd-902a-5f1e0691a20a.jpg)
--
## INTRODUCTION
This is a break down of the data wrangling & cleaning process for FIFA '21 dataset. This data set was provided as part of a challenge #Datacleaningchallenge launched on twitter by data ethusiasts to test the prowess of newbies , intermediate and pro Data analyst alike for a large messy dataset.

The data set contains 18,979 rows and 77 columns of football players statistics and demography in 2021 The dataset is publicly available on kaggle which contains data scrapped from sofifa. The data file also includes a Data dictionary as well as a column named player url which contains a link to the player profile on sofifa to give the analyst furher insight and full details of the player in view in case of missing information.

## TOOLS
* Power Query

## DATA CLEANING PROCESS
The first step of cleaning the data after importing was removing whitespaces, this was done by clicking the viewtab and ticked remove whitespaces.

## WHITESPACES
![224610838-f6b78c4b-b204-42d9-b158-f7aeacb6cda8](https://user-images.githubusercontent.com/100303051/235520620-555d3af1-7fc7-44d4-adcf-482b24fe3345.png)
![224610689-763b528d-9eed-431a-8b7d-2d5a54abaa32](https://user-images.githubusercontent.com/100303051/235520683-0964430c-a4a5-4d5c-8242-5c6d87dded49.png)

## NAMES
The Name and Longname column were Standardised by splitting delimiters and replacing empty rows to generate a first name and last name column. Hyphenated or double last names like De Bruyne & Van Dijk were also kept in the right format.

![224680924-00835e64-6273-4c6e-aab9-a472fe3cea3b](https://user-images.githubusercontent.com/100303051/235521994-1f799eae-61fa-418f-85ba-36042b0099fc.png)
![224681183-81a31f33-425e-4105-a848-ebf7d3134ecc](https://user-images.githubusercontent.com/100303051/235522043-acc24032-46bf-4792-9087-e8206586b608.png)

## PERCENTAGES
As advised by the Data Dictionary, the columns OVA and POT were reformatted to reflect percentages. Column from example was used to add % to the end of the row figures, then the data type was changed to percentage.

![224689449-f6a490f1-e016-4058-9373-71487095283d](https://user-images.githubusercontent.com/100303051/235523085-5eb9158f-bb9d-4fed-bd5a-68079456698a.png)
![224689726-1884d63f-e22e-4b70-8a67-3dbead6aa4ed](https://user-images.githubusercontent.com/100303051/235523130-4a2fab85-c88e-4396-8a55-bf84297099c5.png)

## CLUBS
Some club names started with i.e; fc koln & fc union Berlin these were normalised. Some club names were diacritical and this makes alphabetical sorting to fail during visualization.

![224834902-356b3ed5-c7e0-489c-87d2-b3602bc91364](https://user-images.githubusercontent.com/100303051/235526006-7f1cfc58-75ad-4bac-a5e8-490215d05999.png)
![224835627-e81bbc9a-7c95-41e9-a1e3-5be5cef1ac2c](https://user-images.githubusercontent.com/100303051/235526073-5163c018-d46b-4b1f-88b7-08ef9b38c258.png)

## CONTRACT
This column contained inconsistent data type and format, hence this was regularized using a combination of 3 columns namely;Contracts, Joined and Loan end date.The filter view reveals players whose contract column specify that they are on loan tallies with the year on the Loan end date column. While players whose contract indicates free transfer, tallies with those players without a parent club and with no wage or value or release clause.This were replaced with null as there is no specified loan end date since they're not on contract and have no recorded wages. These players should therefore be dropped during visualization.

At the end of the cleaning, splitting and merging of columns, two columns became the result: contract start and contract end which displays only the year info as lack of more data prevented further date drill down.

![224838470-25cd2741-d7bf-479b-8ff7-14d2917f498c](https://user-images.githubusercontent.com/100303051/235529617-4931cbd7-0a3c-4f8c-9bbe-069d4baac043.png)
![224838770-df41bf1a-5391-4bdd-8a17-99c4a7da1cb5](https://user-images.githubusercontent.com/100303051/235529680-d9ac685b-6f60-40db-8b2e-c2b984cbdb76.png)


## VALUE, WAGE & RELEASE CLAUSE
These three columns contains euro values in shortenend format, where 1,500 euros was written as 1.5k and one million ,five hundred euros as 1.5m. The goal is to standardise the columns and convert to US dollars. Hence the approach used was to dropped the euro symbol from all rows using find and replace, then split columns by M and K.
First step was to create a New custom column which If column 1 contains M multiplies the figure by 1,000,000 then if column 1 contains K multiply by 1000 else return the figure on the original column, this else function handles the values, wages or release clause in hundreds having no K or M attached (some players earn as low as 500 euro wage).

This approach gives the full numeric form of the value , wage or release clause but that is not all. To convert this full numeric digits to USD, the average euro to USD exchange rate of 1.183 was used as this was the average exchange rate as at 2021 which our data is based on.

![224848874-1db3b234-8f91-4a58-8aa8-62e4db072d38](https://user-images.githubusercontent.com/100303051/235531374-e1864a47-4af2-43ff-9e1d-548abba1103a.png)
![224849112-0e74cdb0-ceb6-4a38-bc4d-4efc3f9ccf43](https://user-images.githubusercontent.com/100303051/235531407-d9acf8f3-fd4b-4469-a453-4c5990556de0.png)


_Disclaimer: This dataset was gotten from Kaggle, a dummy dataset._








