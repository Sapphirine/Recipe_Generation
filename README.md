# Recipe Generation Based on Ingredient Network

This is our final project for course EECS E6893 Big Data Analytics at Columbia University.

## Project Overview
Recipe recording and sharing has been around for many years. Recipe collections containing ingredient combinations yield information about cooking fundamentals and user preferences. We construct an ingredient network to study the importance of each ingredient, capture the relationships between ingredients and explore reasonable combinations. We also perform experiments, to predict ratings of newly generated recipes using features derived from the network and accordingly suggest the recipes to the user. 

## Data Collection

Our dataset was scaped from Allrecipes.com (http://allrecipes.com/recipes/?grouping=all). Each row contains the following features:
  1. id: ID of the recipe (type: string)
  2. title: title of the recipe (type: string)
  3. made_it_count: the number of users who have tried the recipe (type: int)
  4. time: the total time needed for the recipe (including preparing and cooking) (type: int)
  5. ingredients: a list of ingredients needed for the recipe (type: list)

To be able to use the scraper, you need to download the following tools:
  1. MongoDB
  2. Chromedriver (if you are using Chrome):
  https://chromedriver.storage.googleapis.com/index.html?path=2.25/
  3. Install the following python libraries:
  selenium, pymongo, numpy, pandas

## Dataset
Recipes.csv 

## Network Data
Nodes.csv, Edges.csv, features.csv, SVDfactor.npy 

## Model
SGBT (Stochastic Gradient Boosted Tree)

## Package Description
We provided python implementation for our recipe generator. To be able to run the package, one needs to first download the pre-stored file containing nodes (Nodes.csv) and edges (Edges.csv) from the Data directory, pre-trained boosted tree model (SGBT directory), and network features (features.csv, SVDfactor.npy), also from the Data directory. Users can then run the python script generator.py to see the results. (All the scripts can be found in in the Code directory)

### generator.py : 
Recipe Generator
+ To speed up, users need to have an initial run of the program to generate clique.json file. For the future runs, users can ingore this step and simply load the clique file.
+ After the generator is initiated, users will first be asked to input one or two ingredients they would like to try (separated by comma and no space allowed after the comma). If they are not satisfied with the suggested recipe, a new recipe will be generated until the generator produces one that the users like. If the user input consists of unusual ingredient combinations that are considered unachievable as stated in section 4.4 (2), users will be asked to input another set of ingredients. 

### scraping.py :
Webscraping from allrecipes.com

### processing.py :
Text Processing with Spark and nltk (natural language processing toolkit)

### network.py :
Network Construction

### community.R :
Network Centrality and Community Detection

### lsa.py :
Network Feature Extraction with Latent Semantic Analysis

### sgbt.ipynb :
Rating Prediction with Stochastic Gradient Boosted Trees

To set up pyspark in ipynb :
+ Follow:  http://ramhiser.com/2015/02/01/configuring-ipython-notebook-support-for-pyspark/
+ Use 
`PYSPARK_DRIVER_PYTHON=ipython PYSPARK_DRIVER_PYTHON_OPTS='notebook' $SPARK_HOME/bin/pyspark`
will launch pyspark within ipython notebook.
