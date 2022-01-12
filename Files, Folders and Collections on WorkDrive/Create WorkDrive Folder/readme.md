# Create WorkDrive Folders

This function will help you create folders on WorkDrive.

# Instructions
### Creating Connection
1. Go to **Settings** > **Connections**
2. Search for **Zoho OAuth**
3. Create a connection named `crm`
4. Authenticate the connection 

### Creating Function
1. Go to **Settings** > **Functions**
2. Click on **Create Function**
3. Enter a Function Name **ABRCreateWorkDriveFolder**
4. Enter a Display Name **ABR Create WorkDrive Folder**
5. Enter a description (optional)
6. Select **Standalone**
7. In the editor, copy an paste the content of file [creatingFile.dg](www.google.com) inside the editor
8. On the top, click on **Add Arguments**
9. Enter the arguments as follows:
 
| Argument | Type |
|--|--|
| parent_folder_id | string |
| folder_name | string |
 
 10. Click on **Save**


# How to use it?
Once the function is created your can use this functions inside other functions following these examples:

### Example 1: Single Folder
    // Creating a folder for a deal
    
    template_id = "oeiuuo2iueituoeiuoweirgt6854dt";
    
    deal = zoho.crm.getRecordById("Deals", 39839839849389);
    
    folder_name = deal.get("Deal_Name") + " - " + zoho.currentdate;
    
    // Here the folder is created
    folder = standalone.ABRCreateFolder(parent_folder, folder_name).toMap();
    
    // Here we print the folder id
    info folder.get("id");
  

 ### Example 2: Nested Folder

    // Creating a folder for a deal
    
    template_id = "oeiuuo2iueituoeiuoweirgt6854dt";
    parentfolder_id = "oeiuuo2iueituoeiuoweirgt6854dt";
    
    deal = zoho.crm.getRecordById("Deals", 39839839849389);
    
    folder_name = deal.get("Deal_Name") + " - " + zoho.currentdate;
    
    // Here the folder is created
    folder = standalone.ABRCreateFolder(parentfolder_id, folder_name).toMap();
    
    subfolder_name = "Internal";
    
    // Here the subfolder is created
    subfolder_name = standalone.ABRCreateFolder(folder.get("id"), subfolder_name).toMap();


# Limitations

 - Folder name must not contain special characters
 - Connection must be created by admin

# Related Links

 - [Upload attachments to WorkDrive](www.google.com)
 - [Check if folder exists on WorkDrive](www.google.com)
