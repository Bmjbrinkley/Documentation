# Azure Active Directory Setup for Software Company
> Free trial of Microsoft Azure AD: https://azure.microsoft.com/en-us/offers/ms-azr-0044p/
##

## Organization Diagram
Referenced Organization Diagram: 
https://www.edrawsoft.com/templates/pdf/software-company-org-chart.pdf
    
    
  I will be basing my Azure setup based on this template for a small software company, in no way do I believe this diagram represents a normal well-rounded functioning organization.
 
  ![](https://svgshare.com/i/gQa.svg)
  
  #
  
## Manually Create New Users
  Navigate to **Azure Active Directory** and select **Users**. Considering the small amount of employees, we will manually add each user. This step involves filling out general information such as first name, last name, job title, department and so on. I will now add each user manually so I can create credentials and assign roles and groups in the future. I do not plan on adding all employees, **only** the main job titles and departments.
  
  You will notice there's an option for creating or auto-generating the password. In this scenario I will opt-in for generated passwords. At the moment, we don't have any Groups or Roles established, we will get to that later. For **Usage Location**, I'm going with United States - any IP address coming from a location other than the US will be blocked after enabling this option. This step will act as a minor deterrent for malicious threats outside of the United States in regards to database leaks.
  
  After filling out the rest of the form and adding the remainder of employees, you will notice the new users listed under **All Users** on the left panel.
  
 *In the case that I would ever need to add bulk users, I would likely utilize **Bulk Operations** and import a .CSV file or integrate PowerShell scripts with Azure AD for efficiency, speed and convenience.* 
 
 [**.CSV example for importing users via Azure Bulk Operations or PowerShell automation**](https://docs.google.com/spreadsheets/d/1Qt_GbjJlud19sVa3vzzpWZR605uasFUcdc_nw4ugG2U/edit?usp=sharing)
 
## Enabling 2FA
 Navigate to **All Users** and select **Per-User MFA**. A new window will appear. Check mark all the employees by clicking the box in the top row. Under **Quick Steps** choose **Enable** you should receive a dialog box that communicates to you that the update was successful. This means that the account is ready to setup and configure MFA once the user has attempted to log in with their credentials.
 
 
 
 
 
 
 
  
  
  
  
  
  
  