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
2. Choose **_Create bucket._** **Bucket names have to be globally unique. All AWS accounts share the namespace.**
3. For this instance we use the name **sim-website**
   <img src = "https://github.com/user-attachments/assets/2a814573-37d3-4b94-b4c3-e946dd57b2e3" width = "400">
4. For **_Object Ownership_** enable ACLs so we can provide controlled access to the objects.
5. I keep the **_bucket owner preferred_** enabled as only I will be uploading to the the bucket.

   <img src = "https://github.com/user-attachments/assets/b1323f1a-9ec0-4973-8b1b-1253530f2e94" width = "400">
6. Since this is S3 will contain the files for the static website. The files must be accessible through the internet. For this I permit public access by clearing the checkbox for **Block _all_ public access**.
   
   <img src = "https://github.com/user-attachments/assets/45eaf130-aed9-4eef-a0a9-6505759b9900" width = "400">
   
   I have to select the box that acknowledges the settings. 
    
7. For **_Bucket Versioning_** I choose **_Enable_**. It is important to understand that once bucket versioning is enabled, it cannot be turned off.
   
   <img src = "https://github.com/user-attachments/assets/4c5f684b-689d-4390-a0fc-c37effd3528c" width = "400">

8. I choose to **_Add tag_** with the following **key:Department** and **Value:Marketing**.

   <img src = "https://github.com/user-attachments/assets/b1ec02ff-1a8f-4abb-a86f-86406434f8c8" width = "400">

10. After choosing **_Create bucket_**, the new bucket appears in the list.
    <img src = "https://github.com/user-attachments/assets/83ea02a7-31a0-417c-a9ce-df0bf3a28369" width ="400">

## Task B: Static website configuration
