# Admin in a day

## M01-HOL-Securing your tenant

## Table of Contents

**Lab theory** 

**Lab test environment**

1. Exercise 1 - Baseline data policy for the entire tenant

   **Scenario**
   
   - Task 1: Create the "Baseline data policy" 

   - Task 2: Test the new "Baseline data policy" when building a canvas app 

2. Exercise 2 – Reinforcing the default environment

   **Scenario**
   
   - Task 1: Create the "Default data policy"

   - Task 2: Test the new "Default data policy" when building a canvas app 

3. Exercise 3 – Empowering your pro developers

   **Scenario**
   
   - Task 1: Create the "Pro dev data policy"
   
   - Task 2: Test the new "Pro dev data policy" when building a cloud flow 

   - Bonus task: Enable the HTTP connector with endpoint filtering (public preview) 




## Lab theory


Power Platform has a large ecosystem of [Connectors](https://docs.microsoft.com/en-us/connectors/connectors) that enable your Makers to connect their applications, automations, websites, and chatbots to more than 800 data sources, services, and devices - either on-premises or in the cloud. Your Makers will use these connectors day-to-day to build what they need to solve their business problems. At times, it can be easy for your Makers to overlook important considerations such as the security of your organization's data.

Thankfully, Power Platform's [data Policies](https://docs.microsoft.com/en-us/power-platform/admin/wp-data-loss-prevention) allow you as administrators to control what connectors are available to your Makers and how they can us act as guardrails to help prevent Makers from unintentionally exposing your important business data. These data policies are configured in the Power Platform admin center and are a fundamental tool of the administrator's toolbox. Tenant administrators can create data policies which protect the entire tenant whereas environment administrators can create data policies strictly for the environments they administer. In both cases, Makers working in the target environment(s) will have to respect the rules put forth in your data policies. In today's workshop, you will play the role of a tenant administrator for a new customer seeking to establish their first data loss prevention strategy.


![](images/M01-1/image1.png)


## Lab test environment

Please use the unique tenant and the user credentials provided to complete the following 3 exercises.


 •  Registration URL: https://bit.ly/3TVhk9u 

 •  Activation code: ACTIVATE25983           


## Exercise 1: Baseline data policy for the entire tenant

### Scenario

Your first objective as a tenant administrator is to establish a first layer of governance for your entire organization. To do so, you will create a data policy that applies to all environments (both existing and future environments). This data policy will require your Makers to build their canvas apps and cloud flows exclusively with connectors that are published by Microsoft (there are more than 250 of them), not from external 3rd parties. Connectors that are created by external 3rd parties are incredibly valuable, but you will want to review them beforehand because they have not been built by Microsoft. Keep in mind that the process of creating a new connector is a rigorous and safe one regardless of its origin.

Environments and data policies before exercise #1:

  ![](images/M01-1/image3.png)

Environments and data policies after exercise #1:

  ![](images/M01-1/image4.png)


### Task 1: Create the "Baseline data policy"

 1.   Go to the Power Platform admin center using your tenant administrator credentials (https://aka.ms/ppac).   
    
        
        a. Reminder: Your credentials are in the **"Environment Details"** tab.

      
        ![](images/M01-1/image5.png)
    

2. Enter the **"Data policies"** page under the "Policies" section of the admin center's left nav.
   
3. Click **"New Policy"** in the top command bar to create your first data policy.
    
  
     ![](images/M01-1/imag6.png)
  

4. In the **"Policy name"** section of the wizard, name your data policy as follows: **"Baseline data policy"**.
  
     
     ![](images/M01-1/image7.png)
  


5. In the **"Prebuilt connectors"** section of the wizard, block all connectors that are not published by Microsoft.  

     a. Click the **"Publisher"** column.      

     b.Under **"Filter by column value"**, click **"Non Microsoft"**.                  

     c. Click **"Apply"**.             

     d. Select all connectors that are displayed.          

     e. Click **"Block"** in the top command bar.                 

      ![](images/M01-1/image8.png)
      
      ![](images/M01-1/image9.png)
      
      ![](images/M01-1/image10.png)
        
        
6. Important: Find the **"MSN weather"** and the **"HTTP"** connector in **"Non-business"** and block them too.


     ![](images/M01-1/image11.png)        

     ![](images/M01-1/image12.png)
 
     ![](images/M01-1/image13.png)        
 
     ![](images/M01-1/image14.png)
 
  
  **Additional information:** If a connector is placed in blocked, your Maker will not be able to save a canvas app or cloud flow if it uses this blocked connector.The                               meaning of the "business" and "non-business" categories will be covered in the second exercise of the data policy workshop.



7. In the "Set default group" in the top command bar, you will block all new connectors.   
    
      a. All new connectors added in the future -- whether published by Microsoft or not - will be blocked.
                                                                                                  
   ![](images/M01-1/image15.png)
       
   ![](images/M01-1/image16.png)



**Pro tip:** Before blocking all new connectors, make sure you have established a process to regularly review new connectors that have been recently introduced to                  the Power Platform. You might find something that could be incredibly valuable to your organization. All connectors are listed in this 
             [public documentation](https://docs.microsoft.com/en-us/connectors/connector-reference/connector-reference-powerapps-connectors). 


8. In the **"custom connectors"** section of the wizard, block the first and only **"custom connector pattern"**.

   a. Click **"Edit"**.
 
   b. Change the default data group from **"Ignore"** to **"Blocked (default)"**.

  ![](images/M01-1/image17.png)       ![](images/M01-1/image18.png)
       
  

**Information bubble:** Your Makers can create their own [custom connectors](https://docs.microsoft.com/en-us/connectors/custom-connectors/) to connect their apps and                         flows with a world of services, like a custom API built by a service oock this by default as a precautionary measure. Soon enough, you will                             want to enable it in specific environments because it is an effective building tool.



9. Move to the **"Scope"** section where you configure which environments will be protected by this data policy.
  
    c. "Add all environments" is pre-selected by default.

  ![](images/M01-1/image19.png)       


10. Move to the **"Review"** section of the wizard to confirm you have made the right changes (picture above).

    d. Policy name: **"Baseline data policy"**                         

    e. Prebuilt connectors: **"(0) Business, 220 (Non-business), (601) Blocked"**                                               

    f. Custom connector patterns: **"1 pattern(s) added"**             

    g. Scope: **"Add all environments"**                               

    
    ![](images/M01-1/image20.png)


11. Click **"Create policy"** and you will see your first data policy displayed in the **"Data policies"** page.

      ![](images/M01-1/image21.png) 


### Task 2: Test the new "Baseline data policy" when building a canvas app


1. Go to the Power Apps Maker portal at https://make.powerapps.com.   
    
2. Make sure you are working in the default environment. It has the **"(default)"** suffix appended.                                                                                        
      
      a. Your default environment is named differently from the one depicted in the screenshots.

      ![](images/M01-1/image22.png)
    
3.	Click on the **“Apps”** section of the left nav.

4.	Create a new blank canvas app named **“DLP – Exercise 1 – Task 2”** with a **“Tablet”** format.

      ![](images/M01-1/image23.png)
      
5.	Click the **“Data”** section and **“Add data”**. 

     ![](images/M01-1/image24.png)
     
6.	In the search bar, write **“MSN weather”**. This is currently blocked by your data policy (picture above).

7.	Select **“MSN weather”** and click **“Connect”**. You will see an error message.
   
     ![](images/M01-1/image25.png)       
     
8.	Remove the MSN weather data connection. Click **“File”** and save the app to the cloud. It will be reused later.

     ![](images/M01-1/image26.png)

9.	**Get creative!** Try different combinations of connectors and test the outcomes.



## Exercise  #2: Reinforcing the default environment

### Scenario

Now that you have established a baseline for the entire organization, it is time to focus on the [default environment](https://docs.microsoft.com/en-us/power-platform/admin/environments-overview#the-default-environment). Every organization is equipped with a single default environment from the very beginning. It is the place where your Makers can play around and get excited about low code. For example, if your Makers build automations directly from the SharePoint product, the resulting cloud flows will be in the default environment. 

   ![](images/M01-1/image27.png)
   
Everybody in your organization has access to this default environment which means it has unique needs when it comes to the security and governance of your data. In this second exercise, you will create another data policy that is exclusively applied to the default environment. This data policy will be slightly stricter meaning your Makers in the default environment will be more limited in their app and flow building experiences.  More specifically, you will leverage data policy’s [basic connector classification](https://docs.microsoft.com/en-us/power-platform/admin/dlp-connector-classification), “Business” and “Non-business”, to define a mutual exclusion group (i.e., connectors located in one category cannot be used with connectors in another category).

Environments and data policies before exercise #2:

![](images/M01-1/image28.png)

Environments and data policies after exercise #2:

![](images/M01-1/image29.png)


### Task #1: Create the “Default data policy”

1.	Go to the Power Platform admin center using your tenant administrator credentials (https://aka.ms/ppac).

    a.	Reminder: Your credentials are in the **“Environment Details”** tab.
    
    ![](images/M01-1/image30.png)
    
2.	Enter the **“Data policies”** page under the **“Policies”** section of the admin center’s left nav.
    
    a.	You will notice the 1 data policy named **“Baseline data policy”** that you have created beforehand.
    
    ![](images/M01-1/image31.png)
    
3.	Click **“New Policy”** in the top command bar to create your second data policy.

4.	In the **“Policy name”** section of the wizard, name your data policy as follows: **“Default data policy”**.
    
     ![](images/M01-1/image32.png)
     
5.	In the **“Prebuilt connectors”** section of the wizard, place Microsoft’s 1st party connectors in **“Business”**.
    a.	From the **“Non-business (849) | Default”** category, click the **“Blockable”** column.
    
    b.	Under **“Filter by column value”**, click **“No”**.
   
    c.	Click **“Apply”**. 
    
    ![](images/M01-1/image33.png)
    
    d.	Select all connectors that are displayed.
    
    e.	Click **“Move to Business”** in the top command bar.

    ![](images/M01-1/image34.png)
    
    ![](images/M01-1/image35.png)
    
  
**Information bubble:** “Business” and “Non-business” are mutually exclusive groups. Your Makers cannot build canvas apps or cloud flows that combine connectors from                            both categories. If your Maker adds a connector from “Business” to its canvas app, then the Maker cannot add a connector from the “Non-                                Business” group, and vice-versa. To summarize, the terms “Business” and “Non-business” have no inherent meaning beyond the mutual exclusion.
 
 
6.	Move to the **“Scope”** where you will apply the new data policy only to the default environment.
    
    a.	Select the 2nd radio button named **“Add multiple environments”**.

    ![](images/M01-1/image36.png)
    
    b.	Move to the new section in the wizard named **“Environments”**.
    
    c.	In the list of environments under the **“Available”** section, locate the default environment.
        a.	Note: Your default environment will be named differently, but it will have the **“(default)”** suffix.
    
    d.	Select the default environment and click **“Add to Policy”** button in the top command bar.
    
    ![](images/M01-1/image37.png)
    
    ![](images/M01-1/image38.png)
    
7.	Move to the **“Review”** section of the wizard to confirm you have made the right changes.
    
    a.	Policy name: **“Default data policy”**
    
    b.	Prebuilt connectors: **“(24) Business, 797 (Non-business), (0) Blocked”**
    
    c.	Custom connector patterns: **“1 pattern(s) added”**
    
    d.	Scope: **“Add multiple environments”**
    
    e.	Environments: **“1 environment(s) selected”**
    
    ![](images/M01-1/image39.png)
    
8.	Click **“Create policy”** and you will see your second data policy displayed in the **“Data policies”** page. 

    ![](images/M01-1/image40.png)  
    
    
  **More information:** You can apply more than one data policy to an environment. In fact, the default environment is protected by the “Baseline data policy ” and the                         “Default data policy”. **Power Platform will always enforce the strictest outcome** . For example, if any data policy marks a connector as                             “Blocked”, no canvas app or cloud flow can use that connector in the environment. It doesn't matter whether any other policy classifies                                 that connector as “Business” or “Non-business”. Learn more [here](https://docs.microsoft.com/en-us/power-platform/admin/dlp-combined-effect-multiple-policies).
  
  
**Pro tip:** Although you can layer data policies, try to have at most 2 per environment at once. That will make it easier for you to determine  the effects of your                data policies. Lastly, remember that your environment administrators can autonomously create data policies to environments they administer.


### Task 2: Test the new “Default data policy” when building a canvas app

1.	Go to the Power Apps Maker portal at https://make.powerapps.com using your administrator credentials.

2.	Make sure you are operating in the **“default environment”**.

3.	Click on the **“Apps”** section of the left nav.

4.	Open the **“DLP – Exercise 1 – Task 2”** canvas app that was created previously. Click **“Edit”**. 

    ![](images/M01-1/image41.png) 
    
5.	Add a connector from the **“Business”** category such as **“Microsoft To-Do”**. The canvas app can be saved.    

    ![](images/M01-1/image42.png)        ![](images/M01-1/image43.png) 
    
6.	Add a connector from the **“Non-business”** category such as **“Azure AD”**. 

    ![](images/M01-1/image44.png)
    
7.	Follow the instructions in the dialog after clicking **“Connect”**.

    a.	Use your tenant administrator credentials.

    b.	Skip the 3rd step for configuring Windows Authenticator for your account.
    
    ![](images/M01-1/image44.png)   ![](images/M01-1/image44.png)   ![](images/M01-1/image44.png)
    
    ![](images/M01-1/image44.png)   ![](images/M01-1/image44.png)
    
8.	After clicking **“Allow access”**, you will encounter another error. 

    ![](images/M01-1/image50.png)
    
9.	**Get creative!** Try different combinations of connectors and test the outcomes.

![](images/M01-1/image51.png)


## Exercise 3: Empowering your pro developers


### Scenario

As adoption of the Power Platform grows within your organization, your Makers will increasingly request additional connectors to further support their application and automation building initiatives. This time around, your pro developers are working on a mission-critical project. Remember that your role as an administrator is to empower your pro developers by providing what they need to propel your business forward. To that effect, you have already created three dedicated environments for them: “Thrive HR - Dev”, “Thrive HR - Test”, and “Thrive HR - Prod”. However, beyond dedicated environments, your pro developers need an additional connector – the MSN weather connector* – so they can implement special types of automation. In this third and final exercise, you will create a unique data policy for those 3 environments which grants access to more connectors than the original “Baseline data policy”. Data policy’s granular controls will allow you to partially unblock the MSN weather connector in a safe manner.

* Note: MSN weather was chosen for simplicity’s sake. This scenario usually takes place when you need to enable more advanced connectors such as Azure Blob, HTTP,             etc..

Environments and data policies before exercise #3:

![](images/M01-1/image52.png)

Environments and data policies after exercise #3:

![](images/M01-1/image53.png)


### Task 1: Create the “Pro dev data policy”

1.	Go to the Power Platform admin center using your tenant administrator credentials (https://aka.ms/ppac).
    
    a.	Reminder: Your credentials are in the **“Environment Details”** tab.
    
    ![](images/M01-1/image5.png)
    
2.	Enter the **“Data policies”** page under the **“Policies”** section of the admin center’s left nav.
    
    a.	You will notice the 2 data policies that you have created beforehand.
    
    ![](images/M01-1/image54.png)
    
3.	Select **“Baseline data policy”** and click the **“Edit policy”** button in the top command bar.

4.	Move directly to the **“Scope”** section of the data policy’s wizard.

5.	Select the 3rd radio button named **“Exclude certain environments”**.
   
    ![](images/M01-1/image55.png)
    
6.	Move to the next **“Environments”** section in the data policy’s wizard.

7.	Select environments **“Thrive HR - Dev”, “Thrive HR - Test”, and “Thrive HR - Prod”** and select **“Add to policy”**.
    
    a.	Result: The 3 environments are now excluded from the data policy and will not be protected by it.
    
    ![](images/M01-1/image56.png)
    
    ![](images/M01-1/image57.png)
    
8.	Move to the **“Review”** section of the wizard and click **“Update policy”** if the summary looks right.

    ![](images/M01-1/image58.png)
    
9.	Create your final data policy by clicking **“New Policy”** once last time in the top command bar.

10.	In the **“Policy name”** section of the wizard, enter the following name: **“Pro Dev data policy”**.
 
    ![](images/M01-1/image59.png)
    
11.	In the **“Prebuilt connectors”** section of the wizard, block all connectors that are not published by Microsoft.
    a.	Click the **“Publisher”** column.
    
    b.	Under **“Filter by column value”**, click **“Non Microsoft”**.
    
    c.	Click **“Apply”**.
    
    d.	Select all connectors that are displayed.
    
    e.	Click **“Block”** in the top command bar.
    
    ![](images/M01-1/image60.png)
    
    ![](images/M01-1/image61.png)
    
12.	Select the MSN weather connector in **“Non-business”** and click **“Configure connector > Connector actions”**.

    ![](images/M01-1/image62.png)
    
13.	In the **“Connector actions”** side panel, block the **“Get current weather”** action and block new actions.

    ![](images/M01-1/image63.png)
    
 **More information:** With connector actions (Generally Available), you can control with more granularity how Makers can use a given connector by enabling or                                disabling its actions. Once configured, your Makers cannot build a canvas app or cloud flow if it’s using a blocked action from an enabled                              connector. Learn more [here](https://docs.microsoft.com/en-us/power-platform/admin/dlp-granular-controls).
 
 14.	In the **“Scope”** section of the data policy’s wizard, select the 2nd option named **“Add multiple environments”**.

        ![](images/M01-1/image64.png)
      
 15.	In the **“Environment”** section, add the 3 environments to the data policy: **“Thrive HR – Dev/Test/Prod”**.

        ![](images/M01-1/image65.png)
     
        ![](images/M01-1/image66.png)
      
16.	Make sure your data policy is configured as intended before creating it.

      ![](images/M01-1/image67.png)
      
      
### Task 2: Test the new “Pro dev data policy” when building a cloud flow

1.	Go to the Maker portal using the same tenant administrator credentials (https:/make.powerautomate.com).

    a.	Non-admin users (ex. your pro devs) will experience the same steps depicted below.

    b.	Reminder: Your credentials are in the **“Environment Details”** tab.
    
     ![](images/M01-1/image5.png)
     
     ![](images/M01-1/image68.png)
     
2.	Go to the **“My flows”** section in the left nav and create a new cloud flow named **“DLP – Exercise 2 – Task 2”**.
    
    a.	The flow must be manually triggered.
    
    ![](images/M01-1/image69.png)    ![](images/M01-1/image70.png)
    
3.	Add an operation, and search for **“MSN weather”**.    
     
      ![](images/M01-1/image71.png)
      
4.	Select the **“Get current weather”** action – which is currently blocked – and fill in the information.
    
    a.	You will immediately get an error via the Flow checker when clicking save.
      
    ![](images/M01-1/image72.png)
    
5.	Delete the operation and add another one such as **“Get forecast for today”**.
    
    a.	Your flow will immediately be re-enabled when clicking save.
    
    ![](images/M01-1/image73.png)
    
    
    
### Bonus task: Enable the HTTP connector with endpoint filtering (public preview)

1.	Go to the Power Platform admin center using your tenant administrator credentials (https://aka.ms/ppac).
    
    a.	Reminder: Your credentials are in the **“Environment Details”** tab.
    
    ![](images/M01-1/image5.png)


2.	Locate the HTTP connector in the **“Non-business”** category.

    a.	Select **“Configure connector > Connector endpoints (preview)”**.

    b.	Add an allowed endpoint to the public Cat Fact API: “https://catfact.ninja/*”.

    c.	Change the action to **“Deny”** for the remaining “*” endpoint. 
    
    ![](images/M01-1/image74.png)
    
    ![](images/M01-1/image75.png)
    
    ![](images/M01-1/image76.png)
    
    
**More information:** Thanks to connector endpoints (Public Preview), your pro developers can now only use the HTTP connector to connect to the Cat Fact API. In the                         subsequent steps, the pro developers will be blocked if they attempt to connect to any other API. Learn more about this preview feature and its                         limitations [here](https://docs.microsoft.com/en-us/power-platform/admin/dlp-granular-controls#connector-endpoint-filtering).

**Pro tip:** Instead of manually entering each endpoint, you should pattern matching with the wildcard character (*). By entering “https://catfact.ninja/*”, your pro                developers can access any endpoint with that prefix such as “https://catfact.ninja/fact”, “https://catfact.ninja/facts”, or                                            “https://catfact.ninja/breeds”.

3.	Go to the **“Review”** section of the data policy’s wizard and make sure it is properly configured.

      ![](images/M01-1/image77.png)
      
4.	Go to the Maker portal using the same tenant administrator credentials (https:/make.powerautomate.com).

5.	Open the cloud flow that was created in the previous task (“DLP – Exercise 3 – Task 2”).

6.	Add a new step, search for the **“HTTP”** connector, and add it to the cloud flow.

    a.	Select **“Get”** as the method.

    b.	Enter “https://catfact.ninja/fact” as the URI.

    c.	Leave all other fields empty.

7.	Click save, and manually test the cloud flow. You will find a cat joke in the response object.

      ![](images/M01-1/image78.png)
      
8.	If you change the URI to “https://official-joke-api.appspot.com/random_joke” your cloud flow will be disabled.
      
      ![](images/M01-1/image79.png)
      
9.	**Congratulations!** You have completed this portion of the workshop. You can now try different combinations of connectors, actions and endpoints to test the           outcomes.You can also modify the data policies. Get creative! 
