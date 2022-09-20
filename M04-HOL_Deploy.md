# Admin in a day

## M04-HOL Application Lifecycle Management and Deploying Apps (Optional)


### Lab Scenario

 In this Hands-on Lab, you are an administrator for Contoso, helping
 them to adopt the Power Platform.

 The team building the Device Order Management app is now ready for you
 to transport their solution from their development environment to the
 test environment for testing.

 In this lab, you will be using Azure DevOps and the Power Apps build
 tools to automate checking their solution into a source control
 repository and then using that to deploy to test and production.

 Because this is the first deployment to test, you will have to do some
 setup to configure security for users to be able to access the app.

### Lab Test Environment

 This hands-on lab is designed to be completed in an environment setup
 for multiple students to complete the Admin in a day series of
 hands-on labs.

 You will be assigned one or more users to use to complete the hands-on
 tasks. Because this is a shared environment, some tasks that require a
 tenant Global Administrator or a Service Administrator will already be
 performed.

 This lab assumes you have completed M03_Automation prior to starting
 this lab. In that lab you would have created the environment that you
 will deploy to in this lab.


 **Important!** To avoid abuse Azure Pipelines now requires approval in
 free accounts to run pipelines. Use this to request the free grant of
 parallel jobs in Azure Pipelines. Please fill out this must be
 approved before you can complete the steps in this lab.

 You will receive an email when your approval request is completed.

## Exercise 1: Initialize Azure DevOps

 In this exercise, you will be signing up for an Azure DevOps account
 and configuring the PowerApps build tools for the account.

 **Note:** If you already have Azure DevOps outside of this course and this environment, you CANNOT use that here. You will need to follow our instructions to sign                up.

### Task 1: Signup for Azure DevOps

1. Navigate to and click **Sign in to Azure DevOps**.

 **Note:** Use the same account you have been using for the other labs.


  ![](images/M04/image1.png)
  

2. Provide your credentials and click **Next**.

3. Provide a **Password** and click **Sign in**.

4. Click **Continue**.

5. If prompted, provide a unique **Azure DevOps Organization** name such as lastnameMMYY, select a location closest to your tenant, select your region, enter captcha      if prompted and click **Continue**. Replace lastname with your last name, MM current month and YY current year.

  ![](images/M04/image2.png)
  
6. Enter **Device Management lastnameMMYY** for **Project Name** and click **Create project**. Replace lastname with your Last name, MM with current month, and YY        with current year.

  
  ![](images/M04/image3.png)
 
Projects are containers in Azure DevOps that track work items and source assets. When you set up the automation for the deployment tasks those will be pipelines built in the context of a project.

7. Select **Repos**.


  ![](images/M04/image4.png)
  
An Azure Repo is a source/version control container inside the Azure DevOps project used to track changes you make. You will be using it to store the solution files for the team building the Device Ordering app.

8. Check the **Add a Readme** checkbox and click **Initialize**.


  ![](images/M04/image5.png)


### Task 2: Configure Power Apps Build Tasks

1. Click on the shopping basket icon and select Browse marketplace.

  
  ![](images/M04/image6.png)
  

2. Search for **Power Platform**.
 
3. Select **Power Platform Build Tools**.

  
  ![](images/M04/image7.png)
  

4. Click **Get it Free**.

  
  ![](images/M04/image8.png)
  

5. Select the **Azure DevOpsorganization** you created and click **Install**.

 
  ![](images/M04/image9.png)
  

6. Click **Proceed to Organization**.

  
  ![](images/M04/image10.png)
  

7. Click to open the **Device Management** project you created.


  ![](images/M04/image11.png)
  

## Exercise 2: Build Export Pipeline

 In this exercise, you will build an Azure DevOps pipeline that will export the solution from the
 development Dataverse environment, unpack the solution file to
 individual files and then check those files into the repository. These
 solution files can be then used to re-create development environments
 or to promote the solution to test/production.

### Task 1: Export Solution

1. Create a Build Pipeline.

   a. Click to expand **Pipelines**.


     ![](images/M04/image12.png)
  

   b. Select **Pipelines**.

  
     ![](images/M04/image13.png)
  

   c. Click **Create Pipeline**.

  
      ![](images/M04/image14.png)


   d. Click **Use the Classic Editor.**


      ![](images/M04/image15.png)


   e. Do not change the default values and click **Continue**.


      ![](images/M04/image16.png)
 

   f. Select **Empty Job**.


      ![](images/M04/image17.png)


   g. Click **Save and Queue** and select **Save**.

  
      ![](images/M04/image18.png)


   h. Click **Save**.

  
      ![](images/M04/image19.png)
 

2. Add PowerApps Tool Installer task.

 **Note:** The Power Platform Tool Installer needs to be run before any other Power Platform build tasks.

   a. Click **+ Add Task to Agent Job 1**.

   ![](images/M04/image20.png)
 

   b. Search for **Power Platform** hover over select **Power Platform Tool Installer** and click **Add**.

  
   ![](images/M04/image21.png)


3. Add Power Platform Export Solution task.

     a. Search for **Export.**
    
     b. Hover over **Power Platform Export Solution** and click **Add**.


      ![](images/M04/image22.png)


4. Open Power Platform Export Solution.

     a. Select the **Power Platform Export Solution** task.

  
      ![](images/M04/image23.png)
  

5. Get your development environment URL
     a. Start a new browser window or tab and navigate to

     b.Select **Environments** and click to open the **Device Ordering Development** environment. c. Copy the **Environment URL** and keep it in your clipboard or you        can keep this URL on a notepad.

  
      ![](images/M04/image24.png)


     d.Close the **Power Platform Admin** browser window or tab.

6. Create a **Generic Service Connection.** Service Connections are how the build tasks know what environment URL and user credentials to use to access the Common        Data Service environments. 
 
     a. Make sure you still have the **Power Platform Export Solution** task selected.

     b. Click **Manage**.

  
      ![](images/M04/image25.png)
 

     c. Click Create Service Connection.

  
      ![](images/M04/image26.png)
  

     d.Select **Generic** and then click **Next**.

  
      ![](images/M04/image27.png)
 

     e. Provide a **Connection Name**, paste the **Environment URL** you copied, provide your credentials, and click **Save**.

  
      ![](images/M04/image28.png)
 

     f. Close the **Service Connections** browser window or tab.


7. Select the Generic Service Connection you created as the Power Apps Environment URL.

     a. Go back to the **Build Pipeline** tasks and make sure you still have PowerApps Export Solution task selected.

     b.Locate the **Service Connection** field and click **Refresh**.

      ![](images/M04/image29.png)
  

     c. Select the **Generic Service Connection** you just created named Dev Connection.

      ![](images/M04/image30.png)
 

     d. Enter **\$(SolutionName)** for **Solution Name**, **\$(Build.ArtifactStagingDirectory)\\\$(SolutionName).zip** for **Solution Output File**.

  
      ![](images/M04/image31.png)
  

     e. Click **+** add Task.

 
      ![](images/M04/image32.png)
  

     f. Add another **Export Solution** task.


      ![](images/M04/image33.png)
  

     g. Select **Dev Connection** for the Power Apps Environment URL.
     
     h. Check the Export as Managed Solution.
     
     i. Enter **\$(SolutionName)** for **Solution Name**, **$(Build.ArtifactStagingDirectory)\$(SolutionName)_managed.zip** for **Solution** **Output File**

  
      ![](images/M04/image34.png)
  
8. Add an Unpack task. This task will take the solution zip file and expand it into a file for each solution component.\
   
     a. Click **+ Add Task**.

      ![](images/M04/image35.png)
  

     b.Search for **Unpack**.
     
     c. Hover over **Power Platform Unpack Solution** and click **Add**.

  
      ![](images/M04/image36.png)
 

9. Provide Unpack settings information.
     
     a. Select the **Unpack** task.
     
     b. Enter **$(Build.ArtifactStagingDirectory)\$(SolutionName).zip** for **Solution InputFile**, **$(Build.SourcesDirectory)\$(SolutionName)** for **Target
        Folder**.
     
     c. Choose **Both** for Type of Solution.

      ![](images/M04/image37.png)
 

10. Allow scripts to access the OAuth Token. This will allow the commands you will add to check in files to the Azure DevOps repo to work.
     
     a. Select **Agent Job 1**.

       ![](images/M04/image38.png)
  

     b.Scroll down and check the **Allow Scripts to Access the OAuth Token** checkbox.


       ![](images/M04/image39.png)
 

11. Add Command Line task.
     a. Click **+ Add a Task**.

 
       ![](images/M04/image40.png)
  


     b.Search for **Command line**. 

     c. Hover over **Command Line** and click **Add**.             

  
       ![](images/M04/image41.png)
  

12. Add Scripts to the Command Line task. This task will be used to check in the solution file changes to the repo.      

     a. Select the Command Line task. 


       ![](images/M04/image42.png)
  

     b.Paste the script below in the **Script** text area. Replace **user@myorg.onmicrosoft.com** with your username.

        
         echo commit all changes                                            
         git config user.email "user\@myorg.onmicrosoft.com"              
         git config user.name "Automatic Build"                           
         git checkout main                                                  
         git add --all                                                     
         git commit -m "solution updates"                                 
         echo push code to new repo                                         
         git -c http.extraheader=\"AUTHORIZATION: bearer $(System.AccessToken)" push                                      
         origin main    
         
   
  
       ![](images/M04/image43.png)
  

13. Add Solution Name variable.
     
     a. Select the **Variables** tab.
     
     b.Click **+ Add.**

  
       ![](images/M04/image44.png)
 

    c. Enter **SolutionName** for **Name** and **ContosoDeviceOrderManagement** for **Value**. Confirm that there are no extra spaces at the end  of the value after         pasting.                      


       ![](images/M04/image45.png)
  

    d.Click **Save and Queue** and select **Save**.
    
    e.Click **Save** again.


## Exercise 3: Test the Pipeline

In this exercise, you will test the build pipeline you created.


### Task 1: Run the Pipeline

1. Open the build pipeline.
    a. Navigate to and click to open the **Device Management** project.
    
    b.Select **Pipelines \| Pipelines**.

  
      ![](images/M04/image13.png)
  

    c. Click **Device Management-youruser-CI**.

  
      ![](images/M04/image46.png)
  

    d. Click **Run Pipeline**

  
      ![](images/M04/image47.png)
  

    e. Select **Run** again and wait.


      ![](images/M04/image48.png)
  

    f. Refresh the screen until your Agent job 1 has a Status of **Running.**


      ![](images/M04/image49.png)
  

    g. Click on **Agent job 1** to open the job\
    
    h. The build will run up to the Command Line Script and fail because we need to adjust permissions. The first run causes a project specific build service user to        be added, we will adjust the permissions to fix this problem.

  
      ![](images/M04/image50.png)
  

    i. Click **Project Settings** in the lower left corner.


      ![](images/M04/image51.png)
 

    j. Select **Repositories**.


      ![](images/M04/image52.png)
 

    k. Select the **Security** tab. 
    
    l. In the **Users** section, select the **Device Management Build Service** user. 


      ![](images/M04/image53.png)
 

    m. In the **Access Control Summary**, locate **Contribute** and change it to **Allow**.

  
      ![](images/M04/image54.png)
  

    n.Select **Pipelines** | **Pipelines** in the left navigation.

  
      ![](images/M04/image55.png)
 

    o.Click to open the failed run.
    
    p.Click **Run Pipeline**.

  
      ![](images/M04/image56.png)
 

    q.Click **Run** and wait until the status changes to **Running**. 
    
    r. Click to open the job.


      ![](images/M04//image57.png)
  

    s. The job should now run successfully


      ![](images/M04/image58.png)
  

2. Review the Repository.
    
    a. Select Repos.


      ![](images/M04/image59.png)
  

    b. You should see **ContosoDeviceOrderManagement** folder. Click to open the folder.

  
      ![](images/M04/image60.png)
  

    c. The content of the folder should look like the image below.


      ![](images/M04/image61.png)
  

    d.You may examine the content of the folders.

## Exercise 4: Build Manage Solution and Publish Artifacts


 In this exercise, you will take the solution files checked into the
 repo in the prior steps and re-package them into a managed solution
 file. This solution file will be published as a build artifact so it
 can be used in the release pipeline we are going to use to publish to
 test and production.

 In a real project this is where you could add steps to import the
 solution into a build Dataverse environment to check for missing
 dependencies. You could also add build tasks to run tests against your
 solution as well as run Power Apps Solution Checker to detect
 problems. In this lab exercise we will skip those extra steps to
 ensure you have enough time to complete the lab.

### Task 1: Build the Managed Solution

1. Select **Pipelines**, click **New Pipeline**.

  
   ![](images/M04/image62.png)
  

2. Click **Use Classic Editor**.


   ![](images/M04/image63.png)


3. Click **Continue**.


   ![](images/M04/image64.png)
  

4. Click **Empty Job.**

  
   ![](images/M04/image65.png)
  

5. Enter **Build Managed Solution** for **Name**, click **Save and Queue** and select **Save**.


    ![](images/M04/image66.png)


6. Click **Save** again.

7. Click **Add a Task** to **Agent Job 1**.

 
    ![](images/M04/image67.png)
  

8. Search for **Power Platform Tool**, hover over **Power Platform Tool Installer** and click **Add**.


  
    ![](images/M04/image68.png)
  

9. Search for **Power Platform Pack**, hover over **Power Platform Pack Solution** and click **Add**.

  
    ![](images/M04/image69.png)
 

10. Select the **Power Platform Pack Solution** task.


     ![](images/M04/image70.png)
 

11. Enter **$(Build.SourcesDirectory)\$(SolutionName)** for **Source Folder of Solution to Pack**, enter **$(Build.ArtifactStagingDirectory)\$(SolutionName).zip**         for **Solution Output Folder**.
12. Change the solution type to **Managed**


     ![](images/M04/image71.png){


13. Select the **Variables** tab and click **+ Add**.

  
     ![](images/M04/image72.png)

14. Enter **SolutionName** for **Name** and **ContosoDeviceOrderManagement** for **Value**.

  
     ![](images/M04/image73.png)
  

15. Select the **Tasks** tab.


  ![](images/M04/image74.png)
  

16. Click **Add a Task**.
17. Search **Publish Pipeline**, hover over **Publish Pipeline Artifact** and click **Add**. Publishing the solution as an artifact will make it available for the         release pipeline you will build.

  
     ![](images/M04/image75.png)
  

18. Select the **Publish Pipeline Artifact** task.

19. Enter **$(Build.ArtifactStagingDirectory)\$(SolutionName).zip** for **File or Directory Path** and enter **drop** for **Artifact Name**.

  
     ![](images/M04/image76.png)
  

20. Click **Save and Queue** and select **Save and Queue**.

  
     ![](images/M04/image77.png)
 

21. Click **Save and Run**.

22. Refresh the page until Agent Job 1 has a status of **Running**


     ![](images/M04/image78.png)


23. Click on **Agent job 1** and wait for the run to complete. Build tasks should run and succeed.

  
     ![](images/M04/image79.png)
 

24.Click on **1 artifact produced**

 
     ![](images/M04/image80.png)
  

25. Expand the folder and you should see the managed solution.

  
     ![](images/M04/image81.png)
 

## Exercise 5: Build a Release Pipeline

 In this exercise, you will build your release pipeline. The release
 pipeline is intended to take the output from the build pipeline and
 coordinate deployments to one or more release environments. A common
 release pipeline might deploy to dev -\> test -\> user acceptance -\>
 production. Release pipelines can have approval requirements between
 each environment.

 For the purposes of this lab, we are only going to deploy to one test
 environment. We will be using the Central Apps Test trial environment
 we created in the previous lab. In real use, you would deploy to both
 Test and Production and would use environments of type production
 instead of trial.

## Task 1: Create Connection and Release to Prod

1. Go back to\

2. Click to open the **Device Management** project.


    ![](images/M04/image82.png)


3. Click **Project Settings.**

  
     ![](images/M04/image83.png)
  

4. Go to the **Pipelines** area and select **Service Connections**.

 
     ![](images/M04/image84.png)
 

5.Click **New Service Connection**.


     ![](images/M04/image85.png)
  

6. Select **Generic** and click **Next**.

 
     ![](images/M04/image27.png)


7. In a new browser window or tab, navigate to\

8. Select **Environments** and locate your **Central Apps Test** environment you created in the prior lab.

9. Click on the environment name to show the details, and then copy the **URL** from the detail screen.

  
     ![](images/M04/image86.png)
  

10. Enter **Test** for **Connection Name**, paste the **Environment URL** copied in the previous step, provide your credentials, and click **Save**.

  
     ![](images/M04/image87.png)
 

11. Select **Pipelines** -> **Releases**.

  
     ![](images/M04/image88.png)
 

12. Click **New Pipeline**.


     ![](images/M04/image89.png)
  

13. Select **Empty Job**.


     ![](images/M04/image90.png)


14. Enter **Test** for **Stage Name** and click **+ Add Artifacts**.

  
     ![](images/M04/image91.png)
 

15. Select **Build Managed Solution** for **Source** and click **Add**.


    ![](images/M04/image92.png)
  

16. Select the **Tasks** tab and click **+ Add Task**.

 
     ![](images/M04/image93.png)
 

17. Search for **Power Platform Tool**, hover over **Power Platform Tool Installer** and click **Add**.

  
     ![](images/M04/image68.png)
  

18. Search for **Power Platform Import**, hover over **Power Platform Import Solution** and click **Add**.

  
     ![](images/M04/image94.png)
 

19. Select the **Power Platform Import Solution** task.
20. Select the **Test** connection for Environment and enter **$(System.DefaultWorkingDirectory)/_Build Managed Solution/drop/$(SolutionName).zip** for **Solution         Input File**.

  
     ![](images/M04/image95.png)
 

21. Select the **Variables** tab and click **+ Add**.


     ![](images/M04/image96.png)
 

22. Enter **SolutionName** for **Name**, **ContosoDeviceOrderManagement** for **Value**, and click **Save**.

 
     ![](images/M04/image97.png)


23. Click **OK**.

24. Click **Create Release**.


     ![](images/M04/image98.png)
  

25. Click **Create**.


     ![](images/M04/image99.png)
 

26. Select **Releases** and click to open the release.


     ![](images/M04/image100.png)
 

27. Wait for the release tasks to complete. The release pipeline should succeed.

  
     ![](images/M04/image101.png)
 
If your Release has succeeded, go to to Step 28\
If your Release has failed, try:

A common error here is the import fails because the Solution file is not found -- one of the reasons for this could be that you have named your pipeline different to what's written in the lab.


   ![](images/M04/image102.png)
 

A fix for this is to manually select the solution file for the import.To do click on **Edit \| Edit Pipeline**

  
   ![](images/M04/image103.png)


Select the **Test Task**

  
  ![](images/M04/image104.png)
 

  ![](images/M04/image104.png)

Select **PowerApps Import Solution**\
Select the ... next to **Solution Input File**

  
   ![](images/M04/image105.png)
 

Select the .zip file in the drop folder and confirm with OK

  
   ![](images/M04/image106.png)
 

Go back to Releases and click **Create Release and Create**

28. Navigate to and select the **Test** environment **Central Apps Test**.

  
    ![](images/M04/image107.png)
 

29. Select **Solutions**. You should see the managed solution you published from the release pipeline. 
30. Click to open the **Contoso Device Order Management** solution.

  
    ![](images/M04/image108.png)
  

31. You should get the **You cannot edit managed** solution message.


    ![](images/M04/image109.png)


32. Select Apps. You should see **Device Ordering App** Canvas application and **Device Procurement** Model-Driven-Application.

  
    ![](images/M04/image110.png)



 DISCLAIMER

 This demo/lab contains only a portion of new features and enhancements
 in Microsoft Power Apps. Some of the features might change in future
 releases of the product. In this demo/lab, you will learn about some,
 but not all, new features.


