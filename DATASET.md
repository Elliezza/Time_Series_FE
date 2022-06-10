# Data Set Description

This dataset is from JD, one of China's biggest e-commerce companies, with billions of customers and humongous amount of real commercial data. This dataset is provided as part of a competition where the contestants are required to build a machine learning model to predict the purchase intention of customers. The dataset is extracted from real customers from the JD mall, including product and user action log information. The intention is to predict customer's intention to purchase certain products, to match customers with products they desire.

* Data includes daily users from 2016-02-01 to 2016-04-15 (group U), behaviour, comments and user action information towards products in group S, and potential product information in group P.
* Acronyms definition:
	* S: all products;
	* P: potential products, P is a subset of S;
	* U: all users;
	* A: users action towards products in S;
	* C: comment information of products in S.
 
* Data Tables: 

 1. User Data

| <div style="width:400px">Name</div> | <div style="width:400px">Meaning</div> | <div style="width:800px">Notes</div> |
|-------------|-----------------------|-----------------------------------------|
| user_id     | user ID               | Encoded                                 |
| age         | age group             | -1 for unknown                          |
| sex         | gender                | 0 for male, 1 for female, 2 for others  |
| user_lv_cd  | user level            | higher level bigger number              |
| user_reg_tm | user registration date | in days                                 |

2. Product Data

| <div style="width:400px">Name</div> | <div style="width:400px">Meaning</div> | <div style="width:800px">Notes</div> |
|-------------|-----------------------|-----------------------------------------|
| sku_id      | product ID            | Encoded                                 |
| a1          | property 1            | -1 for unknown                          |
| a2          | property 2            | -1 for unknown                          |
| a3          | property 3            | -1 for unknown                          |
| cate        | category ID           | Encoded                                 |
| brand       | brand ID              | Encoded                                 |

3. Comments Data

| Name        | Meaning               | Notes                                   |
|-------------|-----------------------|-----------------------------------------|
| dt         | time until             | in days                                 |
| sku_id      | product ID            | Encoded                                 |
| comment_num | total number of comments  | 0 for no comments; 1 for 1 comment; <br> 2 for 2-10 comments; 3 for 11-50 comments; <br> 4 for above 50 comments.                        |
| has_bad_comment  | if product has bad comments | 0 for no; 1 for yes.         |
| bad_comment_rate | rate of bad comments        | ratio of bad comments in all comments|

4. Action Data

| Name        | Meaning               | Notes                                   |
|-------------|-----------------------|-----------------------------------------|
| user_id     | user ID               | Encoded                                 |
| sku_id      | product ID            | Encoded                                 |
| time        | time of action    |
| type        | type of action        | 1: browse; 2: put to cart; <br>3: remove from cart; 4: place order; <br>5: follow; 6: click |
| cate        | category ID           | Encoded                                 |
| brand       | brand ID              | Encoded                                 |

For more information, visit https://jdata.jd.com/html/detail.html?id=1.
