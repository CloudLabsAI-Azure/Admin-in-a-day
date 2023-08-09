# Admin in a day


## M02-HOL- Empower


## Table of Contents


1. Exercise 1 - Create an internal Microsoft Power Platform hub

   **About**
   
   - Task 1: Get started with the Power Platform communication site template


## Exercise 1: Create an internal Microsoft Power Platform hub

### About

At the heart of growth is a community, a place for people to collaborate, share ideas, and discover new ways to apply technology to achieve more. A community is a safe place to ask 
questions to share tacit knowledge and expand skill sets. Organizations that have succeeded at creating a growing community of makers provide tools such as Yammer or Microsoft Teams 
groups, regular events and speaking opportunities, and foster an environment of ongoing learning.They make sure that every person in the organization can come together at regular 
intervals to socialize, share their knowledge, and explore new possibilities. Leaders who want to create a digital culture will put a framework in place for the community inside their 
organization to break down geographic and organizational silos.


### Task 1: Get started with the Power Platform communication site template


1. Open the **VSCode** by clicking on the icon in desktop shortcut.

    ![](../images/M04-1/vscode.png)

2. Once the VSCode is opened, select **File** and click on **Open Folder**.

    ![](../images/M04-1/folder.png)

4. Now, navigate to this path `C:\LabFiles\PowerPlatformHub` and select the folder to open it in vscode.

    ![](../images/M04-1/pphub.png)

5. Open the **Deploy-PowerPlatformHub.ps1** file from left navigation and make the below changes and save the file.

     a. Rename the **adminTenantName** with **otuwacne<inject key="Deployment ID" enableCopy="false"/>**

    b. Rename the **companyName** with **otuwacne<inject key="Deployment ID" enableCopy="false"/>**

    c. Rename the **ownerEmail** with **<inject key="AzureAdUserEmail"></inject>**

7. Once You have updated the file, image should look like below.

    ![](../images/M04-1/deploy-pphub.png)

8. Open the **Set-PowerPlatformHubAsDLPErrorSettings.ps1** file from left navigation and make the below changes and save the file.

     a. Rename the **newSiteURL** with **https://otuwacne<inject key="Deployment ID" enableCopy="false"/>.sharepoint.com/sites/powerplatformhub/SitePages/Data-Loss-Prevention-(DLP)-Policies.aspx**

     b. Rename the **supportEmail** with **otuwacne<inject key="Deployment ID" enableCopy="false"/>**

     c. Rename the **tenantId** with ****

10.  Once You have updated the file, image should look like below.

     ![](../images/M04-1/deploy-pphub.png)

11. Now, clcik on Terminal and select **New Terminal**
 
    ![](../images/M04-1/terminal.png)

12. In the terminal window run the command **.\Deploy-PowerPlatformHub.ps1** and once the template deployment is finished you will get a **Success** message and **site url**.

     ![](../images/M04-1/pphub-site.png)

13. Navigate to the site url by selecting it and click on open to visit the site.

     ![](../images/M04-1/pphub-site1.png)



**Info:** For more details on Power Platform Hub click on the link https://learn.microsoft.com/en-us/power-platform/guidance/adoption/wiki-community



**Congratulations!** You have completed this portion of the workshop.


    
