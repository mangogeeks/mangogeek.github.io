---
layout: post 
title: "Technical Content Layout"
---



# Modules Status

- [x]  [0. Deployment](https://support.hycu.com/hc/en-us/articles/360014291939-0-Deployment)
- [x]  [1. Adding Sources](https://support.hycu.com/hc/en-us/articles/360014223760-1-Adding-Sources)
- [x]  [2. Backup&Restore](https://support.hycu.com/hc/en-us/articles/360014224980-2-Backup-Restore)
- [x]  [3. Archiving](https://support.hycu.com/hc/en-us/articles/360014294379-3-Archiving)
- [x]  [4. Backup From Replica](https://support.hycu.com/hc/en-us/articles/360014237980-4-Backup-From-Replica)
- [x]  [5. Nutanix Files Backup and Recovery](https://support.hycu.com/hc/en-us/articles/360014239960-5-Nutanix-Files-Backup-and-Recovery)
- [x]  [6. Applications](https://support.hycu.com/hc/en-us/articles/360014308859-6-Applications)
- [x]  [7. Physical](https://support.hycu.com/hc/en-us/articles/360014319859-7-Physical)
- [x]  [8. Self-service](https://support.hycu.com/hc/en-us/articles/360014264600-8-Self-service)
- [x]  [9. Reporting](https://support.hycu.com/hc/en-us/articles/360014333359-9-Reporting)

---

# Observation

## 1. Deployment

- Since we have a note that in HYCU assigned environment HYCU controller is pre deployed but since this module is specific to deployment so it's relevant to Non HYCU environment.
- We should ask Audience to go over the documentation to follow the steps.
    - For instance, *“Uploading the HYCU virtual appliance image to a Nutanix AHV cluster”* from the user guide.
    
    ![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled.png)
    

<aside>
🚫 While Going over Module 2, I noticed similar feedback from one of the users. A lot of users are testing or going over labs on Nutanix CE or VMware labs. 👇

                                                                 ⬇️ 

</aside>

![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%201.png)

## **2. Ordering of Key concepts: -**

- HYCU Terminology and concepts section needs to Cover all option in the left panel and should be in the same order as in the dashboard.  The following example is one of the samples but noticed this for all the captured workflows.
    
    
    ![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%202.png)
    
    ![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%203.png)
    

---

- Another Example, Target creation workflow. Where the first page only has following options to be entered:
    - *Name,*
    - *Description (That’s optional),*
    - *Concurrent Backups,*
    - *Use for Archiving,*
    - *Enable compression.*

![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%204.png)

![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%205.png)

<aside>
💡 I have a personal feeling that UI layout has changed since the docs (workflow documentation) was created.

</aside>

## 3. Observation (Could be an issue)

- When we have default policy as "Exclude" ideally it should be applied to all VM’s. But it didn’t happen.
    - I waited for an hour and then manually assigned the exclude policy to them.
- However, when I tested it again, I noticed the same behavior. Created a VM and didn’t assign it any policy.
- This is what been observed ⬇️

![                                                                    Expected Behavior ](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%206.png)

                                                                    Expected Behavior 

![                        Default Policy is set to Exclude. ](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%207.png)

                        Default Policy is set to Exclude. 

---

![           Cloned VM isn’t part of this policy yet. ](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%208.png)

           Cloned VM isn’t part of this policy yet. 

## 4. Some Key Observations (Improvement)

- Advanced Backup configuration needs to be explained together for the “**Enabled Options”**.
    - It may be a bit confusing for end users.
- Wherever possible we can use **acli** workflow to create a VM (this may help to shorten the learning curve and documentation).
- We can also cover the reasoning for any points covered outside of the HYCU workflow like *“why AHV attached SCSI (VG) disk doesn't need to be explicitly discovered”*.

# Learnings Captured

- For Non-HYCU users, we need to cover the deployment workflow.
- Need to explain the options layout the same as in HYCU Portal.
- The UI workflow has changed since the doc was created so the articles must be revamped. In General, this whole workflow needs to be addressed.
- The Backup and Restoration workflow must be improved so it's easy to understand and we cover all available options (F*or later as an advanced training guide*)
- **Rough Sketch of new workflow**
    
    ## New Format of Articles
    
    ![Article_Framework.jpg](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Article_Framework.jpg)
    

[Technical Content Structure](https://www.notion.so/Technical-Content-Structure-8d8b1e59509f4742b089120ee7a62de3?pvs=21) 

---

# Chapters Review (From 3 onwards)

## Archiving

This section in [3. Archiving](https://support.hycu.com/hc/en-us/articles/360014294379-3-Archiving) needs correction since the backup starts immediately but the Archival Starts at the specified time.  I specified Archival to start at 12:00 PM as expected.

![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%209.png)

## Back from Replica

![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2010.png)

In Chapter [4. Backup From Replica](https://support.hycu.com/hc/en-us/articles/360014237980-4-Backup-From-Replica) following points were noticed:

- Backup from replica doesn't support pre and postscript. This information is missing in the article.
- *HYCU has found the snapshot replica in the Protection domain on the central HYCU cluster ntnx-robo. —>* This seems to be a mistake and instead of ntnx-robo, it should have been ntnx-prod where the replicated snapshot was found.
- Also noticed another glitch there is no container named *ntnx-prod/HYCUWorkshops.* This container exists on *ntnx-robo/HYCUWorkshops*. Might confuse users.

![As per the doc ](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2011.png)

As per the doc 

![  This is what we see in the lab](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2012.png)

  This is what we see in the lab

<aside>
🚫 Potential UI improvement: - We can reflect certain tags to reflect the grouping.

</aside>

- UI Glitch

![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2013.png)

<aside>
🚫 In the lab what option we should stick to while displaying the restore operation?

</aside>

## Nutanix Files Backup and Recovery

In chapter [5. Nutanix Files Backup and Recovery](https://support.hycu.com/hc/en-us/articles/360014239960-5-Nutanix-Files-Backup-and-Recovery)

- Minor UI Glitch

![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2014.png)

- **From HYCU left panel go to Jobs and notice that two new jobs are started. Add Nutanix Files source job will check all connections with Nutanix and synchronize the File shares to HYCU Shares view.**
    - The important thing to notice is that in the lab we don't have any HYCU instance running on Nutanix cluster where the Files cluster is running so we may highlight this option and the reason behind it. Though this has been explained later but this may catch users by surprise.
        - Before asking users to proceed with the Instance creation steps.
            
            ![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2015.png)
            

<aside>
🚫 Issue with Instances workflow. The VM was not deleted though the instance was deleted (P4). How long does it take for stale entries to be removed?

</aside>

> A default policy was applied to newly discovered shares.
> 
- **Files Restoration process**
    - The File restoration process has changed a bit.  Also restore ACL option only applicable to SMB Shares. When Source and Target both are SMB.  Since our example, the target is NFS this option will not work.
    - Export Share option as explained in the doc is no longer applicable instead following way is the approach
        
        ![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2016.png)
        
    

## Applications

- In chapter [6. Applications](https://support.hycu.com/hc/en-us/articles/360014308859-6-Applications) We have talked about pre- and post-backup script and their usage. We can provide more insight into this topic or redirect users to the page where the information persists.
- The reason we only do incremental backup for SQL (App consistent) is that we have already performed a full back up at the VM level.

![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2017.png)

<aside>
📌 **Lab Improvement** In the module Archiving we used the VM WorkshopSQL01 and then the same one for the Application module WorkshopSQL01. Instead, we can dedicate another VM for Archival Manual.

</aside>

![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2018.png)

![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2019.png)

> I need to test SQL Backups in-depth and will plan the scenarios mentioned in the Article based on possibility and identifying the efforts needed to achieve it.
> 

## Physical

- In chapter [7. Physical](https://support.hycu.com/hc/en-us/articles/360014319859-7-Physical), it’s been mentioned that we don’t support Hyper-V hypervisor & we are treating the Hyper-V VM as Physical Servers. How about Xen/Qemu environments?
Any VM added as a physical will behave the same.
    
    ![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2020.png)
    
- This solves one of the P2V migration solutions where VirtIO drivers can be installed before performing the backup ( A beautiful use case)

## Self-service

- *Please login to HYCU as the admin user. :-* However, the user is already part of the infrastructure group so we should not ask users to log in as admin
- The UI workflow is a bit confusing so we can improve it. Some of the instructions are not in place. I’ll have to test the User configuration part one more time and ask specific questions.

<aside>
🚫 **~~UI/UX Improvement:-** Owner Radio Button should be at the same location. For shares, it is at the top but for VM it's at the bottom.~~

</aside>

---

## Suggestions

- ~~Suggestions to improve Our User Guide Searchability and accessibility~~
    - ~~Break the Titles into their own HTML format. Right now it’s all PDF format and difficult to follow or search specific section~~
    - ~~Apart from PDF, we should have an HTML view of the document. For instance, we can look at the Nutanix Files Guide. [Files 4.2 - Nutanix Files User Guide](https://portal.nutanix.com/page/documents/details?targetId=Files-v4_2:Files-v4_2)~~
        - ~~This helps in searchability, especially by leveraging meta (JSON tagging)~~
- I’ll sync up with Alexander to check if we can leverage another VM to showcase the Archival workflow instead of the SQL VM that will be used for the Application workflow.
- In the Articles, I’ll try to capture the workflow depicted in Jobs in a graphical format to just give an overview. The following piece is just an example

![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2021.png)

## Questions

- Let's learn more about the **enabled options category** and when to choose what. This can help me to explain the topic.
    
    ![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2022.png)
    
- Concept of New Backup Chain.
- The advantage of using an SMB type of target is that the backup data is
getting copied directly from the physical server to the respective SMB target, not going through the HYCU VM. **Isn't this statement true about NFS Targets as well? And if not then why?**
- Key Difference between **Archival** and **Backup** (I understand the use case)
- We have explained a bit about Pre and Postscript for snapshots and backup (doesn’t work on replica backup). Should we explain a bit more with a use case?

---

## ****Maintenance****

- We missed specifying the VM that is going to be used and the logic of filters must be explained. As searching for full backup instances for expiration can be a tedious task.
- ❓Also, specify the way to check the Backup chain. For instance, For Nutanix snapshots the Maximum snapshot chain height is 38.
- This piece of information can be added in the notes section.

![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2023.png)

## ****HYCU Protégé - Migrating a VM to Cloud****

- For labs, we have preconfigured cloud Accounts because it’s easy to proceed but someone trying to test this feature on their own might have a challenging time figuring this out.
- 📝In the article, we are asking users to configure it. I’ll get more clarity from Alexander, if this is true in all cases then in this case, we can provide more details. @pikuma
    
    ![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2024.png)
    
    ![Untitled](technical-enablement-content-review%202e7ab9462034425784932b86892cbc03/Untitled%2025.png)
    

- 📝Spend more time understanding the **Prerequisites for lift and shift to GCP and try it myself @pikuma**
- Elaborate on the steps needed as **“Prerequisite”** before the **Spin up to Cloud** Activity.
- Couldn’t find Virtual Machine type “custom -1-1024-ext” while attempting to migrate application to the cloud.
- There is a request for a similar doc with Azure as well. @pikuma
