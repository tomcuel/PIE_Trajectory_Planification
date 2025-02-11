# PIE Trajectory Planification
> I carried out a little trajectory planification project. The first aim was to find the best the trajectory of an object in a complex environment full of obstacles. I needed this part of the code for predicting the shortest path trough a track for a school project for an autonomous vehicule that we don't yet know right now what it will look like… It is also a good way of learning about modelling and finding the shortest path. Doing in C++ was also a good training to improve my skills in this language. A lot of things have been simplified for it to work, and the result could be better if some improvements were made both in terms of modelisation constraints and computational time (I'll make a list of possible improvements and points to work on below).


#### Tables of contents
* [Path tree](#path-tree)
* [Direct links to folders](#direct-links-to-folders)  
* [About the Shell Eco Marathon Challenge](#about-the-shell-eco-marathon-challenge)
* [Results preview](#app-preview)
* [Simplifications](#simplifications)
* [Possible improvements](#possible-improvements)


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
    ├── Test_1/           
    ├── Test_2/         
    └── Test_less_points/    
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
The **Shell Eco-marathon** is a global competition that challenges students to design, build, and drive the most energy-efficient vehicles. The event brings together teams from around the world to push the boundaries of fuel efficiency and sustainable mobility.  

#### Objectives  
- **Energy Efficiency:** Develop a vehicle that consumes the least amount of fuel or energy over a set distance.  
- **Innovation & Engineering:** Apply advanced engineering principles to optimize aerodynamics, materials, and powertrain efficiency.  
- **Real-World Impact:** Encourage sustainable transportation solutions by fostering research in energy-efficient technologies.  

#### Competition Categories  
The challenge is divided into different categories based on the type of vehicle and energy source:  
1. **Prototype:** Ultra-lightweight, futuristic vehicles focused solely on efficiency.  
2. **Urban Concept:** More practical, city-oriented vehicles that resemble real-world cars.  
3. **Autonomous Urban Concept:** subcategory of Urban Concept, where autonomous vehicles must complete a course without driver intervention, showcasing autonomous driving technologies and energy optimization, reflecting current industry trends *(the category we are competing in, though not yet advanced enough to qualify for the real-world event)*.

**Energy Sources:** Vehicles can be powered by gasoline, battery-electric systems, hydrogen fuel cells, or alternative fuels.  

#### More Information
For detailed information about the competition, we encourage you to visit the official [Shell Eco-marathon website](https://www.shellecomarathon.com). This site provides comprehensive insights into the event's history, categories, and global participation.

Additionally, you can explore the official [track data page](https://telemetry.sem-app.com/wiki/doku.php/telemetry_data/tracks), which includes direct access to telemetry and detailed data for the various tracks around the world. This resource can help you better understand the specific conditions and challenges of each location, to start working on it.


## Results preview
The real track look like this on Google Maps.

<img src="./PIE_Track/Visuals/Real_Track_Maps.png" alt="login_screen_render" width="400" height="200"/>

After dowloading the csv data of the track on the website, I then centered everything around the middle of the track in meters, that is representated in this picture.

<img src="./PIE_Track/Visuals/track_data_utm.png" alt="login_screen_render" width="400" height="200"/>

Then, I created the graph corresponding to the track and I found out the optimal path through the track, that I modelize with many simplifications that are both related to our problem *(10m wide track, supposed 2m max vehicle, only obstacle = track layout)* and my code restriction *(not all arcs are considered since there are too many of them, for time computation purpose, and they only are segments for example)*.

<img src="./PIE_Track/Visuals/track_visual_result.png" alt="login_screen_render" width="400" height="200"/>

I finally exported the data to convert it back to GPS coordinates so it can be read like that, but I could be inverted back to centered data, depending on the future needs on the project.

<img src="./PIE_Track/Visuals/track_visual_lat_long.png" alt="login_screen_render" width="400" height="200"/>

At the end of the day, instead of covering 1,319 meters per lap, we only need to complete 1,272 meters. This 47-meter reduction could be a game-changer in a challenge where maximizing the number of laps with the same energy input is crucial.


## Simplifications
* Only 1/3 of the points were considered when modelizing the graph, but that's not that much of deal since there are more than a thousand points all very close to each others. Having 1 point out of 3 doesn't change how the track look like at the end 
* I supposed that the track is 10m wide at any point, even it could be less, but since I took margins, there will not be any problem of the vehicle going off
* There is no padding involved, since we already took that into account when modelizing the track borders
* There is no need to consider if the trajectory does make some sharps since, the number and proximity of the points and the shortest path is already penalizing them
* The arcs are only segments since the point are really close, one to another, there is no need to consider parametric arcs, since the complexity of them will make everything to difficult to modelize for me right now
* The obstacles are only the track layout, so there is no probleme with obstacles intersection 
* To separate the start and the finish point, we just add an obstacle between the two points that we connect to the track layout the right way

## Possible improvements
About the code restriction : 



What can be added : 