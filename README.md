## Grab Sense

This application is implemented to monitor a variety of sensors and respond to custom rules.

***\*Scenario:\****

Supposing I have N sensors in any place, I can just define X and Y location points and sense them 24/7.

Now, my mission is to get the data (without losing it) from each sensor at variable intervals and process it.

***\*The first point:\****

Sensors can only transfer the data via the internet, and there is no need to be involved in connection challenges or how to connect with sender hardware or software.

Just get the JSON file from each sensor, including sensor_id, time_stamp, and payload_data.

***\*Big Challenges:\****

-Velocity of sending the data from sensors so fast

-Probably the connection failed after the right bulk data was sent.

-For each sensor, depending on type, have a custom rule to process.

-Just a unique URL path used to get the data from sensors.

-Manage the data from any sensors without packet loss or server crashes.
