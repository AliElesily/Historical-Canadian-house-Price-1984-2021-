# Housing-price
Read csv file which has dataset 
#### df = pd.read_csv("House price.csv")

Split arrays or matrices into random train and test subsets "dftrain , dftest = train_test_split(df , test_size  = .1 ,random_state = 42)"
which is train data is represent 90% from data and test data  represent 10% from data 

function preprocessing to make train data suits to train
When we have a feature where variables are just Type and there is  order  convet it to nominal encoding according to  sorting 

#### "replace_dict = {"Composite_Benchmark" : 1 , "Single_Family_Benchmark": 2 ,
 ####              "One_Storey_Benchmark" : 3 , "Two_Storey_Benchmark" : 4}"
                
                
When we have a feature where variables are just names and there is no order or rank to this variable's feature convert it using One Hot Encoding
#### "ohe = OneHotEncoder()
#### ohe_data = ohe.fit_transform(train_data[["Geo"]])"

add new column "year" , "month" extracting from "Data" column
#### "train_data["year"] = [i.split("-")[0] for i in train_data["Date"]]
####  train_data["month"] = [i.split("-")[1] for i in train_data["Date"]]"
 
 
drop unnecessary column such as "Date" , "Geo"
#### "train_data.drop(columns =["Date","Geo"] ,inplace =  True)"
 
finally in machine learning we nead X which represent Features and y represent Target "Price"
#### "Xtrain = train_data.drop(columns = "Price")
#### ytrain = train_data["Price"]"
  
and rescale y to make model more accurate
#### "ytrain = np.log10(ytrain)"


  
  
and do same preprocessing on test data
#### "def testing_preprocessing(test_data , ohe)"


next step creat model  , I choose SVM (support vector machine) as machine learning model
#### "SVR(kernel= "rbf" , C = 200 ,gamma = .01)"


train model on train Xtrain (feature) , ytrain (target)
#### "svmrg.fit(Xtrain , ytrain)"


get prediction of Xtest and compare it with ytest and get accuray of model
#### "ypred = svmrg.predict(Xtest)
####  print("r2 score" , svmrg.score(Xtest,ytest))"
 
 
