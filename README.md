# PIE Trajectory Planification
> I carried out a little trajectory planification project. The first aim was to find the best the trajectory of an object in a complex environment full of obstacles. I needed this part of the code for predicting the shortest path trough a track for a school project for an autonomous vehicule that we don't yet know right now what it will look like… It is also a good way of learning about modelling and finding the shortest path. Doing in C++ was also a good training to improve my skills in this language. A lot of things have been simplified for it to work, and the result could be better if some improvements were made both in terms of modelisation constraints and computational time (I'll make a list of possible improvements and points to work on below).


#### Tables of contents
* [Path tree](#path-tree)
* [Direct links to folders](#direct-links-to-folders)  
* [About the Shell Eco Marathon Challenge](#about_the_shell_eco_marathon_challenge)
* [Results preview](#app-preview)
* [Simplifications](#simplifications)
* [Possible improvements](#possible_improvements)


## Path tree
```
PIE_Trajectory_Planification/
├── First_Tests/
│   ├── Obstacles_concatenation/              
│   ├── Test_Arc/    
│   ├── Test_Djikstra/    
│   ├── Test_Graph/    
│   ├── Test_Obstacle/    
│   ├── Test_Param/    
│   └── Test_Point/
│
├── Graph_Src/
│   └── source code           
│
├── PIE_Track/
│   ├── Data/           
│   ├── Visuals/         
│   └── source code
│  
├── Test_Little_Track/
│   ├── Results/           
│   └── source code 
│
└── Test_Real_Track/
│   ├── Test_1/           
│   ├── Test_2/         
│   └── Test_less_points/    
```


## Direct links to folders  
* [First_Tests](./First_Tests/) : various test cases related to different modules
    * [Obstacles_concatenation](./First_Tests/Obstacles_concatenation/) : tests the merging of obstacles  
    * [Test_Arc](./First_Tests/Test_Arc/) : tests related to arc classes
    * [Test_Djikstra](./First_Tests/Test_Djikstra/) : tests the implementation of Dijkstra’s algorithm  
    * [Test_Graph](./First_Tests/Test_Graph/) : verifies the graph class and functionalities
    * [Test_Obstacle](./First_Tests/Test_Obstacle/) : checks how obstacle classes are handled 
    * [Test_Param](./First_Tests/Test_Param/) : parametered function related tests 
    * [Test_Point](./First_Tests/Test_Point/) : tests related to point classes  

* [Graph_Src](./Graph_Src/) : source code related to graph functionalities  

* [PIE_Track](./PIE_Track/) : finding the shortest path on the real world track and exporting results
    * [Data](./PIE_Track/Data/) : track data files used for processing  
    * [Visuals](./PIE_Track/Visuals/) : visual representations of track-related data 

* [Test_Little_Track](./Test_Little_Track/) : tests performed on a small-scale hand-made track  
    * [Results](./Test_Little_Track/Results/) : stores the results of the small track test

* [Test_Real_Track](./Test_Real_Track/) : tests conducted on some tracks, hand-made, and the real one
    * [Test_1](./Test_Real_Track/Test_1/) : first test of track modelisation using a different approach
    * [Test_2](./Test_Real_Track/Test_2/) : second test of track modelisation using a different approach
    * [Test_less_points](./Test_Real_Track/Test_less_points/) : tests conducted with a reduced number of points for the real track, doesn't have the processed output as the final code does contain


## About the Shell Eco Marathon Challenge



## Results preview




## Simplifications



## Possible improvements
