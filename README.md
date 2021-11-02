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

Now I want to define the *cart_checkout* variable, 
![Screen Shot 2021-11-02 at 6 22 02 PM](https://user-images.githubusercontent.com/89553126/139965613-1c5e6624-b903-4ba5-8840-be6740d30624.png)

Getting the following product, 

![Screen Shot 2021-11-02 at 6 23 00 PM](https://user-images.githubusercontent.com/89553126/139965616-817da85e-8fe5-412d-bfa8-578b48237c11.png)

 
