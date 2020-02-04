# MiniBot_Patrol

## Parameters
rest_time:到達座標點後，需要等待的秒數，在往下個目標點  
keep_patrol:是否持續巡邏，設定參數為true後，以下巡邏類型就會無效，沒有圈數和時間限制，只能設定random_patrol，是否使用隨機座標點巡邏  
random_patrol:是否啟動隨機座標點巡邏，而不是按照順序來巡邏，此參數只有在keep_patrol設定為true時才有效  
patrol_type:巡邏類型，不是不斷巡邏時才需要設定使用哪種巡邏方式，patrol_loop=與patrol_time為互斥性，設定為0，patrol_time就會無效，設定為1，patrol_loop就會無效  
* 0:巡邏圈數patrol_loop，巡邏指定圈束後停止  
* 1:巡邏時間patrol_time，巡邏指定時間後返回起始點停止  
patrol_loop:keep_patrol設定為false後，可以設定巡航圈數  
patrol_time:設定巡邏時間，當巡邏時間到達指定時間後，就返回起始點，時間單位為分鐘  

## 設定巡邏座標
Navigation設定目標後查尋目標座標  
$ rostopic echo /move_base/current_goal  
![alt text](https://github.com/wowamy/MiniBot_Patrol/blob/master/document/%E5%B7%A1%E9%82%8F%E9%BB%9E%E5%BA%A7%E6%A8%99.PNG)  
增加或減少巡邏點  
更改patrol_nav.py中navigation target pose的座標(Point、Quaternion)  
self.locations['數字']   = Pose(Point(2.808,  -0.760, 0.000), Quaternion(0.000, 0.000, -0.384, 0.923))

## Patrol

`$ roslaunch MiniBot_Patrol MiniBot_Nav_Patrol.launch`