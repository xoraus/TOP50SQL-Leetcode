<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

# [TOP50SQL-Leetcode](#top50sql-leetcode)


![SQL Batch](https://assets.leetcode.com/static_assets/others/Top_SQL_50.gif)


   * [Select ](#select)
      + [Recyclable and Low Fat Products ](#recyclable-and-low-fat-products)
      + [Find Customer Referee ](#find-customer-referee)
      + [Big Countries ](#big-countries)
      + [Article Views I ](#article-views-i)
      + [Invalid Tweets ](#invalid-tweets)
   * [Basic Joins ](#basic-joins)
      + [Replace Employee ID With The Unique Identifier ](#replace-employee-id-with-the-unique-identifier)
      + [Product Sales Analysis I ](#product-sales-analysis-i)
      + [Customer Who Visited but Did Not Make Any Transactions ](#customer-who-visited-but-did-not-make-any-transactions)
      + [Rising Temperature ](#rising-temperature)
      + [Average Time of Process per Machine ](#average-time-of-process-per-machine)
      + [Employee Bonus ](#employee-bonus)
      + [Students and Examinations](#students-and-examinations)
      + [Managers with at Least 5 Direct Reports ](#managers-with-at-least-5-direct-reports)
      + [Confirmation : Rate ](#confirmation-rate)
   * [Basic Aggregate Functions ](#basic-aggregate-functions)
      + [Not Boring Movies ](#not-boring-movies)
      + [Average Selling Price ](#average-selling-price)
      + [Project Employees I ](#project-employees-i)
      + [Percentage of Users Attended a Contest ](#percentage-of-users-attended-a-contest)
      + [Queries Quality and Percentage ](#queries-quality-and-percentage)
      + [Monthly Transactions I ](#monthly-transactions-i)
      + [Immediate Food Delivery Il ](#immediate-food-delivery-il)
      + [Game Play Analysis IV ](#game-play-analysis-iv)
   * [Sorting and Grouping ](#sorting-and-grouping)
      + [Number of Unique Subjects Taught by Each Teacher ](#number-of-unique-subjects-taught-by-each-teacher)
      + [User Activity for the Past 30 Days I ](#user-activity-for-the-past-30-days-i)
      + [Product Sales Analysis III ](#product-sales-analysis-iii)
      + [Classes More Than 5 Students  ](#classes-more-than-5-students)
      + [Find Followers Count ](#find-followers-count)
      + [Biggest Single Number ](#biggest-single-number)
      + [Customers Who Bought All Products ](#customers-who-bought-all-products)
   * [Advanced Select and Joins ](#advanced-select-and-joins)
      + [The Number of Employees Which Report to Each Employee ](#the-number-of-employees-which-report-to-each-employee)
      + [Primary Department for Each Employee ](#primary-department-for-each-employee)
      + [Triangle Judgement ](#triangle-judgement)
      + [Consecutive Numbers ](#consecutive-numbers)
      + [Product Price at a Given Date ](#product-price-at-a-given-date)
      + [Last Person to Fit in the Bus ](#last-person-to-fit-in-the-bus)
      + [Count Salary Categories ](#count-salary-categories)
   * [Subqueries ](#subqueries)
      + [Employees Whose Manager Left the Company  ](#employees-whose-manager-left-the-company)
      + [Exchange Seats ](#exchange-seats)
      + [Movie Rating](#movie-rating)
      + [Restaurant Growth ](#restaurant-growth)
      + [Friend Requests II: Who Has the Most Friends ](#friend-requests-ii-who-has-the-most-friends)
      + [Investments in 2016 ](#investments-in-2016)
      + [Department Top Three Salaries ](#department-top-three-salaries)
   * [Advanced String Functions / Regex/Clause ](#advanced-string-functions-regexclause)
      + [Fix Names in a Table ](#fix-names-in-a-table)
      + [Patients With a Condition ](#patients-with-a-condition)
      + [Delete Duplicate Emails ](#delete-duplicate-emails)
      + [Second Highest Salary ](#second-highest-salary)
      + [Group Sold Products By The Date ](#group-sold-products-by-the-date)
      + [List the Products Ordered in a Period ](#list-the-products-ordered-in-a-period)
      + [Find Users With Valid E-Mails ](#find-users-with-valid-e-mails)

<!-- TOC end -->

<!-- TOC --><a name="select"></a>
## Select 

<!-- TOC --><a name="recyclable-and-low-fat-products"></a>
###  Recyclable and Low Fat Products 

Leetcode 1757 - Write a solution to find the ids of products that are both low fat and recyclable. Return the result table in any order.

```sql
SELECT product_id
FROM Products
WHERE low_fats = 'Y' AND recyclable = 'Y' 
```
<!-- TOC --><a name="find-customer-referee"></a>
###  Find Customer Referee 

Leetcode 584 - Find the names of the customer that are not referred by the customer with id = 2. Return the result table in any order.

```sql
SELECT name 
FROM Customer 
WHERE referee_id <> 2 OR referee_id IS NULL 
```

<!-- TOC --><a name="big-countries"></a>
###  Big Countries 

Leetcode 595 - A country is big if: it has an area of at least three million (i.e., 3000000 km2), or it has a population of at least twenty-five million (i.e., 25000000). Write a solution to find the name, population, and area of the big countries. Return the result table in any order.

```sql
SELECT name, population, area 
FROM World 
WHERE area >= 3000000 OR population >= 25000000 
```

<!-- TOC --><a name="article-views-i"></a>
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

<!-- TOC --><a name="invalid-tweets"></a>
###  Invalid Tweets 

Leetcode 1148 - Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15. Return the result table in any order.

```sql
SELECT tweet_id
FROM Tweets
WHERE LENGTH(content) > 15 
```

<!-- TOC --><a name="basic-joins"></a>
## Basic Joins 

<!-- TOC --><a name="replace-employee-id-with-the-unique-identifier"></a>
###  Replace Employee ID With The Unique Identifier 
Leetcode 1378 : Solution - Write a solution to show the unique ID of each user, If a user does not have a unique ID replace just show null. Return the result table in any order. 

```sql
SELECT EU.unique_id, E.name
FROM Employees E
LEFT JOIN EmployeeUNI EU ON E.id = EU.id 
```

<!-- TOC --><a name="product-sales-analysis-i"></a>
###  Product Sales Analysis I 
Leetcode 1068 : Solution - Write a solution to report the product_name, year, and price for each sale_id in the Sales table. Return the resulting table in any order.

```sql
SELECT P.product_name, S.year, S.price
FROM Sales AS S
JOIN Product AS P ON S.product_id = P.product_id;  
```

<!-- TOC --><a name="customer-who-visited-but-did-not-make-any-transactions"></a>
###  Customer Who Visited but Did Not Make Any Transactions 

Leetcode 1581 : Solution - Write a solution to find the IDs of the users who visited without making any transactions and the number of times they made these types of visits. Return the result table sorted in any order.

```sql
SELECT v.customer_id, COUNT(v.visit_id) as count_no_trans
FROM Visits v
LEFT JOIN Transactions t ON v.visit_id = t.visit_id
WHERE t.transaction_id is NULL
GROUP BY (v.customer_id) 
```

<!-- TOC --><a name="rising-temperature"></a>
###  Rising Temperature 

Leetcode 197 : Solution - Write a solution to find all dates' Id with higher temperatures compared to its previous dates (yesterday). Return the result table in any order.

```sql
SELECT weather.id AS 'Id'
FROM weather
JOIN weather w ON DATEDIFF(weather.recordDate, w.recordDate) = 1
        AND weather.Temperature > w.Temperature;
 ```

<!-- TOC --><a name="average-time-of-process-per-machine"></a>
###  Average Time of Process per Machine 

Leetcode 1661 : Solution - There is a factory website that has several machines each running the same number of processes. Write a solution to find the average time each machine takes to complete a process. The time to complete a process is the 'end' timestamp minus the 'start' timestamp. The average time is calculated by the total time to complete every process on the machine divided by the number of processes that were run. The resulting table should have the machine_id along with the average time as processing_time, which should be rounded to 3 decimal places. Return the result table in any order.

```sql
SELECT machine_id, ROUND(AVG(end_time - start_time), 3) AS processing_time
FROM (
    SELECT machine_id, process_id, 
           MAX(CASE WHEN activity_type = 'start' THEN timestamp END) AS start_time,
           MAX(CASE WHEN activity_type = 'end' THEN timestamp END) AS end_time
    FROM Activity
    GROUP BY machine_id, process_id
) AS ProcessTimes
GROUP BY machine_id; 
```
<!-- TOC --><a name="employee-bonus"></a>
###  Employee Bonus 

Leetcode 577 : Solution - Write a solution to report the name and bonus amount of each employee with a bonus less than 1000. Return the result table in any order.

```sql
SELECT E.name, B.bonus
FROM Employee E
LEFT JOIN Bonus B ON E.empId = B.empId
WHERE B.bonus < 1000 or B.bonus IS NULL
 ```

<!-- TOC --><a name="students-and-examinations"></a>
###  Students and Examinations 

Leetcode 1280 : Solution - Write a solution to find the number of times each student attended each exam. Return the result table ordered by student_id and subject_name.

```sql
# Approach 1

SELECT s.student_id, s.student_name, sub.subject_name, COALESCE(e.attended_exams, 0) AS attended_exams
FROM Students s
CROSS JOIN Subjects sub
LEFT JOIN (
    SELECT student_id, subject_name, COUNT(*) AS attended_exams
    FROM Examinations
    GROUP BY student_id, subject_name
) e USING (student_id, subject_name)
ORDER BY s.student_id, sub.subject_name;  
```

<!-- TOC --><a name="managers-with-at-least-5-direct-reports"></a>
###  Managers with at Least 5 Direct Reports

Leetcode 570 : Solution - Write a solution to find managers with at least five direct reports. Return the result table in any order.

```sql
SELECT name
FROM Employee 
WHERE id IN
    (SELECT managerId
    FROM Employee E
    GROUP BY (managerId)
    HAVING COUNT(id) >=5 ) 
```
<!-- TOC --><a name="confirmation-rate"></a>
###  Confirmation : Rate 

Leetcode 1934 : Solution - The confirmation rate of a user is the number of 'confirmed' messages divided by the total number of requested confirmation messages. The confirmation rate of a user that did not request any confirmation messages is 0. Round the confirmation rate to two decimal places. Write a solution to find the confirmation rate of each user. Return the result table in any order.

```sql
SELECT s.user_id,
       CASE
           WHEN c.time_stamp IS NULL THEN 0.00
           ELSE ROUND(SUM(CASE WHEN c.action = 'confirmed' THEN 1 ELSE 0 END) / COUNT(*), 2)
       END AS confirmation_rate
FROM Signups s
LEFT JOIN Confirmations c ON s.user_id = c.user_id
GROUP BY s.user_id;
``` 

<!-- TOC --><a name="basic-aggregate-functions"></a>
## Basic Aggregate Functions 

<!-- TOC --><a name="not-boring-movies"></a>
###  Not Boring Movies 
<!-- TOC --><a name="average-selling-price"></a>
###  Average Selling Price 
<!-- TOC --><a name="project-employees-i"></a>
###  Project Employees I 
<!-- TOC --><a name="percentage-of-users-attended-a-contest"></a>
###  Percentage of Users Attended a Contest 
<!-- TOC --><a name="queries-quality-and-percentage"></a>
###  Queries Quality and Percentage 
<!-- TOC --><a name="monthly-transactions-i"></a>
###  Monthly Transactions I 
<!-- TOC --><a name="immediate-food-delivery-il"></a>
###  Immediate Food Delivery Il 
<!-- TOC --><a name="game-play-analysis-iv"></a>
###  Game Play Analysis IV 

<!-- TOC --><a name="sorting-and-grouping"></a>
## Sorting and Grouping 

<!-- TOC --><a name="number-of-unique-subjects-taught-by-each-teacher"></a>
###  Number of Unique Subjects Taught by Each Teacher 
<!-- TOC --><a name="user-activity-for-the-past-30-days-i"></a>
###  User Activity for the Past 30 Days I 
<!-- TOC --><a name="product-sales-analysis-iii"></a>
###  Product Sales Analysis III 
<!-- TOC --><a name="classes-more-than-5-students"></a>
###  Classes More Than 5 Students  
<!-- TOC --><a name="find-followers-count"></a>
###  Find Followers Count 
<!-- TOC --><a name="biggest-single-number"></a>
###  Biggest Single Number 
<!-- TOC --><a name="customers-who-bought-all-products"></a>
###  Customers Who Bought All Products 

<!-- TOC --><a name="advanced-select-and-joins"></a>
## Advanced Select and Joins 

<!-- TOC --><a name="the-number-of-employees-which-report-to-each-employee"></a>
###  The Number of Employees Which Report to Each Employee 
<!-- TOC --><a name="primary-department-for-each-employee"></a>
###  Primary Department for Each Employee 
<!-- TOC --><a name="triangle-judgement"></a>
###  Triangle Judgement 
<!-- TOC --><a name="consecutive-numbers"></a>
###  Consecutive Numbers 
<!-- TOC --><a name="product-price-at-a-given-date"></a>
###  Product Price at a Given Date 
<!-- TOC --><a name="last-person-to-fit-in-the-bus"></a>
###  Last Person to Fit in the Bus 
<!-- TOC --><a name="count-salary-categories"></a>
###  Count Salary Categories 

<!-- TOC --><a name="subqueries"></a>
## Subqueries 

<!-- TOC --><a name="employees-whose-manager-left-the-company"></a>
###  Employees Whose Manager Left the Company  
<!-- TOC --><a name="exchange-seats"></a>
###  Exchange Seats 
<!-- TOC --><a name="movie-rating"></a>
###  Movie Rating
<!-- TOC --><a name="restaurant-growth"></a>
###  Restaurant Growth 
<!-- TOC --><a name="friend-requests-ii-who-has-the-most-friends"></a>
###  Friend Requests II: Who Has the Most Friends 
<!-- TOC --><a name="investments-in-2016"></a>
###  Investments in 2016 
<!-- TOC --><a name="department-top-three-salaries"></a>
###  Department Top Three Salaries 

<!-- TOC --><a name="advanced-string-functions-regexclause"></a>
## Advanced String Functions / Regex/Clause 

<!-- TOC --><a name="fix-names-in-a-table"></a>
###  Fix Names in a Table 
<!-- TOC --><a name="patients-with-a-condition"></a>
###  Patients With a Condition 
<!-- TOC --><a name="delete-duplicate-emails"></a>
###  Delete Duplicate Emails 
<!-- TOC --><a name="second-highest-salary"></a>
###  Second Highest Salary 
<!-- TOC --><a name="group-sold-products-by-the-date"></a>
###  Group Sold Products By The Date 
<!-- TOC --><a name="list-the-products-ordered-in-a-period"></a>
###  List the Products Ordered in a Period 
<!-- TOC --><a name="find-users-with-valid-e-mails"></a>
###  Find Users With Valid E-Mails 
