# AWS-Storage

***Objectives***
- Creating a S3 bucket to host a static website
- Upload content to the bucket and configuring public access.
- Implementing bucket policy security.
- Enabling object versioning.

**S3:** 

## Task A: Bucket creation

1. Search for S3 services in the search bar of the management console.
   
   <img src = "https://github.com/user-attachments/assets/b3fa0a03-03e6-4626-8af1-dc30085eb824" width = "400">
3. Choose **_Create bucket._** **Bucket names have to be globally unique. All AWS accounts share the namespace.**
4. For this instance we use the name **sim-website**
   
   <img src = "https://github.com/user-attachments/assets/2a814573-37d3-4b94-b4c3-e946dd57b2e3" width = "400">
5. For **_Object Ownership_** enable ACLs so we can provide controlled access to the objects.
6. I keep the **_bucket owner preferred_** enabled as only I will be uploading to the the bucket.

   <img src = "https://github.com/user-attachments/assets/b1323f1a-9ec0-4973-8b1b-1253530f2e94" width = "400">
7. Since this is S3 will contain the files for the static website. The files must be accessible through the internet. For this I permit public access by clearing the checkbox for **Block _all_ public access**.
   
   <img src = "https://github.com/user-attachments/assets/45eaf130-aed9-4eef-a0a9-6505759b9900" width = "400">
   
   I have to select the box that acknowledges the settings. 
    
8. For **_Bucket Versioning_** I choose **_Enable_**. It is important to understand that once bucket versioning is enabled, it cannot be turned off.
   
   <img src = "https://github.com/user-attachments/assets/4c5f684b-689d-4390-a0fc-c37effd3528c" width = "400">

9. I choose to **_Add tag_** with the following **key:Department** and **Value:Marketing**.

   <img src = "https://github.com/user-attachments/assets/b1ec02ff-1a8f-4abb-a86f-86406434f8c8" width = "400">

10. After choosing **_Create bucket_**, the new bucket appears in the list.
    
    <img src = "https://github.com/user-attachments/assets/83ea02a7-31a0-417c-a9ce-df0bf3a28369" width ="400">

## Task B: Static website configuration
1. Select the newly created bucket from the bucket list.
2. Choose the **_Properties_** tab.
3. In the **_Static website hosting_** panel choose to **_Edit_** and then choose **_enable_**.
4. For the **_Hosting type_**, I keep the default to host a static website.
5. I now make the following configurations.
   - **_Index document_**: Enter index.html
   - **_Error document_**: Enter error.html

   <img src = "https://github.com/user-attachments/assets/9420a7c7-e6c6-45b3-9e2c-ebdcf566d25d" width = "400">

6. Now I choose to **_Save changes_**, which takes me back to the bucket home page.
7. In the **_Static website hosting_** panel a link is provided under **_Bucket website endpoint_**. Clicking on the link redirects to a 403 Forbidden message as the bucket permissions are not yet configured.

   <img src = "https://github.com/user-attachments/assets/dde1b430-2182-47d5-a45b-35560cf4b245" width = "400">

## Task C: Uploading content to bucket. 
1. Navigate to the **_Objects tab_** and choose to **_Upload_** and then **_Add files_**.
   
   <img src = "https://github.com/user-attachments/assets/a3e2e716-8e41-433f-b5ee-b5ae96aa350b" width = "400">

   <img src = "https://github.com/user-attachments/assets/06b7290d-74fb-4b07-927b-748008bad409" width = "400">

3. I then select to upload the files **_inde.html, script.js_** and **_style.css_** from my PC and then choose **_Open._**
   
   <img src ="https://github.com/user-attachments/assets/2af274b3-0106-4406-ab94-4f1f8680466f" width = "400">
5. Finally I choose **_Upload_**.
   
   <img src = "https://github.com/user-attachments/assets/25dd7703-ebc3-446b-a460-01539e854f3b" width = "400">

## Task D: Public access to objects. 
Next I have to allow public access to the objects so that the error 403 does not occur. Amazon S3 objects can be made public in two different ways:
- Make either a whole bucket public or a specific directory in a bucket public using a bucket policy.
- To make individual objects in a bucket public using an ACL.

The safer options is to make individual objects public to avoid accidentally other objects public. Or I could make the entire bucket safe to allow public access.

1. Under the **_Objects_** tab, I choose the **_Name_** checkbox and select the three uploaded objects.
3. In the **_Actions_** menu, I select the **_Make public using ACL_**.
   
   <img src = "https://github.com/user-attachments/assets/902b2705-e0b3-4028-a5bd-f392bbdf9a74" width = "400">
5. A list of the selected objects is displayed and I select the **_Make public_**.
   
   <img src = "https://github.com/user-attachments/assets/300c3d94-54d0-424b-afe2-84ea788ce865" width = "400">
7. The static website is now accessible to the public and visible.
   
   <img src = "https://github.com/user-attachments/assets/0ddb23f7-3835-4c60-a745-4ffacc37f1bc" width = "400">

## Task E: Secure sharing of object using a presigned URL.
I can create a URL to temporarily and securely share an object with a person or group of people without making it public. It is important to propely configure the duration of the validitiy of the URL. 

1. In the **_Objects_** tab choose **_Upload_**
2. Choose **_Add files_**    
3. Choose the file (**_new-report_**) and choose **_Open_**.
   
   <img src= "https://github.com/user-attachments/assets/fc572ffb-3a1a-45cb-941b-ed17a0a0ec12" width = "400">
   
4. Choose **_Upload_** after the file shows up on the files and folders list.

   <img src = "https://github.com/user-attachments/assets/a2d2a865-b1d3-441b-878a-9d2ae11139be" width = "500">

The uploaded file is private by default. The presigned URL provides access to the file without having to make it public. 

5. In the **_Objects_** tab, choose the file. (**_new-report_**)
6. From the **_Actions_** menu select the **_Share with a presinged URL_**
   
   <img src = "https://github.com/user-attachments/assets/66a17898-0140-4d16-a214-7e91281be7da" width = "500">
   
7. A pop-up window will show up, I keep the default minutes for the **_Time interval until the presigned URL expires_**. This can be changed to hours if needed.
8. For the number of minutes I will set as 2 and choose **_Create presinged URL._**

   <img src = "https://github.com/user-attachments/assets/1589b5e9-e63d-44b9-add5-66b7f1bc03e2" width = "500">

   A notification banner with the prsigned URL will be shown.

   <img src = "https://github.com/user-attachments/assets/2fffd92e-1e45-40c4-a6d8-7abb3bc8d7f9" widht = "250">
   
10. I will use the URL and access the **_new-report.png_** file in a a new tab.

    <img src = "https://github.com/user-attachments/assets/71d2a188-0782-4d3c-bb01-b68579eed4db" widht = "400">

11. Since the URL expiry time was set to 2 mins, when the page is refreshed after 2 mins, an Acess denied page is shown.

## Task F: Bucket Policy for security. 

    

