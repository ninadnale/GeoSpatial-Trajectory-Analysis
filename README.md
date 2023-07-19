# GeoSpatial-Trajectory-Analysis

#### DATASET
The input for this project is provided in the format of a json file, named “simulated_trajectories.json”. The structure of final dataframe for the loaded trajectory dataset is as follows,
          |-- trajectory_id: long (nullable = true)
          |-- vehicle_id: long (nullable = true)
          |-- timestamp: long (nullable = true)
          |-- location: array (nullable = true)
          | |-- element: double (containsNull = true)
          |-- geometry: geometry (nullable = false)
In this dataframe, the geometry column represents Point object, since each record contains a set of latitude and longitude coordinates which are then converted to this Point geometry.

#### Phase 1
For this project, the backend application is written using Scala. This part of the application leverages spark and apache Sedona to process the input data. There are four key functions defined in this part, loadTrajectoryData for loading the input dataset into a spark dataframe and further processing to get the required view as mentioned in the first section of this report, getSpatialRange to get all the trajectories which are present inside the given envelope, getSpatioTemporalRange to get all the trajectories which are present inside the given envelope and getKNNTrajectory which calculates K nearest neighbors for the input trajectory id provided.

#### Phase 2
The frontend application is written using the Flask framework in Python. All the user interface is developed using HTML and JavaScript. The templates feature of flask came in handy for this. The index page features the main menu for this application and separate HTML pages for prompting inputs from user for each of the spatial query functions. Each of these forms has a route method mapped to it in the flask framework. The processed data is transferred to the frontend in the form of JSON data. This the necessary format for further processing and visualization by using deck.gl framework, which is final and topmost layer of this project.
