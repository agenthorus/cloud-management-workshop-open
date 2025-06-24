# WorkFlow - Build Windows Private/Public Cloud

## Objective

To enable end to end provisioning process automation on any cloud, in consistent approach, for Windows instances


## Return to Menu

 - [Menu of Exercises](../README.md)

## Summary of steps
    
1. Create AAP Job Templates to Build  and End to End Workflow in AAP
2. re-use the created Job Templates to Create an Automation Workflow
3. Build the workflow with Happy/Exception path logic (yes with ServiceNow Integration)

---


### Step 1 - Create Job Template in AAP (SNOW) - Skip if Already Done 

Create a new Job Template with the following parameters:

* name: SNOW - Raise INC
* organization: *\<your username\>*
* Inventory: localhost
* project: Workshop Repo
* Execution environment: Default Execution Environment
* Playbook: playbooks/snow-create-inc.yml
* Credential: 
  * ServiceNow Credentials
  * Workshop Vault Credential


    Save Template. Should look like the below 
    ![alt text](image.png)

---


### Step 2 - Create Job Template in AAP (AAP - Init Workflow) - Skip if Already Done 

Create a new Job Template with the following parameters:

* name: AAP - Init Workflow
* organization: *\<your username\>*
* Inventory: localhost
* project: Workshop Repo
* Execution environment: Default Execution Environment
* Playbook: playbooks/soe-workflow-init.yml
* Credential: 
  * AAP Credentials
  * Workshop Vault Credential


    Save Template. Should look like the below 


    ![alt text](image-3.png)

---

### Step 3 - Create Workflow Job Template WFJT in AAP for Win on AWS

Create a new Workflow Job Template with the following parameters:

  ![alt text](image.png)

* name: WFJT - Provision Win on AWS Cloud
* organization: *\<your username\>*
* Extra variables (Do not forget to you your username provided)
    ```yaml
    v_instance_count: 1
    student_name: mina
    aws_host_os: win2022
    ```
*  *Notice that now we are moving all extra vars to Workflow Level to have highest precedence .. and notice how we will leverage `prompt_on_launch` that we set on some JTs so we can re-use our automation code*

  Save Template. Once Saved, Click on the Workflow Visualiser 

  ![alt text](image-1.png)


 Create the Nodes and Arrange them to look like the following (Guidance on the Main screen)



![alt text](image-2.png)

---

### Step 4 - RUN The the Workflow Job Template WFJT (WFJT - Provision WIN on AWS Cloud)


