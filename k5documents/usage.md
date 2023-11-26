# Usage

---

## Templates

By default, no job can create documents. This script's main goal was to eliminate the need to edit the configuration to create new type of documents as a server developer.

?> Players in the specified job and job grade can create templates for that job.

In this example, we will create a parking ticket template for the `police` job.

1. Open the documents panel and navigate to the `Templates` menu. Make sure you've set your job and job grade properly.
   ![Template menu](https://i.imgur.com/O59KR8M.png)
2. Click on the `New Template` button. Here you can provide the information about this document type.
   ![New template](https://i.imgur.com/hYVx5H1.png)

| Field                    | Usage                                                                                                                                                        |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Document name**        | This is the name of the template. This will show up in the document selection menu                                                                           |
| **Document description** | This is the description section. Keep it short to provide space for the document creator's data                                                              |
| **Fields**               | These fields will be fillable when someone creates this document. Here you add the **name of the field** and not the value<br />**Example**: _Date of birth_ |
| **Information title**    | This is the title if the information section                                                                                                                 |
| **Information template** | This is the default value of the information section                                                                                                         |
| **Minimum job grade**    | This is the first job grade that can create this type of document section                                                                                    |

3. This is the result of creating the template
   ![Filled template](https://i.imgur.com/ZrKHFaV.png)
4. After clicking `Create template` everyone who's at least in job grade 2 will be able to create a _Parking ticket_ document.
5. To issue a new document, go to the `Issued documents` and click on `New Document`
   ![Template select](https://i.imgur.com/4BbJedA.png)
6. Select the _Parking ticket_ option and here you can see our newly created document type.
   ![New document](https://i.imgur.com/qkNCzX7.png)
7. Players with the specified job grades can always edit the document templates.

   !> **Note that previously created documents will not update!**

## Server event

The script provides a server event, with which you can programmatically create document to players

!> The event must be called on the **client side**

```lua
TriggerServerEvent('k5_documents:createServerDocument', {
    name = "Vehicle Purchase Document",
    description = "This is an official purchase document",
    fields = {
        {
            name = "Firstname",
            value = result.firstname
        },
        {
            name = "Lastname",
            value = result.lastname
        },
        {
            name = "Vehicle Type",
            value = GetDisplayNameFromVehicleModel(GetHashKey(vehicleData.model))
        },
        {
            name = "Plate Number",
            value = generatedPlate
        }
    },
    infoName = "INFORMATION",
    infoValue = "This vehicle was purchased by ".. result.firstname .. " " .. result.lastname .. ".\nThis paper is an official document that proves the original owner of the vehicle.",
    isCopy = true,
    issuer = {
        firstname = "Simeon",
        lastname = "Yetarian",
        birthDate = "1954. 05. 26.",
        jobName = "Dealership Owner"
    }
})
```
