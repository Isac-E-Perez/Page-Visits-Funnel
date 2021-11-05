# Page Visits Funnel Project
### About: 

For this project, I implemented data analysis using R. I used the libraries readr, and dplyr which helped me to build the project. I analyze the data of CoolTShirts.com to gain a better understanding and insight on visits to their website. In order to do this I built a funnel, which is a description of how many people continue to the next step of a multi-step process. 

In this case, the funnel describes the following process:
1. A user visits CoolTShirts.com
2. A user adds a t-shirt to their cart
3. A user clicks "checkout"
4. A user purchases a t-shirt
 
### Note:

This data comes from CoolTShirts.com
 
### Results:

The goal of this project is to learn user interaction with items on the website.

I first loaded the data files onto RStudio.

![Screen Shot 2021-11-02 at 5 53 37 PM](https://user-images.githubusercontent.com/89553126/139962861-7b67bf4f-b2ea-46a7-9b9a-8df5f027220d.png)

Afterwards, I inspected the data frames to see what kind of data I had to analyze.

![Screen Shot 2021-11-02 at 5 53 47 PM](https://user-images.githubusercontent.com/89553126/139962867-3a025ef0-9b93-4443-ad36-0fb9b2cce8a6.png)

***visit* Data Frame**

![Screen Shot 2021-11-02 at 5 54 01 PM](https://user-images.githubusercontent.com/89553126/139962872-8c7c78cc-101d-4eac-840b-1de407288082.png)

***cart* Data Frame**

![Screen Shot 2021-11-02 at 5 54 04 PM](https://user-images.githubusercontent.com/89553126/139962875-e4a813b6-7057-4b84-a8e0-f58f3b66b7d9.png)

***checkout* Data Frame**

![Screen Shot 2021-11-02 at 5 54 07 PM](https://user-images.githubusercontent.com/89553126/139962880-f2e8644c-a2a8-43cf-9826-7fa2eaa28e04.png)

***purchase* Data Frame**

![Screen Shot 2021-11-02 at 5 54 10 PM](https://user-images.githubusercontent.com/89553126/139962884-141731c4-b30e-4a04-b3a2-5657b3469a06.png)

All four data frames have the same *user_id* data, therefore we took advantage of this with the *left_join* function. The *left_join* is joined by *user_id*. I decided to remove the number column because it impacted the *left_join* function. The resulting would be **NA** for the *cart_time* column. In order to fix this, I removed the number column with **NULL**.  

![Screen Shot 2021-11-02 at 6 03 58 PM](https://user-images.githubusercontent.com/89553126/139964031-8042a343-ddfc-4886-8eff-8e1249da4e2e.png)

Producing the following results,
 
![Screen Shot 2021-11-02 at 6 04 17 PM](https://user-images.githubusercontent.com/89553126/139964093-7462734d-e21c-4c86-8bbd-f0c06251aab5.png)

I am now curious on how many users were on the site, but did not head to checkout with an item. Therefore, I defined the total visits on the site,

![Screen Shot 2021-11-02 at 6 13 22 PM](https://user-images.githubusercontent.com/89553126/139964767-b8cf46ec-d5b5-48ea-b288-e398ad0ad09d.png)

where the output was ![Screen Shot 2021-11-02 at 6 13 30 PM](https://user-images.githubusercontent.com/89553126/139964826-c46aa9bf-8f41-4e0b-96cf-b5f9544744ed.png).

Afterwards, I defined the total number of vists where the users did not go to the cart with an item,

![Screen Shot 2021-11-02 at 6 13 51 PM](https://user-images.githubusercontent.com/89553126/139964940-43552c85-b7d2-46ed-bbfe-7ed5293bb263.png)

where the output was ![Screen Shot 2021-11-02 at 6 13 58 PM](https://user-images.githubusercontent.com/89553126/139964955-f10b8244-ef54-4378-adad-62f49956ade4.png). 

Therefore, I learned that only 348 users out of 2000 ended up going to the checkout part of the website with an item. 

So the percentage of users that did not go to checkout was, 

![Screen Shot 2021-11-02 at 6 20 27 PM](https://user-images.githubusercontent.com/89553126/139965149-7393d1de-0c21-4fb0-a97e-c37921662929.png)
 
![Screen Shot 2021-11-02 at 6 20 35 PM](https://user-images.githubusercontent.com/89553126/139965157-6aea25ec-558b-482a-bc02-6868b4ca49ff.png)

Now I want to know the percentage of users that had items in the cart yet did not checkout. Therefore, I defined the *cart_checkout* variable, 

![Screen Shot 2021-11-02 at 6 22 02 PM](https://user-images.githubusercontent.com/89553126/139965613-1c5e6624-b903-4ba5-8840-be6740d30624.png)

Getting the following product, 

![Screen Shot 2021-11-02 at 6 23 00 PM](https://user-images.githubusercontent.com/89553126/139965616-817da85e-8fe5-412d-bfa8-578b48237c11.png)

Afterwards, I defined the *total_cart*.

![Screen Shot 2021-11-04 at 7 46 56 PM](https://user-images.githubusercontent.com/89553126/140440030-606d8656-32ca-483f-84a0-ecb2f5cdbabf.png)

where the output was ![Screen Shot 2021-11-04 at 7 47 11 PM](https://user-images.githubusercontent.com/89553126/140440038-72d2ce09-972e-474b-8284-ba2aa6c7f787.png).

I define the *cart_no_checkout* number here,

![Screen Shot 2021-11-04 at 7 56 37 PM](https://user-images.githubusercontent.com/89553126/140440695-8370f8a0-7732-486f-83b3-3f16e19170c5.png)

![Screen Shot 2021-11-04 at 7 56 52 PM](https://user-images.githubusercontent.com/89553126/140440714-f3360391-551e-4710-836f-f5a0215c6d5d.png)

So the percentage of users that had items in the cart but did not checkout was,

![Screen Shot 2021-11-04 at 7 57 01 PM](https://user-images.githubusercontent.com/89553126/140440729-c9ec97c7-be3a-41cb-a6c5-86be9e317778.png)

![Screen Shot 2021-11-04 at 7 57 15 PM](https://user-images.githubusercontent.com/89553126/140440742-02fb7909-108b-440b-a1f1-f86f5a42cad9.png)

Then I defined all the data here,

![Screen Shot 2021-11-04 at 8 38 11 PM](https://user-images.githubusercontent.com/89553126/140443810-c6dc6485-d648-4498-9b79-e8def20ce2e8.png)

Resulting in, 

![Screen Shot 2021-11-04 at 8 38 26 PM](https://user-images.githubusercontent.com/89553126/140443833-a761459b-e01d-4b80-947f-667f161cc2f4.png)

![Screen Shot 2021-11-04 at 8 38 31 PM](https://user-images.githubusercontent.com/89553126/140443839-97241a0e-6c44-4f7d-b9b2-d47f74ec8821.png)

Now I want to know the percentage of users that checkout with an item but did not purchase the item. 

First, I defined the total number of checkouts,
 
![Screen Shot 2021-11-04 at 8 40 19 PM](https://user-images.githubusercontent.com/89553126/140444095-088bc25a-bf6b-47ec-aa01-57ca39ef3176.png)

Afterwards, I defined the number of checkouts without purchases,
 
![Screen Shot 2021-11-04 at 8 40 31 PM](https://user-images.githubusercontent.com/89553126/140444145-9aa35ff2-b34f-4ce5-9f93-08caef593c33.png)

The results were ![Screen Shot 2021-11-04 at 8 40 43 PM](https://user-images.githubusercontent.com/89553126/140444170-10247033-769a-4e24-a40e-d8a9ab3306f1.png).

Finally, I can calculate the percentage,

![Screen Shot 2021-11-04 at 8 43 52 PM](https://user-images.githubusercontent.com/89553126/140444322-a4de6db3-56c2-438f-bf62-f42c026be94b.png)
 
![Screen Shot 2021-11-04 at 8 44 07 PM](https://user-images.githubusercontent.com/89553126/140444286-b3c947fd-f117-450d-af63-829cb395c3a6.png)

Now I want to the time to purchase by each user,
![Screen Shot 2021-11-04 at 8 46 31 PM](https://user-images.githubusercontent.com/89553126/140444517-e685d5c2-5542-47ad-8a33-fa7e96865b12.png)

![Screen Shot 2021-11-04 at 8 46 40 PM](https://user-images.githubusercontent.com/89553126/140444522-87468ef3-806a-498a-ae1f-d16e375397b2.png)

![Screen Shot 2021-11-04 at 8 46 54 PM](https://user-images.githubusercontent.com/89553126/140444527-79d40d82-faf0-413e-91ef-c7c2dac04dac.png)

Finally, I can get the average time to purchase an item by the user on the site,
 
![Screen Shot 2021-11-04 at 8 47 58 PM](https://user-images.githubusercontent.com/89553126/140444625-b54adaed-ecea-436b-8a12-ffb34dd31542.png)

![Screen Shot 2021-11-04 at 8 48 10 PM](https://user-images.githubusercontent.com/89553126/140444630-7944a82c-c14a-43b8-a26e-8dce48e207b5.png)

In conclusion, I has able to analyze and extract a lot of information about how users behave, with both the interface and the items for purchase, with the data given.
