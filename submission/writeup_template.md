## Project: Building an Estimator


## [Rubric](https://review.udacity.com/#!/rubrics/1807/view) Points
### Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

---
### Writeup / README

#### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one. You can submit your writeup as markdown or pdf.  

You're reading it! Below I describe how I addressed each rubric point and where in my code each point is handled.

### Implement Estimator

#### 1. Determine the standard deviation of the measurement noise of both GPS X data and Accelerometer X data.
1) I extracted the values from config/log/Graph1.txt (GPS X data) and config/log/Graph2.txt (Accelerometer X data)
2) Stored in MS Excel and used stdev formula ,to find the standard devidation of the given samples

<!-- These scripts contain a basic planning implementation that includes...

And here's a lovely image of my results (ok this image has nothing to do with it, but it's a nice example of how to include images in your writeup!)
![Top Down View](./misc/high_up.png)

Here's | A | Snappy | Table
--- | --- | --- | ---
1 | `highlight` | **bold** | 7.41
2 | a | b | c
3 | *italic* | text | 403
4 | 2 | 3 | abcd
 -->
#### 2. Implement a better rate gyro attitude integration scheme in the UpdateFromIMU() function.
![Rate Gyro Integration](./images/2.png)

#### 3. Implement all of the elements of the prediction step for the estimator.
1)The prediction step includes the state update element (PredictState() function), a correct calculation of the Rgb prime matrix, and a proper update of the state covariance. 
2)The acceleration is accounted for as a command in the calculation of gPrime. 
3)The covariance update follows the classic EKF update equation.
#### 4. Implement the magnetometer update.
![magUpdate](./images/4.png)

#### 5. Implement the GPS update.
![GPSUpdate](./images/5.png)

#### 2. Implement a better rate gyro attitude integration scheme in the UpdateFromIMU() function.

#### 2. Implement a better rate gyro attitude integration scheme in the UpdateFromIMU() function.

#### 2. Implement a better rate gyro attitude integration scheme in the UpdateFromIMU() function.

#### 2. Implement a better rate gyro attitude integration scheme in the UpdateFromIMU() function.

### Implementing Your Path Planning Algorithm

#### 1. Set your global home position
<!-- Here students should read the first line of the csv file, extract lat0 and lon0 as floating point values and use the self.set_home_position() method to set global home. Explain briefly how you accomplished this in your code. -->

This was accomlished in the following lines of code.
The line was read from the csv file. Then the float values were extracted and converted into float values.
![Set Global Home Positon](./misc/lat_and_lon.png)

#### 2. Set your current local position
<!-- Here as long as you successfully determine your local position relative to global home you'll be all set. Explain briefly how you accomplished this in your code. -->

After the Global home position is set according to the csv file data. 
Current global positon is converted into local position using global_to_local() function.
![current local position](./misc/current_position.png)

#### 3. Set grid start position from local position
<!-- This is another step in adding flexibility to the start location. As long as it works you're good to go! -->

The respective offset is added to current position and it is set as grid_start
![grid_Start](./misc/grid_Start.png)

#### 4. Set grid goal position from geodetic coords
<!-- This step is to add flexibility to the desired goal location. Should be able to choose any (lat, lon) within the map and have it rendered to a goal location on the grid. -->

Similar method as setting grid_start has been used here to set grid_goal.

![geodetic coords](./misc/geodetic_coords.png)


#### 5. Modify A* to include diagonal motion (or replace A* altogether)
<!-- Minimal requirement here is to modify the code in planning_utils() to update the A* implementation to include diagonal motions on the grid that have a cost of sqrt(2), but more creative solutions are welcome. Explain the code you used to accomplish this step. -->

![A*](./misc/diagnol.png)

Diagnol movements has been added with the existing North South East and West Convention.

For Example :

North has movement (-1,0) 

West  has movement (0,-1)

They have been added to form NorthWest (-1,-1) and an approximate cost of Square Root of 2 has been set up.

#### 6. Cull waypoints 
<!-- For this step you can use a collinearity test or ray tracing method like Bresenham. The idea is simply to prune your path of unnecessary waypoints. Explain the code you used to accomplish this step. -->
I have used the Collinearity test to prune the paths . I have use the same structure and logic as given in Excercise.

3 consecutive points are checked . if Det of them is less than epsilon value( Threshold ) , the second point is removed and third point beomes second point and the test continues till the end of the path in a similar way.

### Execute the flight
#### 1. Does it work?
It works!

### Double check that you've met specifications for each of the [rubric](https://review.udacity.com/#!/rubrics/1534/view) points.
  
# Extra Challenges: Real World Planning

For an extra challenge, consider implementing some of the techniques described in the "Real World Planning" lesson. You could try implementing a vehicle model to take dynamic constraints into account, or implement a replanning method to invoke if you get off course or encounter unexpected obstacles.

I have not worked on the Extra Challenge as of now.