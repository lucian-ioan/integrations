# Microsoft Office 365 Metrics Integration

This integration is to collect metrics for [Microsoft Office 365](https://learn.microsoft.com/en-us/graph/overview).

## Setup

To use this package you need to enable datastreams you want to collect metrics for and register an application in [Microsoft Entra ID (formerly known as Azure Active Directory)](https://www.microsoft.com/en-us/security/business/identity-access/microsoft-entra-id).

Once the application is registered, configure and/or note the following to setup O365 metrics Elastic integration:
1. Note `Application (client) ID` and the `Directory (tenant) ID` in the registered application's `Overview` page.
2. Create a new secret to configure the authentication of your application. 
    - Navigate to `Certificates & Secrets` section.
    - Click `New client secret` and provide some description to create new secret.
    - Note the `Value` which is required for the integration setup.
3. Add permissions to your registered application. Please check [O365 Graph API permissions](https://learn.microsoft.com/en-us/graph/reportroot-authorization) for more details.
    - Navigate to `API permissions` page and click `Add a permission`
    - Select `Office 365 Management APIs` tile from the listed tiles.
    - Click `Application permissions`.
    - If `User.Read` permission under `Microsoft.Graph` tile is not added by default, add this permission.
    - After the permissions are added, the admin has to grant consent for these permissions.

Once the secret is created and permissions are granted by admin, setup Elastic Agent's Microsoft O365 integration:
- Click `Add Microsoft Office 365`.
- Enable `Collect Office 365 metrics via Graph API using CEL Input`.
- Add `Directory (tenant) ID` noted in Step 1 into `Directory (tenant) ID` parameter. This is required field.
- Add `Application (client) ID` noted in Step 1 into `Application (client) ID` parameter. This is required field.
- Add the secret `Value` noted in Step 2 into `Client Secret` parameter. This is required field.
- Oauth2 Token URL can be added to generate the tokens during the oauth2 flow. If not provided, above `Directory (tenant) ID` will be used for oauth2 token generation.
- Modify any other parameters as necessary.



## Compatibility



## Metrics

### SharePoint Site Usage Details

Uses the Office 365 Management Graph API to retrieve metrics from Office 365. 


**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Event timestamp. | date |
| cloud.image.id | Image ID for the cloud instance. | keyword |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| host.containerized | If the host is a container. | boolean |
| host.os.build | OS build information. | keyword |
| host.os.codename | OS codename, if any. | keyword |
| input.type | Type of Filebeat input. | keyword |
| o365metrics.sharepoint_siteusagedetails.ActiveFileCount | The number of active files on the SharePoint site during the reporting period. | integer |
| o365metrics.sharepoint_siteusagedetails.FileCount | The total number of files on the SharePoint site. | integer |
| o365metrics.sharepoint_siteusagedetails.IsDeleted | Indicates whether the SharePoint site is marked as deleted (True or False). | boolean |
| o365metrics.sharepoint_siteusagedetails.LastActivityDate | The date of the last recorded activity on the SharePoint site. May be blank if no activity is recorded. | date |
| o365metrics.sharepoint_siteusagedetails.OwnerDisplayName | The display name of the SharePoint site owner. | keyword |
| o365metrics.sharepoint_siteusagedetails.OwnerPrincipalName | The principal name (email or username) of the SharePoint site owner. | keyword |
| o365metrics.sharepoint_siteusagedetails.PageViewCount | The number of page views on the SharePoint site during the reporting period. | integer |
| o365metrics.sharepoint_siteusagedetails.ReportPeriod | The duration of the reporting period for SharePoint site usage, in days. | integer |
| o365metrics.sharepoint_siteusagedetails.ReportRefreshDate | The date when the SharePoint site usage data was last refreshed. | date |
| o365metrics.sharepoint_siteusagedetails.RootWebTemplate | The template used to create the root web of the SharePoint site (e.g., Team Site). | keyword |
| o365metrics.sharepoint_siteusagedetails.SiteId | The unique identifier of the SharePoint site. | keyword |
| o365metrics.sharepoint_siteusagedetails.SiteURL | The URL of the SharePoint site. | keyword |
| o365metrics.sharepoint_siteusagedetails.StorageAllocatedByte | The total storage allocated to the SharePoint site, in bytes. | integer |
| o365metrics.sharepoint_siteusagedetails.StorageUsedByte | The amount of storage used on the SharePoint site, in bytes. | integer |
| o365metrics.sharepoint_siteusagedetails.VisitedPageCount | The number of unique page visits on the SharePoint site during the reporting period. | integer |


### SharePoint Site Usage Storage

Uses the Office 365 Management Graph API to retrieve metrics from Office 365. 


**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Event timestamp. | date |
| cloud.image.id | Image ID for the cloud instance. | keyword |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| host.containerized | If the host is a container. | boolean |
| host.os.build | OS build information. | keyword |
| host.os.codename | OS codename, if any. | keyword |
| input.type | Type of Filebeat input. | keyword |
| o365metrics.sharepoint_siteusagestorage.ReportDate | The date the SharePoint site storage usage report was generated. | date |
| o365metrics.sharepoint_siteusagestorage.ReportPeriod | The duration of the reporting period for SharePoint site storage usage, in days. | integer |
| o365metrics.sharepoint_siteusagestorage.ReportRefreshDate | The date when the SharePoint site storage usage data was last refreshed. | date |
| o365metrics.sharepoint_siteusagestorage.SiteType | The type of SharePoint sites included in the report (e.g., All, Team, Personal). | keyword |
| o365metrics.sharepoint_siteusagestorage.StorageUsedByte | The total storage used across SharePoint sites during the reporting period, in bytes. | integer |

