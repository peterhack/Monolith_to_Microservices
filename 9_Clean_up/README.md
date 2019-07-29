# Clean up of Module

Follow the following steps to clean up the OpenShift project and Dynatrace.

## Step 1: Delete Services and Pods on OpenShift
```
oc delete project <project-XX>
```
    
## Step 2: Delete Management Zone and Custom Service Detection in Dynatrace
1. From the left menu, choose the **Settings** tab.
1. In the Settings page, open **Server-side service monitoring** and **Custom service detection**.
1. Identify your custom service detection rule and click on **X** under Delete.
1. In the Settings page, open **Preferences** and **Management zones**.
1. Identify your management zone and click on **X** under Delete.

---

[Previous Step: Deploy the Microservice](../6_Deploy_the_Microservice)
:arrow_backward:

:arrow_up_small: [Back to overview](../)