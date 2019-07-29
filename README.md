# Monolith to Microservices 

![ticketmonster](assets/ticketmonster.png)

In this module you'll learn how to migrate a monolithic application to the cloud and how to fearlessly break it up into microservices. Therefore, we want to walk you through the different stages of identifying and extracting a microservice, as well as strangling it around its origin – the monolith. For this purpose, the module provides step-by-step instructions and labs showing the best practices we have identified for migrating a monolith to the cloud. This module goes along with a blog post series, which you can find [here](https://www.dynatrace.com/news/blog/fearless-monolith-to-microservices-migration-a-guided-journey/). Please take a look at the different blog posts to learn more about certain migration steps.

<!-- already installed on Bastion HOST 
# Pre-Requisits

Install the following tool(s):
* [OpenShift CLI](https://docs.okd.io/latest/cli_reference/get_started_cli.html#installing-the-cli)

-->

# Prepare Environment for Labs

1. Clone the repository from [monolith to microservices](https://github.com/dynatrace-innovationlab/monolith-to-microservice-openshift)
    ```
    git clone https://github.com/dynatrace-innovationlab/monolith-to-microservice-openshift.git
    ```

1. Create the project in OpenShift
    ```
    oc login <OurClusterIP:port>
    ```
    * User: `userXX` (`XX` is your assigned number)<br>
    * Password: ask instructor 
    
1. After the successful login, create your own project:
    ```
    oc new-project <project-XX>
    ```

1. Set up a management zone for your OpenShift project
    1. Login to the Dynatrace tenant: tenant-url (Please ask instructor for Dynatrace tenant and login credentials.)
    1. Go to **Settings**, **Preferences**, and click on **Management zones**.
    1. Click **Create management zone**  and set name to `project-XX` (`XX` is your assigned number).
    1. Click **Add new rule** and set rule applies to `Process groups`. 
    1. As condition define: `Kubernetes namespace` > `begins with` > enable `Case sensitive` > name of your project `project-XX`
    1. Enable both checkboxes: **Apply to underlying hosts of matching process groups** and **Apply to all services provided by the process groups**
    1. Finally, click **Save**.

# Troubleshooting
Some useful OpenShift CLI commands:
- `oc get pods`: retrieve all pods
- `oc get services`: retrieve all services
- `oc get routes`: get all exposed routes
- `oc delete all -l app=<yourappname>`: delete an app and all assigned resources to this app
- `oc logs <pod-name>`: get the logs of a pod
- `oc rsh <pod-name>`: open a remote shell on this pod
