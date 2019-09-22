# Monolith to Microservices Workshop Prerequisites

The Monolith to Microservices workshop requires an OpenShift cluster and the use of the OC and Kubectl CLI commands to complete.  If you do not have an OpenShift cluster available to you, please follow the instructions below to build one.  

- OpenShift 3.11 cluster with Cluster Admin privileges
- Dynatrace SaaS Tenant
- 'oc' and 'kubectl' cli 
- shell in which to perform 'oc' and 'cli' commands

## Installing the OpenShift Cluster

If you do not have an OpenShift cluster already, you can create one within AWS using the following instructions.  These require that you have an AWS account with administrative privileges.  If you do not have a 'personal' AWS Account, you can create one using your personal email which will also include enough free credits to run this lab.  In addition to creating the AWS account, you will require an AWS access key to utilize the terraform scripts.


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
