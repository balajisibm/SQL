# SQL

The data set that I have considered to perform the given assignment are given below 
Dataset 1: fda_enforcement -- `bigquery-public-data.fda_food.food_enforcement`
Dataset 2: fda_events -- `bigquery-public-data.fda_food.food_events`
The above 2 dataset are available in GCP under bigquery-public-data under the section name fda_foods

Question-1:
Count the number of classification in each country   to show how many product are being violated by each country where the number of products violated greater than  4

SQL Code-1:

```SELECT distinct count(classification) ,country

FROM `bigquery-public-data.fda_food.food_enforcement` 

group by country

having count(classification) > 4
```

![image](https://user-images.githubusercontent.com/89524685/131256847-a73e7157-db6d-45e4-82d2-211dd1a15a11.png)





Question-2:
Find out the list of distinct recalling firms & their ---status that belongs to the CANADA & of Class -1


SQL Code-2:

```SELECT DISTINCT recalling_firm , status

FROM `bigquery-public-data.fda_food.food_enforcement` 

where country = "Canada" AND classification = "Class I"
```
 
![image](https://user-images.githubusercontent.com/89524685/131257232-5d59a626-e450-419e-8a27-46a10611f9d2.png)





Question-3:
Find out the total number of products that are recalled under all the 3types of class with “undeclared milk “ as the reason.


SQL Code-3:

```SELECT COUNT(classification)

FROM `bigquery-public-data.fda_food.food_enforcement` 

WHERE reason_for_recall LIKE "% undeclared milk %"
```

![image](https://user-images.githubusercontent.com/89524685/131256947-ee9ef2ef-e79c-4d70-9b95-bb8d635a7268.png)





Question-4.1:
Which product (Product_description) has been recalled maximum number of times under class-1


SQL Code-4.1:

```SELECT distinct  max(product_description) 

FROM `bigquery-public-data.fda_food.food_enforcement` 

where classification = "Class I"
```

![image](https://user-images.githubusercontent.com/89524685/131256967-69f710c4-6542-4090-a5ba-674a23b45644.png)






Question-4.2:
which firm has be recalled for maximum number of times for the product description that you get from the question 4.1


SQL Code-4.2: 

```SELECT distinct recalling_firm

FROM `bigquery-public-data.fda_food.food_enforcement` 

where product_description = "white and dark chocolate pecan turtles and tortoises"
```

![image](https://user-images.githubusercontent.com/89524685/131256989-324d6ee0-a4f2-4256-937d-5dcb7062a383.png)





Question -5:
Select the products industry name from fda_events & the classification of that products from fda_enforcement of a particular country “Israel”. 


SQL Code-5:

```SELECT  distinct products_industry_name , classification

FROM `bigquery-public-data.fda_food.food_enforcement`

left join `bigquery-public-data.fda_food.food_events`

ON `bigquery-public-data.fda_food.food_enforcement`.report_date = `bigquery-public-data.fda_food.food_events`.date_created

where country = "Israel"
```

![image](https://user-images.githubusercontent.com/89524685/131257021-56ba8991-d756-4751-b40f-6e63ffc0ea94.png)





Question-6:
Find the list of outcome, how/who it was initiated it & the products name using right join where the products brand name does not belong to “Green gaint corn, golden extra long , lupin flour”



SQL Code-6:

```SELECT  distinct  outcomes,  voluntary_mandated , products_industry_name

FROM `bigquery-public-data.fda_food.food_enforcement`

inner join `bigquery-public-data.fda_food.food_events`

ON `bigquery-public-data.fda_food.food_enforcement`.report_date = `bigquery-public-data.fda_food.food_events`.date_created

Where products_brand_name  NOT IN('Green gaint corn' ,"GOLDEN EXTRA LONG GRAIN WHITE RICE","LUPINE FLOUR") 
```

![image](https://user-images.githubusercontent.com/89524685/131257037-e06be409-691e-42bd-9363-a735d53d2990.png)





