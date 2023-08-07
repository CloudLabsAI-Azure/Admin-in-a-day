# Admin in a day


## M02-HOL- Monitor


## Table of Contents


1. Exercise 1 - Admin Analytics for Power Apps

   **Scenario**
   
   - Task 1: Explore the Power Apps analytics


2. Exercise 2 – Tenant-level analytics

   **Scenario**
   
   - Task 1: Enable tenant-level analytics

  
## Exercise 1: Admin Analytics for Power Apps

### Scenario

Analytics for the environment admin is available at the Microsoft Power Platform admin center. The admin reports provide a view into environment level usage, errors, service performance to drive governance, and change management services to users. These reports are available for canvas apps only and not available for model-driven apps

### Task 1: Explore the Power Apps analytics

1. Go to the Power Platform admin center using your tenant administrator credentials (https://aka.ms/ppac).   
   
   a. Reminder: Your credentials are in the **"Environment Details"** tab.
   
      ![](../images/M01-1/image5.png)

2. To access these reports, sign in to the Power Platform admin center and select **Analytics > Power Apps**. Reports appear in a menu bar at the top of the page.

## Exercise 2: Tenant-level analytics

### Scenario

In this exercise, you will be enabling the tenant level analytics. 

### Task 1: Enable tenant-level analytics

1. Go to the Power Platform admin center using your tenant administrator credentials (https://aka.ms/ppac) if not opened already.   
   
   a. Reminder: Your credentials are in the **"Environment Details"** tab.
   
      ![](../images/M01-1/image5.png)
    
2. select **Analytics > Power Apps**

    ![](../images/M03/tenant-analytics.png)

3. Select the Overview tab and select **Enable** to redirect to the Analytics pane.

   ![](../images/M03/tenant-enable.png)

4. In the Analytics pane, grant consent for tenant-level analytics by enabling the **Tenant-level analytics** feature and select **Save**

   ![](../images/M03/tenant-save.png)


>**Note**: Once enabled, this feature aggregates data from environments across all regions in your tenant and copies it into the default environment region for tenant-level reporting. A tenant-level administrator role is required for one-time operation of granting consent for tenant-level analytics.

5. The Overview tab displays a message indicating that tenant-level analytics has been enabled. Typically, these reports are displayed within 24-48 hours of enabling the feature.

   ![](../images/M03/tenant-report.png)

 
 **Congratulations!** You have completed this portion of the workshop.


