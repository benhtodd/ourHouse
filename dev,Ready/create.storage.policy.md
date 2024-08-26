1\. Task description and objectives
-----------------------------------

Add text

2\. Create a Storage Policy
---------------------------

### 2.1. Login to vSphere client

![mRemoteNG - confCons.xml - vcf-5.2-no-tanzu](images/ba96cb3c-8a59-4997-ba80-aa762044d777.png)

Open Chrome

Open the Livefire Labs Bookmarkl Folder

Choose --> **MGMT WLD** --> **vCenter**

![mRemoteNG - confCons.xml - vcf-5.2-no-tanzu](images/f899fdca-6e1c-43ae-894f-aee158c2dd9e.png)

Login Using  
User:

    Administrator@vsphere.local

Click to copy

Password:

    VMware123!VMware123!

Click to copy

### 2.2. Create a Storage Policy

You need to create a storage policy before the Supervisor deployment. It is going to be used for Supervisor hosted Applications and Services.

Before creating the **storage policy**, you need to create a custom **tag** and **category,** then tag your Datastore with the new tag. The policy then uses these tags as part of it's usage rule.

When logged in the vSphere client UI:

![](images/cc7b9435-b260-480d-ba69-5cce4631e3f9.png)

Click on the hamburger (elipsis) menu in the top left corner

Select **Tags & Custom Attributes**

![](images/7e2889b6-3bee-447d-aaf9-868785b6bae9.png)

To create a new Category:

Under **Tags & Custom Attributes**,

Select **Tags**, then **CATEGORIES** --> **NEW**

[![](https://media.screensteps.com/image_assets/assets/008/688/305/medium/0786cfa4-817a-4f59-a783-6013ec6711c6.png)](images/0786cfa4-817a-4f59-a783-6013ec6711c6.png)

In the **Create Category** wizard enter as following:

**Category Name:**

    vsphere-with-tanzu-category

Click to copy

**Tags Per Object:**

    One Tag

Click to copy

**Associable Object Types:**

    Datastore

Click to copy

Confirm with **CREATE**

[![mRemoteNG - confCons.xml - vcf-5.2-tanzu.1.3](https://media.screensteps.com/image_assets/assets/008/657/304/medium/1ed374b2-2548-482e-b1c9-bd87db098ed9.png)](images/1ed374b2-2548-482e-b1c9-bd87db098ed9.png)

You will see your Category created.

Let's continue with creating a **Tag** that is bound under this **Category**.

![](images/1446c4cf-8730-4b0f-8afa-bfa794f3358a.png)

To create a new **Tag**:

Under **Tags & Custom Attributes**,

Select **Tags**, then again **TAGS** --> **NEW**

![mRemoteNG - confCons.xml - vcf-5.2-no-tanzu](images/036573ca-d774-4202-b426-52fba9a408f1.png)

In the **Create Tag** wizard enter as following:

**Name:**

    vsphere-with-tanzu-tag

Click to copy

Category: vsphere-with-tanzu-category (from the drop-down)

Confirm with **CREATE**

[![](https://media.screensteps.com/image_assets/assets/008/657/346/medium/af4c18ba-0bc7-4823-9010-afcc47cebfad.png)](images/af4c18ba-0bc7-4823-9010-afcc47cebfad.png)

You will see your Tag created and related to the specified Category you created earlier.

Let's continue with applying this Tag on the vSAN Datastore

![](images/d16ba009-7f12-4397-83e6-95fdb0299482.png)

Click on the hamburger (elipsis) menu in the top left corner

Select Inventory

[![](https://media.screensteps.com/image_assets/assets/008/655/562/medium/4ba4c514-77ec-46b5-8779-0c3a60a093d3.png)](images/4ba4c514-77ec-46b5-8779-0c3a60a093d3.png)

In the Inventory menu:

Select the **Storage** section, Expand the vCenter, Expand the Datacenter

Select the **vcf-vsan** Datastore, right click on it and select **Tags & Custom Attributes**

Expand it and select **Assign Tag**

[![](https://media.screensteps.com/image_assets/assets/008/657/348/medium/ea041b03-30b6-409b-87a3-1077070a83c7.png)](images/ea041b03-30b6-409b-87a3-1077070a83c7.png)

In the **Assign Tag wizard**

Select the **vsphere-with-tanzu-tag** you created earlier

Confirm with **ASSIGN**

Now you can configure a relevant **storage policy**, working with **tag based placement** of the objects, over the **vcf-vsan** Datastore.

![](images/750bf9a2-c42d-4c28-992c-b506c1a44344.png)

Click on the hamburger menu in the top left corner

Select **Policies and Profiles**

![](images/90f41c42-acc0-461c-8dc6-9a6c5913fe7e.png)

Under **VM Storage Policies**

Select **VM Storage Policies** --> **CREATE**

[![](https://media.screensteps.com/image_assets/assets/008/655/570/medium/88509219-0cea-4539-842f-6b13ed2086c4.png)](images/88509219-0cea-4539-842f-6b13ed2086c4.png)

In the **Create VM Storage Policy** wizard,

For **Name and description** enter as following:

    vsan-tanzu-storage

Click to copy

Confirm with **NEXT**

[![](https://media.screensteps.com/image_assets/assets/008/655/572/medium/35f9f0fd-b877-444b-b6e4-6edb10a180f1.png)](images/35f9f0fd-b877-444b-b6e4-6edb10a180f1.png)

For **Policy structur**e**,** under **Datastore specific rules**,

Select **Enable tag based placement rules**

Confirm with **NEXT**

[![](https://media.screensteps.com/image_assets/assets/008/657/350/medium/3930ecbd-9393-45e8-a80b-b8c8cc138209.png)](images/3930ecbd-9393-45e8-a80b-b8c8cc138209.png)

For **Tag Based Placement** **,** under **Rule 1**,

Enter the following:

    Tag category: vsphere-with-tanzu-category
    Usage option: Use storage tagged with
    Tags: vsphere-with-tanzu-tag

Click to copy

You can select the **tanzu-tag** clicking on **BROWSE TAGS**

![](images/3df598f3-a0ae-49ba-89e8-23db3344925e.png)

In the **Add tags** wizzard,

Select your **vsphere-with-tanzu-tag** and confirm with **OK**

[![](https://media.screensteps.com/image_assets/assets/008/657/354/medium/319a7b5b-4be7-4039-8fee-d1515d081a9f.png)](images/319a7b5b-4be7-4039-8fee-d1515d081a9f.png)

You can see and the needed values for Tag Category and Tags are in place.

Confirm with **NEXT**

[![](https://media.screensteps.com/image_assets/assets/008/655/602/medium/0347d208-cc15-4f8d-be34-e81449aff805.png)](images/0347d208-cc15-4f8d-be34-e81449aff805.png)

For **Storage Compatibility,** under **COMPATIBLE**,

you can see the listed **vcf-vsan** Datastore.

Confirm with **NEXT**

[![](https://media.screensteps.com/image_assets/assets/008/657/356/medium/6acbff7d-add5-4d59-8e26-37c5bef44deb.png)](images/6acbff7d-add5-4d59-8e26-37c5bef44deb.png)

For Review and finish you can see the configured properties in your new storage policy.

Confirm with **FINISH**
