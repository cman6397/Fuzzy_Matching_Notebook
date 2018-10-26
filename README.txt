
This is a Notebook with many tools for using Fuzzy logic to match collections of strings.  I created this notebook to aid in
hand matching different products to each other using product descriptions and attributes.  Unfortunately this situation occurs frequently at work due to outdated item ids, non unique UPCs, and inconsistent data from venders.  Using fuzzy logic to quickly narrow down match pools and find potential matches saves a ton of time.  

Approach:  The approach of this fuzzy logic algorithm is as follows:
  1) Define attributes that can be compared between items (In my case beverage size, description, type (Wine or Spirit), and brand are useful for comparison.  
  2) Build multiple metrics to assess similarity between attributes (Edit distances, character ratios, and other metrics are used) 
  3) Train a classification algorithm with respect to a Loss function on training data to find the best weights across the metrics for quantifying similariy.  (Linear Regression, Support Vector Machines, Logistic Regression, and Neural Networks were tried.  Triplet Loss, Log loss, squared error, and more were tried as loss functions)
  
Result:
The accuracy of the fuzzy matching is variable based on the size of the validation set and the number of real matches in the set, and how noisy the data is.  On sets of 300 training samples using wine/liquor data from different vendors the Support Vector Machine was able to correctly match 72% of records.  On one to many sets where matching is guaranteed the algorithm achieved a match accuracy of 92% on the wine/liquor data I used (~1000 rows in the One Set and 100,000 rows in the many set).  Fuzzy Matching has saved me a lot and made it somewhat barable to hand match products in very large datasets. I created an excel version in VBA with the best metrics and meta algorithm from this jupyter notebook that other people at my work place use for their own fuzzy matching problems.  
