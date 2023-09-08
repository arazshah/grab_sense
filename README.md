# grab Sense

This application is implemented to monitor a variety of sensors and respond to custom rules depending on sensor type.

**Scenario:**

Supposing I have N sensors in any place, I can just define X and Y location points and the name of the sensor. Now, My mission is to get the data (without losing it) from any sensor at variable intervals and process it using custom commands for each sensor type. (sense 24/7)

You can use this application in three steps:

1. Connect to the API and define your sensor.
2. Make your commands to process the received sensor data. (make consumer)
   1. Just publish the sensors' data via API.
3. see your results

**The first point:**

Sensors can only transfer the data via the internet, and there is no need to be involved in connection challenges or how to connect with sender hardware or software.

Just get the messages from each sensor, including sensor_id, time_stamp, and payload_data.

**Big Challenges:**

-Velocity of sending the data from sensors so fast

-Probably the connection failed after the right bulk data was sent.

-Each sensor, depending on the type, has a custom rule to process.

-Just a unique URL path used to get the data from sensors.

-Manage the data from any sensors without packet loss or server crashes.

**Models:**

1. sensor_id->UUID
2. sensor_name
3 .sensor_location_point(GIS) [GIS field](https://docs.djangoproject.com/en/4.2/ref/contrib/gis/model-api/)
4. Sensor_type
5. payload_data (some keys:value)[JSON field](https://docs.djangoproject.com/en/4.2/ref/models/fields/#jsonfield)
6. Thresholds_data(related payload_data)

**Feature:**

1. ability to involve other sensors' data(stream)
2. ability to create a function
3. ability to publish the result to another device via JSON
4. ability to store all of the sense data(time series)
5. Manage to get data with time intervals and detect modifications.
6. ....

**Picture of project:**

1. The user accesses the URL to register a sensor
2. Get the UUID for each sensor registered
   1. UUID is important for sending the data from a sensor
   2. Sensors data must send include(Sensor_id,time_stamp,payload_data)
3. The user can make custom rules for each sensor or complex
4. The user can obvious the results
   1. decide to send another device
   2. for making visualizing
   3. save in time series data storage

**Workflow:**

1. Authentication and Authorization of the users
2. Make a facility for the user to CRUD sensor's information
   1. GET /sensors/ - Retrieves a list of sensors
   2. GET /sensors?sid= -Retrieve a specific sensor
   3. POST /sensors - Creates a new sensor
   4. PUT /sensors/{sid} - Update a specific sensor
   5. DELETE /sensors/{sid} - Delete a specific sensor
3. Declare a unique URL used to send the sensor data
   1. POST /S/grabber/{sid}/ - Send the data from specific sensor detect with sid
4. Run Message Broker ability to handle high volumes of data, facilitate real-time communication

![schema](https://raw.githubusercontent.com/arazshah/grab_sense/master/static/img/Grabber.png "schema")

**Schema:**

1. IoT Node
2. Gateway
3. Integrator platform
4. Visualization
5. Prototyping
6. storage

