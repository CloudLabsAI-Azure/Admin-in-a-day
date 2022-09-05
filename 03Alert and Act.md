# Lab 03 - Action through Automation

## Lab Scenario

In this hands-on lab, you are an administrator, helping to adopt the Power Platform.

Contoso has decided to control creation of Power Platform environments by disabling creation unless you 
are a global or service admin. Contoso doesn’t want to discourage use of the Power Platform so they 
would like you to put an automated process in place to allow users to request an environment and a 
Microsoft Dataverse database.

In this lab, you will be building a Microsoft Form to allow users to submit their environment requests. 
Using the Power Platform administrative connectors and the built-in approval capabilities of Power 
Automate you will automate the processing of the requests.

The following is an outline of the process you will be implementing:
• A user submits request via the form including justification for the environment
• Form submission triggers flow to run
• Flow uses the approval connector to ask admin team for approval
• If approved, the environment and Dataverse database are created
• User is notified of the outcome; approved or rejected.

This process could easily be expanded to request approval from the user’s manager as well as the request 
information along with the environment information could be stored for resource usage charge back.

Contoso has also decided to use the app auditing process from the CoE Starter Kit. You will be seeing 
how this works by going through the process as both a maker and an admin. 

Additionally, you will be installing a pre-created flow that checks for new people building apps and adds 
them to an Office 365 group and sends them a welcome email.

### Lab Test Environment
This hands-on lab is designed to be completed in an environment setup for multiple students to complete 
the Admin in a day series of hands-on labs.

You will be assigned one or more users to use to complete the hands-on tasks. Because this is a shared 
environment, some tasks that require a tenant Global Administrator or a Service Administrator will already 
be performed.

This lab does not require you have completed any of the prior labs.

## Exercise 1: Create Environment Request Form

### Scenario

In this exercise, you will be creating an environment request form using Microsoft Forms. This form could collect additional information allowing it to be tailored to your individual organization requirements.

### Task 1: Create Microsoft Form

1. While logged in as the lab admin user navigate to Microsoft Forms and close the welcome screen.

     ![](images/L03-1.png)
     
2. Click **New Form**.

     ![](images/L03-2.png)
     
  >**Note:** Create the Form below, if you need steps, continue the steps here. If you do not need each step, continue to the next exercise.

      ![](images/L03-3.png)
      
3. Enter **New Environment Approval Request** for title, enter **New environment request** for description, and click **Add new**.

      ![](images/L03-4.png)
