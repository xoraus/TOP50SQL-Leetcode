# TOP50SQL-Leetcode


## Select 

###  Recyclable and Low Fat Products 

Leetcode 1757 - Write a solution to find the ids of products that are both low fat and recyclable. Return the result table in any order.

```sql
SELECT product_id
FROM Products
WHERE low_fats = 'Y' AND recyclable = 'Y' 
```
###  Find Customer Referee 

Leetcode 584 - Find the names of the customer that are not referred by the customer with id = 2. Return the result table in any order.

```sql
SELECT name 
FROM Customer 
WHERE referee_id <> 2 OR referee_id IS NULL 
```

###  Big Countries 

Leetcode 595 - A country is big if: it has an area of at least three million (i.e., 3000000 km2), or it has a population of at least twenty-five million (i.e., 25000000). Write a solution to find the name, population, and area of the big countries. Return the result table in any order.

```sql
SELECT name, population, area 
FROM World 
WHERE area >= 3000000 OR population >= 25000000 
```

###  Article Views I 

Leetcode 1148 - Write a solution to find all the authors that viewed at least one of their own articles. Return the result table sorted by id in ascending order.

```sql
# Approach 1

SELECT DISTINCT v1.author_id AS id
FROM Views v1
INNER JOIN Views v2 ON v1.author_id = v2.viewer_id
WHERE v1.author_id = v1.viewer_id
ORDER BY id;

# Approach 2

SELECT DISTINCT author_id AS id
FROM Views
WHERE author_id = viewer_id
ORDER BY id  
```

###  Invalid Tweets 

Leetcode 1148 - Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15. Return the result table in any order.

```sql
SELECT tweet_id
FROM Tweets
WHERE LENGTH(content) > 15 
```

## Basic Joins 

###  Replace Employee ID With The Unique Identifier 
###  Product Sales Analysis I 
###  Customer Who Visited but Did Not Make Any Transactions 
###  Rising Temperature 
###  Average Time of Process per Machine 
###  Employee Bonus 
###  Students and Examinations 🔸 
###  Managers with at Least 5 Direct Reports 
###  Confirmation : Rate 

## Basic Aggregate Functions 

###  Not Boring Movies 
###  Average Selling Price 
###  Project Employees I 
###  Percentage of Users Attended a Contest 
###  Queries Quality and Percentage 
###  Monthly Transactions I 
###  Immediate Food Delivery Il 
###  Game Play Analysis IV 

## Sorting and Grouping 

###  Number of Unique Subjects Taught by Each Teacher 
###  User Activity for the Past 30 Days I 
###  Product Sales Analysis III 
###  Classes More Than 5 Students  
###  Find Followers Count 
###  Biggest Single Number 
###  Customers Who Bought All Products 

## Advanced Select and Joins 

###  The Number of Employees Which Report to Each Employee 
###  Primary Department for Each Employee 
###  Triangle Judgement 
###  Consecutive Numbers 
###  Product Price at a Given Date 
###  Last Person to Fit in the Bus 
###  Count Salary Categories 

## Subqueries 

###  Employees Whose Manager Left the Company  
###  Exchange Seats 
###  Movie Rating
###  Restaurant Growth 
###  Friend Requests II: Who Has the Most Friends 
###  Investments in 2016 
###  Department Top Three Salaries 

## Advanced String Functions / Regex/Clause 

###  Fix Names in a Table 
###  Patients With a Condition 
###  Delete Duplicate Emails 
###  Second Highest Salary 
###  Group Sold Products By The Date 
###  List the Products Ordered in a Period 
###  Find Users With Valid E-Mails 
