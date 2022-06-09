# Introduction
## Authentication URls

IDP and Base API URLS

### Live

Swagger: [https://api.papercloudelite.co.uk/swagger](https://api.papercloudelite.co.uk/swagger)

Base URL: [https://api.papercloudelite.co.uk/](https://api.papercloudelite.co.uk/)

Auth URL: [https://idp.papercloudelite.co.uk/connect/authorize](https://idp.papercloudelite.co.uk/connect/authorize)

Token URL: [https://idp.papercloudelite.co.uk/connect/token](https://idp.papercloudelite.co.uk/connect/token)

### Sandbox

Swagger: [https://sandboxapi01.papercloudelite.co.uk/swagger](https://sandboxapi01.papercloudelite.co.uk/swagger)

Base URL: [https://sandboxapi01.papercloudelite.co.uk](https://sandboxapi01.papercloudelite.co.uk/)

Auth URL: [https://idpsandbox01.papercloudelite.co.uk/connect/authorize](https://idpsandbox01.papercloudelite.co.uk/connect/authorize)

Token URL: [https://idpsandbox01.papercloudelite.co.uk/connect/token](https://idpsandbox01.papercloudelite.co.uk/connect/token)

## Acceptend Authentication code flows

Papercloud allows the following flows:
Authorisation Code Flow
The Authorization Code grant type is used by web and mobile apps. It differs from most of the other grant types by first requiring the app launch a browser to begin the flow. At a high level, the flow has the following steps:

- The application opens a browser to send the user to the OAuth server
- The user sees the authorization prompt and approves the app’s request
- The user is redirected back to the application with an authorization code in the query string
- The application exchanges the authorization code for an access token

Client Credentials Flow (Tenant)

- Allows you to access web-hosted resources by using the identity of an application. Commonly used for server-to-server interactions that must run in the background, without immediate interaction with a user.
- Watermark do impose limits on opening this access. Any use cases requiring this access will be assessed and functionality will be made available where deemed fit.

## Sandbox Access
Sandbox access can be requested through our support team. This will allow new 3rd parties to gain access to a demo system to trial the API and test the relevant end points.

##Versionning

The current version of the API is V02

V1 is still active, however it will be phased out at the end of 2022.


## Flows examples

A set of flows have been created to detail the core exposed functionality of the Papercloud API. This suite of calls is accessible from &quot;URL ONCE HOSTED&quot;

> - **Flow1 - Creating Clients**
>   - Create Client file with option to apply structure or apply a template
>     - Flow1A - Client Get Client by Reference Number
>     - Flow1B – Cabinet Get All	
>   - Create a client file with no structure (blank)
>     - Flow 1C - Create Client file no structure (blank structure with no template)
>   - Create a client file and define a bespoke structure for tabs. Rows and boxes
>     - Flow 1D - Create Client File with structure
>   - Client Create Client and apply and existing template
>     - Flow1E – Template Get List
>     - Flow 1F - Client Create Client and apply template
> - **Flow 2 - Adding Structure**
>   - Flow2A - Client Apply Template
>     - Flow2B – Add a tab to a client file
>     - Flow2C – Add a Row to a client file
>     - Flow2D - Add a Box to a client file
> - **Flow3 – Add Paperwork to a box**
>   - Flow3A Paper V2 Upload Paper 
> - **Flow4 – Searches**
>   - Flow4A - See All Tabs Rows Boxes For specific client file by ExternalReference
>   - Flow4B - Get a list of all boxes clients that are API accessible that contain the given tag
> - **Flow5 – Viewing, retrieving, and downloading items**
>   - Flow5A - Paper V2 Get Papers For Box
>   - Flow5B - Box Download Box Contents
>   - Flow5C - Paper V2 Download Paper
>   - Flow5D -Paper V2 Download Paper Base64
> - **Flow6 – Jumping to items**
>   - Flow6A - Message Hub Post Jump Itinerary
> - **Flow7 - Deletes**

## Connect config for use with the Sandbox

With WatermarkConnect closed the below file should be placed in the following location:

C:\Program Files\WatermarkTech\WatermarkConnect

NKB NEED FILE


# Generic attributes

These attributes are generic across the API calls.

## Colours

Used for both Tabs and Boxes.

Colour fields accept either the numerical value or the text value.

>- ![#808080](https://via.placeholder.com/15/f03c15/000000?text=+) `Grey = 0`
>- ![#1589F0](https://via.placeholder.com/15/1589F0/000000?text=+) `Blue = 1`
>- ![#7F6000](https://via.placeholder.com/15/f03c15/000000?text=+) `Brown = 2`
>- ![#FFA500](https://via.placeholder.com/15/f03c15/000000?text=+) `Orange = 3`
>- ![#c5f015](https://via.placeholder.com/15/c5f015/000000?text=+) `Green = 4`
>- ![#FFC0CB](https://via.placeholder.com/15/c5f015/000000?text=+) `Pink = 5`
>- ![#800080](https://via.placeholder.com/15/c5f015/000000?text=+) `Purple = 6`
>- ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) `Red = 7`
>- ![#FFFF00](https://via.placeholder.com/15/c5f015/000000?text=+) `Yellow = 8`


## Return codes

200 – indicates success – this will also return in some instances a confirmation of the data stored with some of the post endpoint e.g., if you post a client file the response will include the &quot;ClientFileID&quot; created for the file.

204 – Specifically for deletes, a return with this code indicates success

403 – generally this is a response type indicating something exists but the user does not have access to view\update it. E.g. trying to find a client that resides within a cabinet for which the user does not have access.

## Input Param lengths

These are listed on the Swagger documentation.

## Date format

Dates should be provided in &quot;DD/MM/YYYY&quot; format e.g., &quot;23/02/2001&quot;. There is no time requirement on the API.

## Paper Types

PaperType lookup by extension:

>- &quot;.tif&quot; or &quot;.tiff&quot; : 0
>
>- &quot;.doc&quot;: 1
>
>- &quot;.xls&quot;: 2
>
>- &quot;.txt&quot;: 3
>
>- &quot;.pdf&quot;: 4
>
>- &quot;.msg&quot;: 5
>
>- &quot;.mp3&quot;: 6
>
>- &quot;.ppt&quot;: 7
>
>- &quot;.jpg&quot; or &quot;.jpeg&quot; : 10
>
>- &quot;.docx&quot;: 11
>
>- &quot;.xlsx&quot;: 12
>
>- &quot;.pptx&quot;: 13
>
>- &quot;.wav&quot;: 14
>
>- &quot;.zip&quot;: 15
>
>- &quot;.xlsm&quot;: 16
>
>- &quot;.dmsg&quot;: 17
>
>- &quot;&quot;: 9
>
>- &quot;other&quot; : 8

## UploadItinerary

This is a list of items that can be provided within the calls - the items are optional depending on the required action:

{ “ClientId”:, “TabId”:, “RowId”:, “BoxId”:, “FileInformation”: [{ “FileName”: “”, “CreatedDate”: “”}] }

# Example endpoint calls

## Check if a client exists by external reference

This endpoint confirms if a client already exists. This endpoint has an optional shallow call

This endpoint is demoed via &quot;Flow1A&quot; of the ApiV2FlowGuide.

![clientRef](https://content.watermarktech.co.uk/download/flatdoc/clientRef.JPG "clientRef")

Required Parameters:

- **reference** – this is external unique reference for the client. Typically, the 3rd party&#39;s identification ID.
- **shallow** - when shallow is set to True this will return only contact data for the client file. When set to False – this will return client contact data as well as the structure within the client file (Tabs, Rows and boxes)

Curl Example:

```bash
curl --location --request GET 'https://apihotfix.papercloudelite.co.uk/api/v2/client/ref/JON123?shallow=true' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer eyJhbGci…
```



## Create a client with options to apply structure

These endpoints allow creation of client files within the Papercloud system. Structure can also be applied as part of the creation, which has been shown in the examples. This structure can be a bespoke structure or from existing system templates. 

All calls use the same endpoint:

NKBJPEG HERE

The contents are dynamic, some basic examples have been supplied in the calls laid out within below sections.

An explanation of all fields is found here, this version is for client type &quot;Person&quot;:

NKB IMAGE???

```json
{
  "clientType": "Person",--defines if the client is either a “Person” or “other” (Company)
  "notes": "string", --OPTIONAL (Any entry is displayed within the client file)
  "primaryContactExternalReference": "string", --OPTIONAL though advised (created a link between 3rd party system and Papercloud via the unique identifier from the 3rd party)
  "primaryContactTitle": "string", --OPTIONAL
  "primaryContactFirstName": "string", --OPTIONAL
  "primaryContactSurname": "string", --OPTIONAL
  "primaryContactDateOfBirth": "2022-05-13", --OPTIONAL
  "primaryContactNINumber": "string", --OPTIONAL
  "secondaryContactExternalReference": "string", --OPTIONAL
  "secondaryContactTitle": "string", --OPTIONAL
  "secondaryContactFirstName": "string", --OPTIONAL
  "secondaryContactSurname": "string", --OPTIONAL
  "secondaryContactDateOfBirth": "2022-05-31", --OPTIONAL
  "secondaryContactNINumber": "string", --OPTIONAL
  "phoneNumber1": "string", --OPTIONAL
  "phoneNumber2": "string", --OPTIONAL
  "phoneNumber3": "string", --OPTIONAL
  "parentFileExternalReference": "string", --OPTIONAL (creates a link to another file)
  "addressLine1": "string", --OPTIONAL
  "addressLine2": "string", --OPTIONAL
  "addressLine3": "string", --OPTIONAL
  "addressLine4": "string", --OPTIONAL
  "addressLine5": "string", --OPTIONAL
  "postcode": "string", --OPTIONAL
  "emails": [ --OPTIONAL (comma separated list of email addresses for the client)
    "string"
  ], 
  "cabinetId": 0, --OPTIONAL (define the cabinet that the client should be placed in – blank\not included creates the client outside of a cabinet)
  "cabinetName": "string", --OPTIONAL
  "cabinetExternalReference": "string", --OPTIONAL
  "templateParameters": { --OPTIONAL (allows you to define and apply a template at create)
    "templateId": 0, --Provide the ID of the template you wish to apply
    "templateTitle": "string",
    "mergeTemplateWithExistingStructure": true –-REQUIRED (do you want to add duplicates or ignore them?)
  }
}

```

Create a file of the type &quot;Other&quot;
```json

{
  "clientType": "Other", --defines if the client is either a “Person” or “other” (Company)
  "fileName": "string", --OPTIONAL (Company\Account name)
  "notes": "string", --OPTIONAL (Any entry is displayed within the client file)
  "primaryContactExternalReference": "string", --OPTIONAL though advised (created a link between 3rd party system and Papercloud via the unique identifier from the 3rd party)
  "phoneNumber1": "string", --OPTIONAL
  "phoneNumber2": "string", --OPTIONAL
  "phoneNumber3": "string", --OPTIONAL
  "addressLine1": "string", --OPTIONAL
  "addressLine2": "string", --OPTIONAL
  "addressLine3": "string", --OPTIONAL
  "addressLine4": "string", --OPTIONAL
  "addressLine5": "string", --OPTIONAL
  "postcode": "string", --OPTIONAL
  "emails": [ --OPTIONAL (comma separated list of email addresses for the client)
    "string"
  ], 
  "cabinetId": 0, --OPTIONAL (define the cabinet that the client should be placed in – blank\not included creates the client outside of a cabinet)
  "cabinetName": "string", --OPTIONAL
  "cabinetExternalReference": "string", --OPTIONAL
  "templateParameters": { --OPTIONAL (allows you to define and apply a template at create)
    "templateId": 0,
    "templateTitle": "string",
    "mergeTemplateWithExistingStructure": true
  }
  
```
To apply structure within this endpoint create the following section can be included within the body, this is fully optional – for a clearer example see XXXXX:

ALSO NEED ROW ORDER asc to desc or other way?
```json

"tabs": [
    {    
      "title": "string", --REQUIRED (the title to be applied to the tab)
      "position": 0, -- OPTIONAL (decide on the position of the tab within the client file)
      "colour": "Grey", --OPTIONAL (
      "rows": [ --OPTIONAL (add rows to the new tab)
        {
          "title": "string", --REQUIRED if adding rows (the title to be applied to the Row)
          "position": 0, --OPTIONAL (order in which the row will be created)
          "boxes": [ --OPTIONAL (add boxes to the row)
            {
              "title": "string", --OPTIONAL
              "notes": "string", --OPTIONAL
              "date": "2022-05-31", --OPTIONAL
              "colour": "Grey", --OPTIONAL
              "deleted": false, --REQUIRED           
              "tagCount": 0, --OPTIONAL
              "tags": [ --OPTIONAL
                "string" –List of comma separated tags to be applied to the box
              ]
            }
          ],
          "notes": "string" –OPTIONAL(row notes)
        }
      ],
    }
  ],


```

### Pre-Requisites\linked items:

- Check if a client exists by external reference
- See cabinets (Flow1B)
- See templates (Flow1E)

## Create client file witout structure

This call will create a client file in Papercloud, but it will not add any Tab, Row or box structure to the file.

In this example we are creating a client file with a partner and placing it within a cabinet.

This endpoint is demoed via &quot;Flow1C&quot; of the ApiV2FlowGuide.

Raw body structure:
```json

{
  "clientType": "Person",
  "notes": "string",
  "primaryContactExternalReference": "string",
  "primaryContactTitle": "string",
  "primaryContactFirstName": "string",
  "primaryContactSurname": "string",
  "primaryContactDateOfBirth": "2022-05-19T14:58:03.982Z",
  "primaryContactNINumber": "string",
  "secondaryContactExternalReference": "string",
  "secondaryContactTitle": "string",
  "secondaryContactFirstName": "string",
  "secondaryContactSurname": "string",
  "secondaryContactDateOfBirth": "2022-05-19T14:58:03.982Z",
  "secondaryContactNINumber": "string",
  "phoneNumber1": "string",
  "phoneNumber2": "string",
  "phoneNumber3": "string",
  "addressLine1": "string",
  "addressLine2": "string",
  "addressLine3": "string",
  "addressLine4": "string",
  "addressLine5": "string",
  "postcode": "string",
  "emails": [
    "string"
  ],
  "cabinetId": 0

```

Curl Example:
```bash

curl --location --request POST 'https://apihotfix.papercloudelite.co.uk/api/v2/client/create' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer eyJhbGci…' \
--data-raw '{
  "clientType": "Person",
  "fileName": "",
  "notes": "Some notes relating to the client file",
  "primaryContactExternalReference": "REF12345",
  "primaryContactTitle": "Mr",
  "primaryContactFirstName": "Mickey",
  "primaryContactSurname": "Mounse",
  "primaryContactDateOfBirth": "2008-10-06",
  "primaryContactNINumber": "NI1234",
  "secondaryContactExternalReference": "REF12346",
  "secondaryContactTitle": "Mrs",
  "secondaryContactFirstName": "Minnie",
  "secondaryContactSurname": "Mouse",
  "secondaryContactDateOfBirth": "1991-04-05",
  "secondaryContactNINumber": "NI12346",
  "phoneNumber1": "01131234567",
  "phoneNumber2": "01131234568",
  "phoneNumber3": "01131234569",
  "addressLine1": "do reprehenderit cillum magna",
  "addressLine2": "anim nulla quis",
  "addressLine3": "cillum in in Ut elit",
  "addressLine4": "fugiat",
  "addressLine5": "sed magna",
  "postcode": "BD18 3ST",
  "emails": [
    "test@test123.com,",
    "Another@1234.com"
  ],
  "cabinetId": 2
}'

```

## Create a client file & apply a template

This call will create a client file in Papercloud and apply a pre created template from the template repository.

This endpoint is demoed via &quot;Flow1F&quot; of the ApiV2FlowGuide.

Raw body structure:
```json

{
  "clientId": 0,
  "clientType": "Person",
  "fileName": "string",
  "notes": "string",
  "primaryContactExternalReference": "string",
  "primaryContactTitle": "string",
  "primaryContactFirstName": "string",
  "primaryContactSurname": "string",
  "primaryContactDateOfBirth": "2022-05-19T14:58:03.982Z",
  "primaryContactNINumber": "string",
  "cabinetId": 0,
  "templateParameters": {
    "templateId": 0,
    "templateTitle": "string",
    "mergeTemplateWithExistingStructure": true
  }
}

```
Curl Example:
```bash

curl --location --request POST 'https://apihotfix.papercloudelite.co.uk/api/v2/client/create' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer eyJhbGc…' \
--data-raw '{
    "clientType": "Person",
    "fileName": "",
    "notes": null,
    "primaryContactExternalReference": "",
    "primaryContactTitle": "Mr",
    "primaryContactFirstName": "Template 7",
    "primaryContactSurname": "Test 7",
    "primaryContactDateOfBirth": null,
    "primaryContactNINumber": "",
    "cabinetId": 1,
    "cabinetName": "Cabinet 1",
       "templateParameters": {
    "templateId": 3,
    "templateTitle": "test",
    "mergeTemplateWithExistingStructure": true
  }
}'

```

## Create a client file & define bespoke structure

This call will create a client file in Papercloud and apply bespoke structure e.g., tabs, rows, and boxes.

This endpoint is demoed via &quot;Flow1D&quot; of the ApiV2FlowGuide.

Within this example the client will be created with the following structure:

> ![John Smith TRB](https://content.watermarktech.co.uk/download/flatdoc/JohnSmithTRB.jpg "johnsmithtrb")

This is the body used to produce the client file:
```json

{
    "clientType": "Person",
    "notes": "Add some notes to the client file",
    "primaryContactExternalReference": "REF123454",
    "primaryContactTitle": "Mr",
    "primaryContactFirstName": "John",
    "primaryContactSurname": "Smith",
    "primaryContactDateOfBirth": "01/02/1985",
    "primaryContactNINumber": "NI1234344",
    "tabs": [
        {
            "title": "Insurance",
            "position": 0,
            "colour": 2,
            "rows": [
                {
                    "title": "T1-R1",
                    "position": 0,
                    "boxes": [
                        {
                            "title": "T1-R1-B1",
                            "tags": [
                                "TAG_12ABC"
                            ]
                        },
                        {
                            "title": "T1-R1-B2"
                        }
                    ]
                },
                {
                    "title": "T1-R2",
                    "position": 0,
                    "boxes": [
                        {
                            "title": "T1-R2-B1"
                        },
                        {
                            "title": "T1-R2-B2"
                        },
                        {
                            "title": "T1-R2-B3"
                        },
                        {
                            "title": "T1-R2-B4"
                        }
                    ]
                }
            ]
        },
        {
            "title": "Forecast",
            "position": 1,
            "colour": 5,
            "rows": [
                {
                    "title": "T2-R1",
                    "position": 0,
                    "boxes": [
                        {
                            "title": "T2-R1-B1"
                        },
                        {
                            "title": "T2-R1-B2"
                        }
                    ]
                },
                {
                    "title": "T2-R2",
                    "position": 0,
                    "boxes": [
                        {
                            "title": "T2-R2-B1"
                        },
                        {
                            "title": "T2-R2-B2",
                            "tags": [
                                "TAG_12ABC",
                                "TAG_34DEF"
                            ]
                        },
                        {
                            "title": "T2-R2-B3"
                        }
                    ]
                }
            ]
        }
    ]
}


```

Curl Example:
```bash

curl --location --request POST 'https://apihotfix.papercloudelite.co.uk/api/v2/client/create' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer eyJhbGciOi…\
--data-raw '{
    "clientType": "Person",
    "fileName": "",
    "notes": null,
    "primaryContactExternalReference": "",
    "primaryContactTitle": "Mr",
    "primaryContactFirstName": "Template 7",
    "primaryContactSurname": "Test 7",
    "primaryContactDateOfBirth": null,
    "primaryContactNINumber": "",
    "tabs": [
        {
            "title": "T1",
            "position": 0,
            "colour": 2,
            "rows": [
                {
                    "title": "T1-R1",
                    "position": 0,
                    "boxes": [
                        {
                            "title": "T1-R1-B1",
                            "tags": [
                                "TAG_12ABC"
                            ]
                        },
                        {
                            "title": "T1-R1-B2"
                        }
                    ]
                },
                {
                    "title": "T1-R2",
                    "position": 0,
                    "boxes": [
                        {
                            "title": "T1-R2-B1"
                        },
                        {
                            "title": "T1-R2-B2"
                        },
                        {
                            "title": "T1-R2-B3"
                        },
                        {
                            "title": "T1-R2-B4"
                        }
                    ]
                }
            ]
        },
        {
            "title": "T2",
            "position": 1,
            "colour": 5,
            "rows": [
                {
                    "title": "T2-R1",
                    "position": 0,
                    "boxes": [
                        {
                            "title": "T2-R1-B1"
                        },
                        {
                            "title": "T2-R1-B2"
                        }
                    ]
                },
                {
                    "title": "T2-R2",
                    "position": 0,
                    "boxes": [
                        {
                            "title": "T2-R2-B1"
                        },
                        {
                            "title": "T2-R2-B2",
                            "tags": [
                                "TAG_12ABC",
                                "TAG_34DEF"
                            ]
                        },
                        {
                            "title": "T2-R2-B3"
                        }
                    ]
                }
            ]
        }
    ],
    "cabinetId": 1,
    "cabinetName": "Cabinet 1"
}'


```

## Jumping to an entity (ClientFile, Tab, Box, Page)

A Jump is simply a means to send some defining data to the API that essentially drives the front end of Papercloud in context of the authenticated user.

This endpoint is demoed via &quot;Flow6A&quot; of the ApiV2FlowGuide.

NKB

This functionality requires vx.x.x.x or later of Connect to be installed on the client machine.

The endpoint to initiate a jump is as follows:

 ![](RackMultipart20220608-1-mjrzu0_html_df1eff0f6933cd60.png)

The Body of this call should contain the following:

```json

{
  "elementType": "",
  "elementId": -12345
}

```
The element types accepted for this call are as follows:


- **ClientFile = 3**

- **Tab = 4**

- **Box = 6**

- **Paper = 7**


The endpoint also allows the jump to be initiated with the use of the ExternalReference, this is done with the following structure:
```json

{
    "elementType": 3,
    "elementId": 0,
    "externalReference": "String"
}

```

The elementId relates to the item that needs to be brought to the attention of the end user of Papercloud.

Curl Example:
```bash

curl --location --request POST 'https://apihotfix.papercloudelite.co.uk/api/messageHub/jump' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer eyJhbGci…'
--data-raw '{
  "elementType": "3",
  "elementId": 6
}'

```
## Download a Paper item by ID

Paper in Papercloud is the individual items contained within a document box. This could be a single image or Office Word Document as examples. This specific call provides the document for download to the caller.

This endpoint is demoed via &quot;Flow5C&quot; and &quot;Flow5D&quot; of the ApiV2FlowGuide.

There are two version of the call, one returns the physical paper item that a user can download to view, e.g., a .docx document that the user could then &quot;Download&quot; in the browser for access. The other allows the return of the paper in Base64 format, this would be useful if the requestion application wanted to display\alter the document within their front-end application.

### File version of download:
NKB
![](RackMultipart20220608-1-mjrzu0_html_cddde0afe3e50468.png)

Required params:

 - **PaperID**

Curl Example:
```bash

curl --location --request GET 'https://apihotfix.papercloudelite.co.uk/api/v2/paper/3892/download' \
--header 'Accept: application/octet-stream' \
--header 'Authorization: Bearer eyJhbGciOiJSUz…'

```
### Base64:
NKB IMAGE
![](RackMultipart20220608-1-mjrzu0_html_f2e5c53b579842a4.png)

Required Parameter:

 - **PaperID**

Curl Example:
```bash

curl --location --request GET 'https://apihotfix.papercloudelite.co.uk/api/v2/paper/3892/downloadBase64' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIs'

```

## Get client files with all Tabs, Rows and Boxes

This endpoint returns the entire structure of a client file.

This endpoint is demoed via &quot;Flow4A&quot; of the ApiV2FlowGuide.
NKB IMAGE
![](RackMultipart20220608-1-mjrzu0_html_ff7f2d4e441f15f9.png)

Required Parameters:

 - **reference** (ExternalReference)
 - **shallow** = false

Curl Example:
```bash

curl --location --request GET 'https://apihotfix.papercloudelite.co.uk/api/v2/client/ref/JON123?shallow=false' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer eyJhbGc…'

```
## Return all paper items within a box

This endpoint returns the contents of a document box.
NKB IMAGE
This endpoint is demoed via &quot;Flow5A&quot; of the ApiV2FlowGuide.

![](RackMultipart20220608-1-mjrzu0_html_46fd3fd3650f53f7.png)

Required Parameters:

 - **id** (boxId)
 - **shallow** = false

Curl Example:
```bash

curl --location --request GET 'https://apihotfix.papercloudelite.co.uk/api/v2/paper/papersForBox/1163' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer eyJhbGciO…'


```
## Download an entire box contents

This endpoint is demoed via &quot;Flow5B&quot; of the ApiV2FlowGuide.
NKB IMAGE
![](RackMultipart20220608-1-mjrzu0_html_2735e8ea484d4a55.png)

Curl Example:
```bash

curl --location --request GET 'https://apihotfix.papercloudelite.co.uk/api/v2/boxes/1234/download?printable=false' \
--header 'Accept: application/octet-stream'
--header 'Authorization: Bearer eyJhbGciO…'

```

## Retrieve items via tag search

This endpoint is demoed via &quot;Flow4B&quot; of the ApiV2FlowGuide.
NKB IMAGE
![](RackMultipart20220608-1-mjrzu0_html_981706a552abea7f.png)

NKB - need example call and response

Body:
```json
{
  "clientId": 0, 
  "tag": "string", --REQUIRED, Comma separated list of tags
  "from": "2022-06-09T07:40:56.450Z", --OPTIONAL – start date of when the tag was applied
  "to": "2022-06-09T07:40:56.450Z", --OPTIONAL – end date of when the tag was applied
  "boxTitle": "string" --OPTIONAL –limit the search by box titles
}
```

Curl Example:
```bash

curl --location --request POST 'https://apihotfix.papercloudelite.co.uk/api/v2/tags/search' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer eyJhbGciO…'
--data-raw '{
    "ClientId": null,
    "Tag": "TAG1",
    "From": null,
    "To": null,
    "BoxTitle": null
}'

```

Responses:

 - 200 – a successful request will return a set of JSON, which can contain multiple items (paper or box items) and their tags e.g.

NKB

```json

[
  {
    "elementId": 0, --This is the tags unique identifier
    "elementType": 0, --This is an internal field and can be ignored
    "elementDate": "2022-05-31T15:47:14.953Z", --This is an internal field and can be ignored

    "clientId": 0, 
    "clientFileName": "string", 
    "tabId": 0, 
    "tabTitle": "string", 
    "rowId": 0, 
    "rowTitle": "string", 
    "boxId": 0, 
    "boxTitle": "string",
    "paperId": 0,
    "paperTitle": "string",
    "pageCount": 0,
    "tagCount": 0
  }
]

```

Example of multiple return items:

NKB SHOW EXAMPLES

## Upload Paper items
NKB TO DO
![](RackMultipart20220608-1-mjrzu0_html_a4476649dbd51e50.png)

Parameters:
NKB CHECK UPLOADITIN
 - **Files** – Required – the File to be sent
 - **UploadItinerary**:
  -- { &quot;ClientId&quot;:, &quot;TabId&quot;:, &quot;RowId&quot;:, &quot;BoxId&quot;:, &quot;FileInformation&quot;: [{ &quot;FileName&quot;: &quot;&quot;, &quot;CreatedDate&quot;: &quot;&quot;}] }

NKB
In terms of the UploadItinerary there are multiple ways to send items

NKB
![](RackMultipart20220608-1-mjrzu0_html_e0a47e0fcc0ddd24.png)

### Body:
```json

{
  "appendToFront": true, --REQUIRED (set the location to either the front\rear of the box)
  "paperBase64String": "string", --REQUIRED (this is the paper item to be stored)
  "thumbnailBase64String": "string", --OPTIONAL (ability to send a thumbnail with the item)
  "filename": "string", --OPTIONAL (filename to be set on the item)
  "filedate": "2022-05-12", --OPTIONAL (todays date is used if not supplied)
  "paperType": "INT", --REQUIRED (see PaperType lookup below)
  "uploadItinerary": { "boxID": “INT” }, --REQUIRED (defines the box that the paper should be placed)


    "uploadItinerary": {
        "boxId": 2351
    },

  "tags": [ --OPTIONAL (define any tags to be added to the item in a comma separated list)
    "string"
  ]
}


```
### PaperType lookup by extension:

>- &quot;.tif&quot; or &quot;.tiff&quot; : 0
>
>- &quot;.doc&quot;: 1
>
>- &quot;.xls&quot;: 2
>
>- &quot;.txt&quot;: 3
>
>- &quot;.pdf&quot;: 4
>
>- &quot;.msg&quot;: 5
>
>- &quot;.mp3&quot;: 6
>
>- &quot;.ppt&quot;: 7
>
>- &quot;.jpg&quot; or &quot;.jpeg&quot; : 10
>
>- &quot;.docx&quot;: 11
>
>- &quot;.xlsx&quot;: 12
>
>- &quot;.pptx&quot;: 13
>
>- &quot;.wav&quot;: 14
>
>- &quot;.zip&quot;: 15
>
>- &quot;.xlsm&quot;: 16
>
>- &quot;.dmsg&quot;: 17
>
>- &quot;&quot;: 9
>
>- &quot;other&quot; : 8


## Send Thumbnails with paper items

This is optional for all items paperwork however this is specifically useful for Office items as server-side thumbnail generation is near impossible due to Office being a client-side application. Any Office documents will be added to the system without thumbnails if this is not supplied. (Note: thumbnails will be applied once the version is updated within PCE via Watermark Connect.)

NKB COME BACK TO

## Paper Deletes

When removing paperwork this is classed as a soft delete. As with Papercloud front end the paperwork will be placed within the relative users recycle bin.
NKB
![](RackMultipart20220608-1-mjrzu0_html_9b0a745efbb9d043.png)

Required Parameters:

 - **Id** (PaperID)

Success returns status - 204 - as the item is deleted there is no return data associated with this call.

## Box Deletes

When removing boxes this is classed as a soft delete. As with Papercloud front end the box and containing paperwork will be placed within the relative users recycle bin.
NKB
![](RackMultipart20220608-1-mjrzu0_html_d6c6bd440f47392d.png)

Required Parameters:

 - **Id** (BoxID)

Success returns status - 204 - as the item is deleted there is no return data associated with this call.


# Quick Guides
## Setting up an app in Papercloud
## Exporting and importing Swagger (Postman)
## Make REST API calls
NKB
