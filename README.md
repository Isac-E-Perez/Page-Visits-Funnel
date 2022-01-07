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

```R
# load data
visits <- read_csv("visits.csv")
cart <- read_csv("cart.csv")
checkout <- read_csv("checkout.csv")
purchase <- read_csv("purchase.csv")
```

Afterwards, I inspected the data frames to see what kind of data I had to analyze.

```R
# inspect data frames
head(visits)
head(cart)
head(checkout)
head(purchase)
```

***visit* Data Frame**

![Screen Shot 2021-11-02 at 5 54 01 PM](https://user-images.githubusercontent.com/89553126/139962872-8c7c78cc-101d-4eac-840b-1de407288082.png)

***cart* Data Frame**

![Screen Shot 2021-11-02 at 5 54 04 PM](https://user-images.githubusercontent.com/89553126/139962875-e4a813b6-7057-4b84-a8e0-f58f3b66b7d9.png)

***checkout* Data Frame**

![Screen Shot 2021-11-02 at 5 54 07 PM](https://user-images.githubusercontent.com/89553126/139962880-f2e8644c-a2a8-43cf-9826-7fa2eaa28e04.png)

***purchase* Data Frame**

![Screen Shot 2021-11-02 at 5 54 10 PM](https://user-images.githubusercontent.com/89553126/139962884-141731c4-b30e-4a04-b3a2-5657b3469a06.png)

All four data frames have the same *user_id* data, therefore we took advantage of this with the *left_join* function. The *left_join* is joined by *user_id*. I decided to remove the number column because it impacted the *left_join* function. The resulting would be **NA** for the *cart_time* column. In order to fix this, I removed the number column with **NULL**.  

```R
# remove the number column:
visits$...1 <- NULL
cart$...1 <- NULL
checkout$...1 <- NULL
purchase$...1 <- NULL

# define visits_cart here:
visit_cart <- visits %>%
left_join(cart)
 
# visit_cart <- left_join(visits, cart, by = c('user_id' = 'user_id'))
visit_cart
```

Producing the following results,
 
![Screen Shot 2021-11-02 at 6 04 17 PM](https://user-images.githubusercontent.com/89553126/139964093-7462734d-e21c-4c86-8bbd-f0c06251aab5.png)

I am now curious on how many users were on the site, but did not head to checkout with an item. Therefore, I defined the total visits on the site,

```R
# define total_visits here:
nrow(visits)
```

where the output was `[1] 2000`.

Afterwards, I defined the total number of vists where the users did not go to the cart with an item,

```R
# define visit_no_cart here:
visit_no_cart <- visit_cart %>% 
filter(is.na(cart_time)) 
nrow(visit_no_cart)

# The null rows means that the customer   
# visited the site but did not select a  
# product to place into the cart  
```

where the output was `[1] 1652`. 

Therefore, I learned that only 348 users out of 2000 ended up going to the checkout part of the website with an item. 

So the percentage of users that did not go to checkout was, 

```R
# calculate visit_no_cart_percent here:
visit_no_cart_percent <- visit_no_cart %>%
summarize(visit_no_cart_percent = 1652/2000)
visit_no_cart_percent
```
 
![Screen Shot 2021-11-02 at 6 20 35 PM](https://user-images.githubusercontent.com/89553126/139965157-6aea25ec-558b-482a-bc02-6868b4ca49ff.png)

Now I want to know the percentage of users that had items in the cart yet did not checkout. Therefore, I defined the *cart_checkout* variable, 

```R
# define cart_checkout here:
cart_checkout <- cart %>%
left_join(checkout)
```

Getting the following product, 

![Screen Shot 2021-11-02 at 6 23 00 PM](https://user-images.githubusercontent.com/89553126/139965616-817da85e-8fe5-412d-bfa8-578b48237c11.png)

Afterwards, I defined the *total_cart*.

```R
# define total_carts here:
cart_checkout
nrow(cart_checkout)
```

where the output was `[1] 348`.

I define the *cart_no_checkout* number here,

```R
# define cart_no_checkout here:
cart_no_checkout <- cart_checkout %>%
filter(is.na(checkout_time))
nrow(cart_no_checkout)
```

where the output was `[1] 122`.

So the percentage of users that had items in the cart but did not checkout was,

```R
# calculate cart_no_checkout_percent here:
cart_no_checkout_percent <- cart_no_checkout %>%
summarize(cart_no_checkout_percent = 122/348)
cart_no_checkout_percent
```

![Screen Shot 2021-11-04 at 7 57 15 PM](https://user-images.githubusercontent.com/89553126/140440742-02fb7909-108b-440b-a1f1-f86f5a42cad9.png)

Then I defined all the data here,

```R
# define all_data here:
all_data <- visits %>%
left_join(cart) %>%
left_join(checkout) %>%
left_join(purchase)
head(all_data, 10)
```

Resulting in, 

![Screen Shot 2021-11-04 at 8 38 26 PM](https://user-images.githubusercontent.com/89553126/140443833-a761459b-e01d-4b80-947f-667f161cc2f4.png)

![Screen Shot 2021-11-04 at 8 38 31 PM](https://user-images.githubusercontent.com/89553126/140443839-97241a0e-6c44-4f7d-b9b2-d47f74ec8821.png)

Now I want to know the percentage of users that checkout with an item but did not purchase the item. 

First, I defined the total number of checkouts,
 
```R
# define total_checkout here:
total_checkout <- nrow(all_data)
```

Afterwards, I defined the number of checkouts without purchases,
 
```R
# define checkout_no_purchase here:
checkout_no_purchase <- all_data %>%
filter(is.na(checkout_time))
total_checkout
nrow(checkout_no_purchase)
```

The results were `[1] 2000
                  [1] 1774`.

Finally, I can calculate the percentage,

```R
# calculate checkout_no_purchase_percent here:
checkout_no_purchase_percent <- checkout_no_purchase %>% 
summarize(checkout_no_purchase_percent = 1774/2000)
checkout_no_purchase_percent
```
 
![Screen Shot 2021-11-04 at 8 44 07 PM](https://user-images.githubusercontent.com/89553126/140444286-b3c947fd-f117-450d-af63-829cb395c3a6.png)

Now I want to the time to purchase by each user,

```R
# update all_data with time_to_purchase column here:
all_data <- all_data %>%
  mutate(time_to_purchase = purchase_time - visit_time)
  
# inspect the updated all_data data frame here:
head(all_data)
```

![Screen Shot 2021-11-04 at 8 46 54 PM](https://user-images.githubusercontent.com/89553126/140444527-79d40d82-faf0-413e-91ef-c7c2dac04dac.png)

Finally, I can get the average time to purchase an item by the user on the site,
 
```R
# define time_to_purchase here:
time_to_purchase <- all_data %>%
  summarize(mean_time = mean(time_to_purchase, na.rm = TRUE))
time_to_purchase
```

![Screen Shot 2021-11-04 at 8 48 10 PM](https://user-images.githubusercontent.com/89553126/140444630-7944a82c-c14a-43b8-a26e-8dce48e207b5.png)

In conclusion, I was able to analyze and extract a lot of information about how users behave, with both the interface and the items for purchase, with the data given.
