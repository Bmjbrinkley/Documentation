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

## Creating Groups and Assigning Members
After creating our users it's important that we assign them to the proper groups. Certain groups may have access to specific things that are required for the job. It's important to always consider the best security practices when assigning credentials and groups. 

For example, Emily Warren has a set of permissions that allow her to do her job efficiently in the sales department. If Emily had elevated privileges, she would have unnecessary access, such as uninstalling or installing applications. This would likely create security concerns and snowball into greater problems down the road.

On the left panel you will see **Groups** go ahead and select it. This group will be the sales department. For **Group Type** I selected **Microsoft 365**, **Group Name** will be sales in this case. I decided this department didn't need a description so I selected **Members** at the bottom of the form. Since we're creating the sales group, I've selected *Emily Warren* as the only member. Click the gray **Create** button at the bottom after and this group will be created.

## Group Settings

After successfully assigning software company members to their department groups you will notice **Naming Policy** on the left panel, select it. This feature allows us to block profanity, reserve names and aliases in Microsoft 365 groups. I decided to upload a .CSV from Google that already has a large list just for testing purposes. In the same tab you will notice **Group Naming Policy**, This allows an administrator to allow/add prefixes or suffixes to group names created by users.

**Example**: *(Finance) (Group) (Seattle)*

In this case I won't be using GNP - I find it unnecessary for the time being. Another option is **Expiration**. This deals with group lifetime, licensing and much more. I won't be delving into this at the moment.

## Enabling MFA (Multi-factor Authentication)
Navigate to **All Users** and select **Per-User MFA**. A new window will appear. Check mark all the employees by clicking the box in the top row. Under **Quick Steps** choose **Enable** you should receive a dialog box that communicates to you that the update was successful. This means that the account is ready to setup and configure MFA once the user has attempted to log in with their credentials.

## Authentication Methods
Navigate to **All Users** and select *Alexander Fowler*. On the left panel click **Authentication Methods**. We have two options available here - the old version, which offers authentication via phone or email and the new version which includes these options along with a **Temporary Access Pass**. I decided to go with the new authentication methods experience and input mobile phone number to test this feature later on. I set a phone number for every employee in the software company.

## Password Reset
On the left panel, click **Password Reset**. You will notice the **Self-Service Password Reset** page. Unfortunately I don't have access to this feature, but I would likely use this option in an enterprise environment. Since we're only working with 7 users in a lab environment - this shouldn't be a problem.

## External Identities
I will add this later.

## Roles and Administrators
I will add this later.

## Administrative Units
I will add this later.

## Enterprise Applications
I will add this later.

## Device Management
I will add this later.

## Application Registrations
I will add this later.

## Identity Governance
I will add this later.

## Application Proxy
I will add this later.

## Licenses
I will add this later.

## Azure AD Connect
I will add this later.

## Custom Domain Names
I will add this later.

## Mobility (MDM and MAM)
I will add this later.

## Directory Properties
I will add this later.

## Security Documentation and Guidance
I will add this later.
