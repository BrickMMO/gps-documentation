<style>@import url("//readme.codeadam.ca/readme.css");</style>

## Pitch: App: GPS: Phase #1

Date: Feb 27th, 2023

Domain: [https://gps.brickmmo.com](https://gps.brickmmo.com) 

GitHub: [https://github.com/BrickMMO/gps-hub-v1](https://github.com/BrickMMO/gps-hub-v1)

## Application Purpose

This application will use the Pixy2 AI camera to track coordinates of seven LEGO^TM robots. 

The end result will allow for a data visualization app using the LEGO^TM map and locations of robots:

The end result will be instructions to create something similar to the [LEGO™ World Map](https://www.lego.com/en-us/product/world-map-31203):

![Sample Map](../images/v1-map.png)

### Front-End

Front end facing application will include the following features:

- A real-time map indicating the current location of each of the seven robots
- Possibly a slider to pan through recent history
- Other features determined by group

Front design may look something like this

![Front end design](../images/front-end-design-image.png)

### Back-End

Application will include a control panel to achieve the following:

- Login to control panel
- Manage the seven robots
- View position history

This application will also require a Python codeset residing on a Pixy2/EV3 to update robot positions. Updates will happen once per second. Update will use the/api/position/{id} endpoint

### API

Application API will include the following API calls:

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| GET | /api/robots | Return a list of the seven robots including ID, current position, last movement date/dime, colour, and profile data.|
| GET | /api/position/{id} | A quick call to retrieve ONLY the current coordinates of the specified robot. <br/> **Parameters**: <br/>id (required): a method of identifying a robot using colour or record ID. |
| GET | /api/history/{id}  | A detailed report of a single robot profile, location, and last 100 positions. <br/> **Parameters**: <br/>id (required): a method of identifying a robot using colour or record ID. <br> from_date and to_date (optional): if both are specified, the API will return all tracking between the two dates. |
| POST | /api/position/{id}   | A quick API endpoint that will primarily be called by the Python application to update a robot's location. <br/> **Parameters**: <br/>id (required): a method of identifying a robot using colour or record ID. |


---

<a href="https://brickmmo.com">
<img src="https://brickmmo.com/images/brickmmo-logo-horizontal.jpg" width="100">
</a>
