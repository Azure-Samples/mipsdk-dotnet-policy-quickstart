---
page_type: sample
languages:
- csharp
products:
- m365
- office-365
description: "This sample application demonstrates using the Microsoft Information Protection SDK .NET wrapper to compute actions given labeling option inputs."
urlFragment: MipSDK-Policy-Dotnet-Quickstart
---

# MipSDK-Policy-Dotnet-Quickstart

This sample application demonstrates using the Microsoft Information Protection SDK .NET wrapper to compute actions for a given label. 

This sample illustrates basic SDK functionality where it:

- Obtains the list of labels for the user
- Prompts to input one of the label IDs
- Prompts the user to enter a second "new" label ID
- Repeatedly calls the `ComputeAction()` function until no actions remain.
- Displays label actions to the screen.

## Summary

This sample application illustrates using the MIP Policy API to list labels, and compute actions for a new label. All SDK actions are implemented in **action.cs**. 

## Getting Started

### Prerequisites

- Visual Studio 2015 or later with Visual C# development features installed

### Sample Setup

In Visual Studio 2017:

1. Right-Select the project and select **Manage NuGet Packages**
2. On the **Browse** tab, search for *Microsoft.InformationProtection.File*
3. Select the package and Select **Install**

### Create an Azure AD App Registration

Authentication against the Azure AD tenant requires creating a native application registration. The client ID created in this step is used in a later step to generate an OAuth2 token.

> Skip this step if you've already created a registration for previous sample. You may continue to use that client ID.

1. Go to https://portal.azure.com and log in as a global admin.
   > Your tenant may permit standard users to register applications. If you aren't a global admin, you can attempt these steps, but may need to work with a tenant administrator to have an application registered or be granted access to register applications.
2. Select Azure Active Directory, then **App Registrations** on the left side menu.
3. Select **New registration**
4. For name, enter **MipSdk-Sample-Apps**
5. Under **Supported account types** set **Accounts in this organizational directory only**
   > Optionally, set this to **Accounts in any organizational directory**.
6. Select **Register**
 
The **Application registration** screen should now be displaying your new application.

### Add API Permissions 

1. Select **API Permissions**
2. Select **Add a permission**
3. Select **Azure Rights Management Services**
4. Select **Delegated permissions**
5. Check **user_impersonation** and select **Add permissions** at the bottom of the screen.
6. Select **Add a permission**
7. Select **APIs my organization uses**
8. In the search box, type **Microsoft Information Protection Sync Service** then select the service.
9. Select **Delegated permissions**
10. Check **UnifiedPolicy.User.Read** then select **Add permissions**
11. In the **API permissions** menu, select **Grant admin consent for <TENANT NAME>** and confirm.

### Set Redirect URI

1. Select **Authentication**.
2. Select **Add a platform**.
3. Select **Mobile and desktop applications**
4. Select the default native client redirect URI, which should look similar to **https://login.microsoftonline.com/common/oauth2/nativeclient**.
5. Select **configure** and be sure to save and changes if required. 

### Update Client ID, RedirectURI, and Application Name

1. Open **app.config**.
2. Replace **YOUR CLIENT ID** with the client ID copied from the AAD App Registration.3. 
3. Replace **YOUR APP NAME** with the friendly name for your application.
4. Replace **YOUR APP VERSION** with the version of your application.
5. If you set the applicaiton type to single-tenant, set the value of **ida:IsMultiTenantApp** to **false**. Otherwise set to **true**.
6. If you set the application type to single-tenant, replace **YOUR TENANT GUID** with the GUID or name of your Azure Active Directly tenant.

## Run the Sample

Press F5 to run the sample. The console application will start and after a brief moment displays the labels available for the user.

- Copy a label ID to the clipboard.
- Paste the label in to the input prompt.
- Copy a second label to the clipboard and paste in the 2nd prompt.
- The app will compute actions and display the various protection, marking, and metadata actions to the screen.
- It's up to the calling application to understand and apply these actions.

## Resources

- [Microsoft Information Protection Docs](https://aka.ms/mipsdkdocs)
