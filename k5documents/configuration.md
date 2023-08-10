# Configuration

---

## LUA configuration

The lua section provides the basics of the script. More complex configurations can be found in the [JavaScript](#javascript-configuration) section.

> Open the `config.lua` file in the root folder

| Variable                    | Usage                                                                                                                                                                                                  |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Config.**Command**          | The command the players can open the documents panel with.<br />Set to `nil` if you don't want players to use the command<br /><br />**Example**: `"documents"`                                        |
| Config.**RegisterKey**      | The key the players can open the documents panel.<br />Set to `nil` if you don't want players to use a key.<br />It will not work if **Config.Command** is set to `nil` <br /><br />**Example**: `"k"` |
| Config.**DocumentItemName** | The name of the item you want to open the documents panel.<br />Set to `nil` if you don't want players to use an item.<br /><br />**Example**: `"wallet"`                                              |
| Config.**PaperProp**        | The name and rotation of the prop to be used when accessing the documents panel.<br />Don't change anything if it works fine on your server.                                                           |
| Config.**Locale**           | Localizaition table. Feel free to translate the texts to your own language.                                                                                                                            |

## JavaScript configuration

?> All JavaScript configurations can be found in the `web/build/config.js` file. Open that file in an editor.

### Set up jobs

Your file should look something like this. Here we've defined 3 different jobs that can create documents.

```js
const AVAILABLE_JOBS = [
  {
    job: 'police',
    templateGrades: [3, 4],
    logo: 'https://i.imgur.com/YsTyMCc.png',
  },
  {
    job: 'ambulance',
    templateGrades: [3],
    logo: 'https://i.pinimg.com/564x/6b/88/4f/6b884f7ebe28ff56a0e1fd9f5c47890a.jpg',
  },
  {
    job: 'mechanic',
    templateGrades: [4],
    logo: '/web/build/mechaniclogo.jpg',
  },
]
```

| Variable            | Usage                                                                                                                                                                                                     |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **_job_**           | The name of the job that can acces the document creation menu                                                                                                                                             |
| **_templateGrade_** | Here you can define the job grades that can access the template creation menu.<br />**Example**: `[1, 5]`                                                                                                 |
| **_logo_**          | The link of the logo that will be printed on the documents this job create<br />As you can see in the example, it can be an external URL, or you can provide a local file. Make sure the path is correct. |

### Citizen templates

Here you can define default document template that can be accessed by anyone.

!> If you don't want any citizen templates, delete everything inside the `[]` like this: `const CITIZEN_TEMPLATES = []`

Here's our default citizen document template:

```js
{
    id: 'citizen_contract',
    documentName: 'Citizen Contract',
    documnetDescription:
      'This is a document between two citizens of Los Santos. This document is an official legal document.',
    fields: [
      {
        name: 'Firstname',
        value: '',
      },
      {
        name: 'Lastname',
        value: '',
      },
      {
        name: 'Valid Until',
        value: '',
      },
    ],
    infoName: 'INFORMATION',
    infoTemplate: '',
  }
```

| Variable                  | Usage                                                                                                                                                                                            |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **_id_**                  | A unique id for this template                                                                                                                                                                    |
| **_documentName_**        | Name of the document header                                                                                                                                                                      |
| **_documnetDescription_** | The description of the document                                                                                                                                                                  |
| **_fields_**              | The fields the player has to fill when creating a document.<br />`name` is the label of the field.<br />`value` is the default value of that field. <br />You can create up to **6 fields max**. |
| **_infoName_**            | Title of the information section                                                                                                                                                                 |
| **_infoTemplate_**        | Default value of the information section                                                                                                                                                         |

### Colors

You can customize the appearance of the documents panel with these colors. Currently only light mode is supported.

| Variable                 | Usage                                       |
| ------------------------ | ------------------------------------------- |
| **_primary_**            | The color of buttons, and highlighted texts |
| **_secondary_**          | The color secondary emelents on the page    |
| **_menuGradientBottom_** | Bottom color of the sidebar menu            |
| **_menuGradientTop_**    | Top color of the sidebar menu               |

### Localization

In the `TEXTS` object, you can find the different localizations for the documents panel. Most texts can be found here.

?> Currently the table's pagination and header texts are not translatable.
