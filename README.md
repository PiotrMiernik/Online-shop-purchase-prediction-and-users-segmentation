Data: The data comes from Kaggle (https://www.kaggle.com/datasets/benpowis/customer-propensity-to-purchase-data). This dataset represents a day's worth of visits to a fictional website. Each row represents a unique customer, identified by their unique UserID. The columns represent features of the user's visit and actions the user took on the website that day. These features are:

UserID - A unique identifier for the visitor

basket_icon_click - Did the visitor click on the shopping basket icon?

basket_add_list - Did the visitor add a product to their shopping cart on the 'list' page?

basket_add_detail - Did the customer add a product to their shopping basket from the product detail page?

sort_by - Did the visitor sort products on a page?

image_picker - Did the visitor use the image picker?

account_page_click - Did the visitor visit their account page?

promo_banner_click - Did the visitor click on a promo banner?

detail_wishlist_add - Did the visitor add a product to their wishlist from the 'detail' page?

list_size_dropdown - Did the visitor interact with a product dropdown?

closed_minibasket_click - Did the visitor close their mini shopping basket?

checked_delivery_detail - Did the visitor view the delivery FAQ area on a product page?

checked_returns_detail - Did the visitor check the returns FAQ area on a product page?

sign_in - Did the customer sign in to the website?

saw_checkout - Did the visitor view the checkout?

saw_sizecharts - Did the visitor view a product size chart?

saw_delivery - Did the visitor view the delivery FAQ page?

saw_account_upgrade - Did the visitor view the account upgrade page?

saw_homepage - Did the customer visit the website's homepage?

device_mobile - Was the visitor on a mobile device?

device_computer - Was the visitor on a desktop device?

device_tablet - Was the visitor on a tablet device?

returning_user - Is this visitor new, or returning?

loc_uk - Was the visitor located in the UK, based on their IP address?

ordered - In this dataset, we also have a feature showing whether the customer placed an order - this is the target variable.

The data on Kaggle was divided into training and testing samples, but in the test set, there were no '1' in the 'ordered' feature (no one placed an order), so the testing sample was dropped, and the training set was divided into training/test sets. The training sample contains 455,401 unique values (users).

Project Objectives: The main objective of the project was to create a predictive model that estimates the probability of a customer making a purchase based on their behavior on the website. Based on this, marketing campaigns can be created targeting potential customers who did not make a purchase but have a high probability of doing so (rather than targeting all users who did not make a purchase). An additional objective of the project was to attempt to segment (cluster) users who visited the website separately for customers (those who made purchases) and non-customers (those who did not make purchases). Segmenting customers and non-customers separately makes sense because the two groups may have different behavior patterns, and separate segmentation of these two groups will help understand the differences in their behavior. For example, people who made a purchase might be more engaged in certain activities on the site (e.g., viewing product details, searching, etc.). Additionally, segmenting these groups separately allows for the creation of dedicated marketing strategies:
- For buyers: Maintaining loyalty, cross-selling (what to do to make them buy more frequently).
- For non-buyers: Optimizing conversions by better understanding their purchasing barriers.

Due to the fact that all variables in the dataset are binary, Multiple Correspondence Analysis (MCA) and the k-means algorithm were used for segmentation:
- MCA is an equivalent of PCA for categorical/binary variables. It reduces the dimensionality of the data, making segmentation easier.
- The result of MCA can then be used as input data for the k-means algorithm or other clustering methods.

Files in the repository:
Data:
-  training_sample.csv - The original dataset that was split into training and test data (for the predictive model).
-  buyers_with_clusters.csv and non_buyers_with_clusters.csv - These files contain cluster numbers and the values of the individual MCA components.
-  data_with_prob.csv - This file contains an additional variable with the probability values of making a purchase for each website user.

- EDA and data preprocessing.ipynb - This notebook contains the results of the exploratory data analysis and data preparation for modeling.
- Web users segmentation.ipynb - This notebook contains an attempt to segment customers and non-customers using the k-means method, preceded by Multiple Correspondence Analysis (MCA) to reduce dimensionality and facilitate interpretation of the segmentation.
- Propensity to purchase prediction.ipynb - This notebook contains the code for creating the predictive model (estimating the probability of making a purchase).
