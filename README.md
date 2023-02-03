# Python_Pyber_AnalysisOverview
The purpose of this data analysis is to identify ride sharing metrics/trends based on city type. Once this is complete we will were tasked with creating a representation of the total weekly fares and based on the city types. This representation will help improve accesibility to ride sharing services and determine ride affordability for each type by providing a clear picture as to what challenges people from different city types may be facing and what solutions we can implement to mitigate the challenges our customers are facing

The first step in this process is to load and read all CSVs that will be involved in the analysis process. Here we read "city_data.csv" and "ride_data.csv". After I read each CSV into jupyter notebook I am sure to display it via head.() or simply by adding it into a cell and running it to ensure it was properly read/imported.
![2B202A0A-D696-4915-8260-A0B822782E10](https://user-images.githubusercontent.com/122326425/216694404-d5764e1f-1226-419c-9540-a22692a0bdb0.jpeg)
![D3754483-FADF-4BD5-AE2F-2958648140E3](https://user-images.githubusercontent.com/122326425/216694770-02212191-9674-4514-8088-5e46dc95aad5.jpeg)


For the next step I decided to merge both CSVs("city_data.csv", "ride_data.csv") on the "city" column as which is a column that both datasets have individually. This is similar to how we use joins in SQL. The finished table will be named pyber_data_df which is why we are setting it equal to the merged datase.

![6A197297-A813-4D1C-AFF3-FCC5CADEF1B4](https://user-images.githubusercontent.com/122326425/216694910-ab9f422b-99ed-4510-a516-cbfd81eb5a6d.jpeg)


Next I began gathering metrics. The first metric is to discover the amount of rides per city type from January to April 2019. We can see the Rural city type has the least amount of total rides with 125 in 4 months. Secondly we display the number of drivers by city type. We can see the number of drivers for Rural cities is significantly less than that of Suburban and Urban city types. We then display the total amount of fares for each city type. Rural is significantly less than both Urban and Suburban once more. After this I calculate average price per ride for each city type. Rural is the most expensive as they have the least amount of available drivers and the least amount of fares. Finally we calculate the average fare per driver for eah city type and as estimated, Rural is still the highest average fare by driver price.

![1A83B8BC-61D6-4202-863E-2F214CDE88E5](https://user-images.githubusercontent.com/122326425/216695058-161114f6-9d17-4668-b37d-4a11e4ad9cfe.jpeg)

Once I gathered everything it was important to put all of our findings in a central location so viewers could see everything quickly and be able to conclude metrics from the dataset efficiently. I did this by putting all the metrics into a dictionary and using a key word to identify each metric. After that we converted it into a dataframe and printed the results as:

![DEF8F341-6970-4D58-97F0-E623DCD13B16](https://user-images.githubusercontent.com/122326425/216695152-3908af8f-3478-4f86-9961-b8cc280a1e77.jpeg)

Next I decided to make the dataframe more presentable by deleting the index name which in this case was'type'. I ran "pyber_summary_df.index.name = None" to complete the task and ran "pyber_summary_df" in the cell afterwards to see if it did as I intended. With everything aligned I was successfully able to delete the index name and the ending result came out to: CE0A9EE7-E597-48A5-9AAE-5124873F510D

![B903BB4F-B0C9-4901-BC4E-5ADF91E1FE7D](https://user-images.githubusercontent.com/122326425/216695269-684c158d-452a-4b4f-b3fa-da5aed953834.jpeg)

Next I changed the fomatting of the columns so the numbers are easier to understand. We want to ensure there are dollar signs, commas, etc so we know what the number in the column is representing. I did this by specifying the dataframe, specifying the column and specifying the format integrity of each column. The results: 
![F64E5F7E-7882-4EC5-A02A-492B4E8819F9](https://user-images.githubusercontent.com/122326425/216699734-c76c1f9f-28db-4d32-a171-0810566a4f78.jpeg)


For the second portion of the project I went in and created a new DataFrame showing the sum of the fares for each date where the indices are the city type and date. To accomplish this I used a .groupby and a .sum function and specified .fare to_fame. The results:
![1C9EF290-26D3-424D-8A53-E4676876500A](https://user-images.githubusercontent.com/122326425/216698488-619e83f2-5b5a-4986-ae0a-0cd52068a41e.jpeg)



I then went in and reset the index so I would be allowed to use the pivot() function which allowed me to create a pivot table
![4538C86F-90A7-488D-B118-CBA21325C7F5](https://user-images.githubusercontent.com/122326425/216698683-8d534baa-b92b-41c4-b818-15b570e4510d.jpeg)


Next I needed to create a pivot table with the 'date' as the index, the columns ='type', and values='fare' to get the total fares for each type of city by the date. Since I reset the index above I was now allowed to use the pivot() function. After creating the pivot table we then need to create a new DataFrame from the pivot table DataFrame using based on dates, '2019-01-01':'2019-04-28'. After that I convert the datatype of the index to datetime 
![73CE9363-DE17-4134-BB3D-6CE534E53748](https://user-images.githubusercontent.com/122326425/216700819-8058238d-1b1b-40ae-b9ac-a2e212f08b9d.jpeg)

![9EBB8384-70BD-4BEC-80A1-06C129F044C7](https://user-images.githubusercontent.com/122326425/216700861-02caea3a-f0b6-4b73-93a2-a390eabedbb1.jpeg)

Index datatype conversion confirmation![Uploading 9EBB8384-70BD-4BEC-80A1-06C129F044C7.jpeg…]()


![58D04D66-6FDB-4A0C-A90E-77151407A804](https://user-images.githubusercontent.com/122326425/216699098-b2ed7524-211d-42f6-9f2c-0f7f6e39432e.jpeg)


After I made the datetimme conversion I could now use the resample function properly. I needed to create a new DataFrame using the "resample()" function by week 'W' and get the sum of the fares for each week. Results: E1EA401E-43CB-4848-8EE8-13C0A79F7617
![552A0106-E7BF-4AC6-BDA7-BA28F4D53390](https://user-images.githubusercontent.com/122326425/216699036-6d178ddb-7ac0-48b3-b95d-18782b90ee46.jpeg)

Finally I transitioned into the visualization element. The goal in this scenario is to create a chart that displays the total fares by city type. First and foremost I went in and imported my dependencies which in this case is "from matplotlib import style". Secondly I stated the actual style type ("fivethirtyeight"). After the style was set I made sure to go in and format graph properties which entails specifying plt.title, plt.ylabel, plt.xlabel, and plt.grid. Lastly I specified details on the chart legend. The final results is as follows.
![C11EDF91-60DE-4CE9-9DE9-49CC81E18FFD](https://user-images.githubusercontent.com/122326425/216698995-45cb0763-2491-41eb-a5ca-d40c7f58d580.jpeg)

### Key Findings
- Pyber is used mainly in Urban cities
- There are more drivers in Urban cities than there are in Suburban or Rural cities. 
- Fares are most expensive in Rural cities
- Drivers in Rural areas get significantly less business than drivers in Urban and Suburan areas. Drivers in Rural areas likely do not drive full time due to the lack of users
