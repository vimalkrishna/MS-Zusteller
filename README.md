# MS-Zusteller
This is the **Web front-end** of the Microservice application that shows the location of a simulated deliverer using google MAP API.
Displays the live location by polling (PULL) the latest position(SYNCHRONOUS REST call) from a Microservices called **MS-GeoPosition-Tracker** that itself fetches 
the geolocation(GPX data) from "ApacheMQ Messaging QUEUE" through a RESTful call and is interpreted my Google MAP API.

## Technical Stack
 **Languages, frameworks library used**: Java 8, Spring Boot 1.5, Spring WebMVC, JSP, Google Maps API, Spring Cloud Eureka Client).
 **Build tools** (Maven/Gradle).

We can see the position of the vehicle changing with each refresh of the browser that we make. This makes a REST call for the location GPX data.
This is a complete Microservice Application to SEE the live position of a Deliverer(Zusteller). The live position is simulated by using GPX data of a stretch.


## Other Microservices that works together
There are 6 Microservices
1. MS-Eureka-Registry (This makes service discover automated, for communication with MS.)
2. MS-global-config (Optional! if we want to completely separate configurations.)
3. ActiveMQ Broker (Main decoupling mechanism between sender and receiver of GPX data.)
4. MS-GeoLocation (Simulates the sending of GPX data to the message queue.)
5. MS-GeoPosition-Tracker (Reads the data from Queue and exposes as REST service.)
**6. MS-Zusteller** (This service, this fetches the data and visualises through Google-MAP API.)

When all of the are running, we can see the movement appearing as live position of deliverer by refreshing (reloading) the browser. The GPX data is simulated and is not real time data.

### Useful localhost links for easy access:

```
MS-Eureka-Registry Server: http://localhost:8010/
ApacheMQ dashboard: http://localhost:8161/admin/queues.jsp  (with admin:admin as ID and Password)
Zusteller (this front end) http://localhost:8080/website/vehicles/vehicle/BMW 
```

## Consumer Contract tests
```
Try it as excercise!
```
## Deployment

Each Microservices has been deployed with Docker SWARM and Kubernetes on AWS.
Another version as instances runing on EC2

## Versioning

Version 1.0
I use [SemVer](http://semver.org/) for versioning. 


## Authors
* **vimal krishna** 

## License
This project is licensed under the MIT License.
