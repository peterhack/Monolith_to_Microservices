# Lift-and-Shift TicketMonster to a Cloud Platform

In this lab you'll learn how to move a monolithic application to a cloud platform, OpenShift in this case. The applied moving approach follows a lift-and-shift concept. This means that the application is not prepared as a cloud-native application. However, the database for the application will be a service that runs on OpenShift. 

![lift-and-shift](../assets/lift_and_shift.png)

## Step 1: Create Database for Monolith

1. Deploy a MySQL database service.
    ```
    oc new-app --name=ticketmonster-db -e MYSQL_USER=ticket -e MYSQL_PASSWORD=monster -e MYSQL_DATABASE=ticketmonster mysql:5.5
    ```

1. Get the IP of the service.
    ```
    oc get svc
    ```

## Step 2: Deploy TicketMonster

1. Create a new application.
    ```
    oc new-app -e MYSQL_SERVICE_HOST=ticketmonster-db -e MYSQL_SERVICE_PORT=3306 --docker-image=dynatraceacm/ticketmonster-monolith:latest
    ```

1. Expose the TicketMonster service.
    ```
    oc expose service ticketmonster-monolith --name=monolith 
    ```

## Step 3: Test your TicketMonster

1. Get the public endpoint of your ticketmonster application.
    ```
    oc get routes
    ```

1. Open the route using a browser and navigate through the application.

![ticketmonster](../assets/ticketmonster.png)

---

:arrow_forward: [Next Step: Extract UI From Monolith](../2_Extract_UI_From_Monolith)

:arrow_up_small: [Back to overview](../)
