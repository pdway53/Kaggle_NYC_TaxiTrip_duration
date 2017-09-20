# Kaggle_NYC_TaxiTrip_duration
https://www.kaggle.com/c/nyc-taxi-trip-duration  
  
In this competition, Kaggle is challenging us to build a model that predicts the total ride duration of taxi trips in New York City. I entered the competition 2 weeks before deadline and got the performance with LB 0.38709   
    
  
    
In this work, what I did is :  
  
  
***Feature Processing***      
  
1.EDA ploration  
2.加入Network feature,利用Networkx建立network, 找出不同地區(cluster)間的shortest weight path來幫助預估trip duration  
3.結合天氣與過去OSRM data(https://www.kaggle.com/oscarleo/new-york-city-taxi-with-osrm) between pickup and dropoff to help us  
  estimate.  
4.Group each trip to find the average speed, 試著去找出不同trip間的關聯  
5.去除outliers  
  
  
***Model***    
  
Choose to use xgboost and uterlize gridsearch and crossvalidation to choose the best parameter.  
  

![Alt text](https://github.com/pdway53/Kaggle_NYC_TaxiTrip_duration/blob/master/photo/photo.png);



**Important feature**
   
|  | Feature | 特徵意義 |
| ------| ------ | ------ |
| 1 | np_trip_duration_gby_pickup_dt_bin | pickup coordinates 平均 trip duration |
| 2 | total_distance | pickup coordinates and dropoff coordinates 距離|
| 3 | distance_haversine | pickup coordinates and dropoff coordinates haversine 距離 |
| 4 | speed_bt_cluster | 每個cluster平均速度 |
| 5 | direction | 每個trip的方向 |
| 6 | pickup_dt | pickuptime normailization |
| 7 | dist_x | latitude distance  |
| 8 | dropoff_pca1 | dropoff coordinates latitude pca transform |
| 9 | network_pred | network shortest weighted path 預測 |
| 10 |pickup_pca0  | pickup coordinates longitude pca transform |


