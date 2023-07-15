# GoLang / Express-NodeJS application - Intersections API:
NOTE: Sorry for the inconvinience , i was not able  to attach the source code file in the google form.

 This is a mapping based API and so requires integration of turfjs:
 
 https://turfjs.org/docs/ (For node)
 https://pkg.go.dev/github.com/tomchavakis/turf-go#section-readme (For go)



* It is a POST request, protected with a header based auth check
* The API takes a really long linestring with (5k points) in GeoJSON in the body.
* There are a set of 50 randomly spread lines (just start and end) on the plane.
* The API find which of the 50 lines with ids (L01 - L50) intersect with the linestring

# The API returns:

  ** No intersections as an empty array [] OR
  ** Array of intersecting line ids along with the point of intersection. OR
  ** An error message (5XX code) if the supplied linestring is invalid OR
  ** An error message (4XX code) if the supplied req body or auth header are missing/malformed.


  To run the above app, you need to install required packages:

  To install the packages , run the following command:

  ```npm install express @turf/turf body-parser```

 # Run the Application:

Run the application using the following command:

```node app.js```

use the follwing command to test the API using curl:

```curl -X POST -H "Authorization: test123" -H "Content-Type: application/json" -d '{"linestring": {"type": "LineString", "coordinates": [[0, 0], [1, 1], [2, 2], [3, 3], [4, 4]]}}' http://localhost:3000/find-intersections```

