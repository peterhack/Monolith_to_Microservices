# Generate Load on the New UI

This lab runs a load generation script for TicketMonster. The script simulates real user actions by utilizing the [PhantomJS](http://phantomjs.org/download.html) and [CasperJS](http://casperjs.org/) framework. While PhantomJS is a headless web browser scriptable with JavaScript, CasperJS allows you to build full navigation scenarios.

![scaling_up](../assets/scale_up.png)

## Requirement(s) for this Lab

Install the following tool(s):
* [Docker](https://www.docker.com/community-edition) 

## Step 1. Build Docker image

1. Switch to the `load-generation` directory.

1. Build image using Docker.
    ```
    docker build -t <your dockerhub account>/loadgeneration:latest .
    docker images
    ```

## Step 2. Run container and start script
1. Usage of load generation script:
    ```
    usage: loadgeneration.sh <target URL> <duration in minutes> <[clients/minute] | [empty = random number of clients (1..10) / minute] >
    ```

1. Start script using the container.
    ```
    docker run -d --rm <imageID> /bin/bash loadgeneration.sh <your-front-end-url> 10 15
    ```

---

[Previous Step: Extract UI From Monolith](../2_Extract_UI_From_Monolith) :arrow_backward: :arrow_forward: [Next Step: Identify a Microservice](../4_Identify_a_Microservice)

:arrow_up_small: [Back to overview](../)
