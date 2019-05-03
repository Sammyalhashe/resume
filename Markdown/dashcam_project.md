# 
- Comma.ai's dashcam product has the capability to sample data every second, of which includes speed, coordinates, and distance since the trip started.
- Using 527 trips, stored as <code>JSON</code>, I created a performant webapp that simultaneously displayed all 527 and their speed distribution on an interactive map. See <a href="https://dashcamroutes.herokuapp.com/">https://dashcamroutes.herokuapp.com/</a>
- I stored the trips in a Mongo Cloud Atlas database in three collections, all dependent on the zoom of the map.
    - Python was used to seperate these trips and uploaded them to the Cloud.
    - Client side caching was implemented so that the data did not need to be downloaded multiple times.
- An <code>Angular2+</code> frontend was implemented with an <code>ExpressJS</code> backend with <code>Mongoose</code> acting as the interface between Mongo and the app.
