# Authentication

IDP and Base API URLS

<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>

Live:

>Swagger: [https://api.papercloudelite.co.uk/swagger](https://api.papercloudelite.co.uk/swagger)

>Base URL: [https://api.papercloudelite.co.uk/](https://api.papercloudelite.co.uk/)

>Auth URL: [https://idp.papercloudelite.co.uk/connect/authorize](https://idp.papercloudelite.co.uk/connect/authorize)

>Token URL: [https://idp.papercloudelite.co.uk/connect/token](https://idp.papercloudelite.co.uk/connect/token)

Sandbox:

>Swagger: [https://sandboxapi01.papercloudelite.co.uk/swagger](https://sandboxapi01.papercloudelite.co.uk/swagger)

>Base URL: [https://sandboxapi01.papercloudelite.co.uk](https://sandboxapi01.papercloudelite.co.uk/)

>Auth URL: [https://idpsandbox01.papercloudelite.co.uk/connect/authorize](https://idpsandbox01.papercloudelite.co.uk/connect/authorize)

>Token URL: [https://idpsandbox01.papercloudelite.co.uk/connect/token](https://idpsandbox01.papercloudelite.co.uk/connect/token)


## Flows

A set of flows have been created to detail the core exposed functionality of the Papercloud API. This suite of calls is accessible from &quot;URL ONCE HOSTED&quot;

>- Flow1 – Create Client file with option to apply structure or apply a template
>  - Flow1A - Client Get Client by Reference Number
>  - Flow1B – Cabinet Get All
>  - Create a client file with no structure (blank)
>    - Flow 1C - Create Client file no structure (blank structure with no template)
>  - Create a client file and define a bespoke structure for tabs. Rows and boxes
>    - Flow 1D - Create Client File with structure
>  - Client Create Client and apply and existing template
>    - Flow1E – Template Get List
>    - Flow 1F - Client Create Client and apply template
>- Flow2 – Add to structure to existing clients
>  - Flow2A - Client Apply Template
>  - Flow2B – Add a tab to a client file
>  - Flow2C – Add a Row to a client file
>  - Flow2D - Add a Box to a client file
>- Flow3 – Add Paperwork to a box
>  - Flow3A Paper V2 Upload Paper
>- Flow4 – Searches
>  - Flow4A - See All Tabs Rows Boxes For specific client file by ExternalReference
>  - Flow4B - Get a list of all boxes clients that are API accessible that contain the given tag
>- Flow5 – Viewing, retrieving, and downloading items
>  - Flow5A - Paper V2 Get Papers For Box
>  - Flow5B - Box Download Box Contents
>  - Flow5C - Paper V2 Download Paper
>  - Flow5D -Paper V2 Download Paper Base64
>- Flow6 – Jumping to items
>  - Flow6A - Message Hub Post Jump Itinerary


## Flow document

Note the variables within the flow document point to the sandbox:

## Connect config for use with the Sandbox

With WatermarkConnect closed the below file should be placed in the following location:

C:\Program Files\WatermarkTech\WatermarkConnect

NEED FILE


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

To be done

>  200 – indicates success – this will also return in some instances a confirmation of the data stored with some of the post endpoint e.g., if you post a client file the response will include the &quot;ClientFileID&quot; created for the file.

>  403 – generally this is a response type indicating something exists but the user does not have access to view\update it. E.g. trying to find a client that resides within a cabinet for which the user does not have access.

## Param lengths

These are listed on the swagger documentation.

## Date format

Dates should be provided in &quot;DD/MM/YYYY&quot; format e.g., &quot;23/02/2001&quot;. There is not time requirement on the API.

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


# Examples endpoint calls

## Check if a client exists by external reference

This endpoint confirms if a client already exists. This endpoint has an option shallow call

This endpoint is demoed via &quot;Flow1A&quot; of the ApiV2FlowGuide.

![](RackMultipart20220608-1-mjrzu0_html_ec891a2f1493e428.png)

Required Parameters:

>- Reference – this is external unique reference for the client. Typically, the 3rd party&#39;s identification ID.
>- Shallow flag, when shallow is set to True this will return only contact data for the client file. When set to False – this will return client contact data as well as the structure within the client file (Tabs, Rows and boxes)

Curl Example:

```
curl --location --request GET &#39;https://apihotfix.papercloudelite.co.uk/api/v2/client/ref/JON123?shallow=true&#39; 
--header &#39;Accept: application/json&#39; \
--header &#39;Authorization: Bearer eyJhbGci…
```



## Create a client with options to create structure or apply a template structure

These endpoints allow creation of client files within the Papercloud system. Structure can also be applied as part of the creation, which has been shown in the examples

All calls use the same endpoint:

NKBJPEG HERE

The contents are dynamic, some basic examples have been supplied in the calls laid out within below sections.

A explanation of all fields is found here, this version is for client type &quot;Person&quot;:

NKB IMAGE???

```
**{**

**&quot;clientType&quot;:**  **&quot;Person&quot;**** ,--defines if the client is either a &quot;Person&quot; or &quot;other&quot; (Company)**

**&quot;notes&quot;:**  **&quot;string&quot;**** , --OPTIONAL (Any entry is displayed within the client file)**

**&quot;primaryContactExternalReference&quot;:**  **&quot;string&quot;**** , --OPTIONAL though advised (created a link between 3 ****rd**  **party system and Papercloud via the unique identifier from the 3**** rd **** party)**

**&quot;primaryContactTitle&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;primaryContactFirstName&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;primaryContactSurname&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;primaryContactDateOfBirth&quot;:**  **&quot;2022-05-13&quot;**** , --OPTIONAL**

**&quot;primaryContactNINumber&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;secondaryContactExternalReference&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;secondaryContactTitle&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;secondaryContactFirstName&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;secondaryContactSurname&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;secondaryContactDateOfBirth&quot;:**  **&quot;2022-05-31&quot;**** , --OPTIONAL**

**&quot;secondaryContactNINumber&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;phoneNumber1&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;phoneNumber2&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;phoneNumber3&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;parentFileExternalReference&quot;:**  **&quot;string&quot;**** , --OPTIONAL (creates a link to another file)**

**&quot;addressLine1&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;addressLine2&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;addressLine3&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;addressLine4&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;addressLine5&quot;:**  **&quot;string&quot;**** , ****--OPTIONAL**

**&quot;postcode&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;emails&quot;: [ --OPTIONAL (comma separated list of email addresses for the client)**

**&quot;string&quot;**

**],**

**&quot;cabinetId&quot;:**  **0**** , --OPTIONAL (define the cabinet that the client should be placed in – blank\not included creates the client outside of a cabinet)**

**&quot;cabinetName&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;cabinetExternalReference&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;templateParameters&quot;: { --OPTIONAL (allows you to define and apply a template at create)**

**&quot;templateId&quot;:**  **0**** , --Provide the ID of the template you wish to apply**

**&quot;templateTitle&quot;:**  **&quot;string&quot;**** ,**

**&quot;mergeTemplateWithExistingStructure&quot;:**  **true** **–-REQUIRED (do you want to add duplicates or ignore them?)**

**}**

**}**
```

Create a file of the type &quot;Other&quot;
```
**{**

**&quot;clientType&quot;:**  **&quot;Other&quot;**** , --defines if the client is either a &quot;Person&quot; or &quot;other&quot; (Company)**

**&quot;fileName&quot;:**  **&quot;string&quot;**** , --OPTIONAL (Company\Account name)**

**&quot;notes&quot;:**  **&quot;string&quot;**** , --OPTIONAL (Any entry is displayed within the client file)**

**&quot;primaryContactExternalReference&quot;:**  **&quot;string&quot;**** , --OPTIONAL though advised (created a link between 3 ****rd**  **party system and Papercloud via the unique identifier from the 3**** rd **** party)**

**&quot;phoneNumber1&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;phoneNumber2&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;phoneNumber3&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;addressLine1&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;addressLine2&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;addressLine3&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;addressLine4&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;addressLine5&quot;:**  **&quot;string&quot;**** , ****--OPTIONAL**

**&quot;postcode&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;emails&quot;: [ --OPTIONAL (comma separated list of email addresses for the client)**

**&quot;string&quot;**

**],**

**&quot;cabinetId&quot;:**  **0**** , --OPTIONAL (define the cabinet that the client should be placed in – blank\not included creates the client outside of a cabinet)**

**&quot;cabinetName&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;cabinetExternalReference&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;templateParameters&quot;: { --OPTIONAL (allows you to define and apply a template at create)**

**&quot;templateId&quot;:**  **0**** ,**

**&quot;templateTitle&quot;:**  **&quot;string&quot;**** ,**

**&quot;mergeTemplateWithExistingStructure&quot;:**  **true**

**}**
```
To apply structure within this endpoint create the following section can be included within the body, this is fully optional – for a clearer example see XXXXX:

ALSO NEED ROW ORDER asc to desc or other way?
```
**&quot;tabs&quot;: [**

**{**

**&quot;title&quot;:**  **&quot;string&quot;**** , --REQUIRED (the title to be applied to the tab)**

**&quot;position&quot;:**  **0**** , -- OPTIONAL (decide on the position of the tab within the client file)**

**&quot;colour&quot;:**  **&quot;Grey&quot;**** , --OPTIONAL (**

**&quot;rows&quot;: [ --OPTIONAL (add rows to the new tab)**

**{**

**&quot;title&quot;:**  **&quot;string&quot;**** , --REQUIRED if adding rows (the title to be applied to the Row)**

**&quot;position&quot;:**  **0**** , --OPTIONAL (order in which the row will be created)**

**&quot;boxes&quot;: [ --OPTIONAL (add boxes to the row)**

**{**

**&quot;title&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;notes&quot;:**  **&quot;string&quot;**** , --OPTIONAL**

**&quot;date&quot;:**  **&quot;2022-05-31&quot;**** , --OPTIONAL**

**&quot;colour&quot;:**  **&quot;Grey&quot;**** , --OPTIONAL**

**&quot;deleted&quot;:**  **false**** , --REQUIRED**

**&quot;tagCount&quot;:**  **0**** , --OPTIONAL**

**&quot;tags&quot;: [ --OPTIONAL**

**&quot;string&quot;**  **–List of comma separated tags to be applied to the box**

**]**

**}**

**],**

**&quot;notes&quot;:**  **&quot;string&quot;** **–OPTIONAL(row notes)**

**}**

**],**

**}**

**],**
```
## Pre-Requisites\linked items:

- Check if a client exists by external reference
- See cabinets (Flow1B)
- See templates (Flow1E)

## Create client file no structure:

This call will create a client file in Papercloud, but it will not add any Tab, Row or box structure to the file.

In this example we are creating a client file with a partner and placing it within a cabinet.

This endpoint is demoed via &quot;Flow1C&quot; of the ApiV2FlowGuide.

Raw body structure:

**{**

**&quot;clientType&quot;:**  **&quot;Person&quot;**** ,**

**&quot;notes&quot;:**  **&quot;string&quot;**** ,**

**&quot;primaryContactExternalReference&quot;:**  **&quot;string&quot;**** ,**

**&quot;primaryContactTitle&quot;:**  **&quot;string&quot;**** ,**

**&quot;primaryContactFirstName&quot;:**  **&quot;string&quot;**** ,**

**&quot;primaryContactSurname&quot;:**  **&quot;string&quot;**** ,**

**&quot;primaryContactDateOfBirth&quot;:**  **&quot;2022-05-19T14:58:03.982Z&quot;**** ,**

**&quot;primaryContactNINumber&quot;:**  **&quot;string&quot;**** ,**

**&quot;secondaryContactExternalReference&quot;:**  **&quot;string&quot;**** ,**

**&quot;secondaryContactTitle&quot;:**  **&quot;string&quot;**** ,**

**&quot;secondaryContactFirstName&quot;:**  **&quot;string&quot;**** ,**

**&quot;secondaryContactSurname&quot;:**  **&quot;string&quot;**** ,**

**&quot;secondaryContactDateOfBirth&quot;:**  **&quot;2022-05-19T14:58:03.982Z&quot;**** ,**

**&quot;secondaryContactNINumber&quot;:**  **&quot;string&quot;**** ,**

**&quot;phoneNumber1&quot;:**  **&quot;string&quot;**** ,**

**&quot;phoneNumber2&quot;:**  **&quot;string&quot;**** ,**

**&quot;phoneNumber3&quot;:**  **&quot;string&quot;**** ,**

**&quot;addressLine1&quot;:**  **&quot;string&quot;**** ,**

**&quot;addressLine2&quot;:**  **&quot;string&quot;**** ,**

**&quot;addressLine3&quot;:**  **&quot;string&quot;**** ,**

**&quot;addressLine4&quot;:**  **&quot;string&quot;**** ,**

**&quot;addressLine5&quot;:**  **&quot;string&quot;**** ,**

**&quot;postcode&quot;:**  **&quot;string&quot;**** ,**

**&quot;emails&quot;: [**

**&quot;string&quot;**

**],**

**&quot;cabinetId&quot;:**  **0**

**}**

Curl Example:

curl --location --request POST &#39;https://apihotfix.papercloudelite.co.uk/api/v2/client/create&#39; \

--header &#39;Content-Type: application/json&#39; \

--header &#39;Accept: application/json&#39; \

--header &#39;Authorization: Bearer eyJhbGci…&#39; \

--data-raw &#39;{

  &quot;clientType&quot;: &quot;Person&quot;,

  &quot;fileName&quot;: &quot;&quot;,

  &quot;notes&quot;: &quot;Some notes relating to the client file&quot;,

  &quot;primaryContactExternalReference&quot;: &quot;REF12345&quot;,

  &quot;primaryContactTitle&quot;: &quot;Mr&quot;,

  &quot;primaryContactFirstName&quot;: &quot;Mickey&quot;,

  &quot;primaryContactSurname&quot;: &quot;Mounse&quot;,

  &quot;primaryContactDateOfBirth&quot;: &quot;2008-10-06&quot;,

  &quot;primaryContactNINumber&quot;: &quot;NI1234&quot;,

  &quot;secondaryContactExternalReference&quot;: &quot;REF12346&quot;,

  &quot;secondaryContactTitle&quot;: &quot;Mrs&quot;,

  &quot;secondaryContactFirstName&quot;: &quot;Minnie&quot;,

  &quot;secondaryContactSurname&quot;: &quot;Mouse&quot;,

  &quot;secondaryContactDateOfBirth&quot;: &quot;1991-04-05&quot;,

  &quot;secondaryContactNINumber&quot;: &quot;NI12346&quot;,

  &quot;phoneNumber1&quot;: &quot;01131234567&quot;,

  &quot;phoneNumber2&quot;: &quot;01131234568&quot;,

  &quot;phoneNumber3&quot;: &quot;01131234569&quot;,

  &quot;addressLine1&quot;: &quot;do reprehenderit cillum magna&quot;,

  &quot;addressLine2&quot;: &quot;anim nulla quis&quot;,

  &quot;addressLine3&quot;: &quot;cillum in in Ut elit&quot;,

  &quot;addressLine4&quot;: &quot;fugiat&quot;,

  &quot;addressLine5&quot;: &quot;sed magna&quot;,

  &quot;postcode&quot;: &quot;BD18 3ST&quot;,

  &quot;emails&quot;: [

    &quot;test@test123.com,&quot;,

    &quot;Another@1234.com&quot;

  ],

  &quot;cabinetId&quot;: 2

}&#39;

## Create client file apply template:

This call will create a client file in Papercloud and apply a pre created template from the template repository.

This endpoint is demoed via &quot;Flow1F&quot; of the ApiV2FlowGuide.

Raw body structure:

**{**

**&quot;clientId&quot;**** : **** 0 ****,**

**&quot;clientType&quot;**** : ****&quot;Person&quot; ****,**

**&quot;fileName&quot;**** : ****&quot;string&quot; ****,**

**&quot;notes&quot;**** : ****&quot;string&quot; ****,**

**&quot;primaryContactExternalReference&quot;**** : ****&quot;string&quot; ****,**

**&quot;primaryContactTitle&quot;**** : ****&quot;string&quot; ****,**

**&quot;primaryContactFirstName&quot;**** : ****&quot;string&quot; ****,**

**&quot;primaryContactSurname&quot;**** : ****&quot;string&quot; ****,**

**&quot;primaryContactDateOfBirth&quot;**** : ****&quot;2022-05-19T14:58:03.982Z&quot; ****,**

**&quot;primaryContactNINumber&quot;**** : ****&quot;string&quot; ****,**

**&quot;cabinetId&quot;**** : **** 0 ****,**

**&quot;templateParameters&quot;**** : {**

**&quot;templateId&quot;**** : **** 0 ****,**

**&quot;templateTitle&quot;**** : ****&quot;string&quot; ****,**

**&quot;mergeTemplateWithExistingStructure&quot;**** : **** true**

**}**

**}**

Curl Example:

curl --location --request POST &#39;https://apihotfix.papercloudelite.co.uk/api/v2/client/create&#39; \

--header &#39;Content-Type: application/json&#39; \

--header &#39;Accept: application/json&#39; \

--header &#39;Authorization: Bearer eyJhbGc…&#39; \

--data-raw &#39;{

    &quot;clientType&quot;: &quot;Person&quot;,

    &quot;fileName&quot;: &quot;&quot;,

    &quot;notes&quot;: null,

    &quot;primaryContactExternalReference&quot;: &quot;&quot;,

    &quot;primaryContactTitle&quot;: &quot;Mr&quot;,

    &quot;primaryContactFirstName&quot;: &quot;Template 7&quot;,

    &quot;primaryContactSurname&quot;: &quot;Test 7&quot;,

    &quot;primaryContactDateOfBirth&quot;: null,

    &quot;primaryContactNINumber&quot;: &quot;&quot;,

    &quot;cabinetId&quot;: 1,

    &quot;cabinetName&quot;: &quot;Cabinet 1&quot;,

       &quot;templateParameters&quot;: {

    &quot;templateId&quot;: 3,

    &quot;templateTitle&quot;: &quot;test&quot;,

    &quot;mergeTemplateWithExistingStructure&quot;: true

  }

}&#39;

## Create client file define bespoke structure:

This call will create a client file in Papercloud and apply bespoke structure e.g., tabs, rows, and boxes.

COLOUIRS

This endpoint is demoed via &quot;Flow1D&quot; of the ApiV2FlowGuide.

Within this example the client will be created with the following structure:

![](RackMultipart20220608-1-mjrzu0_html_72299ecdddd867f9.png)

This is the body used to produce the client file:

**{**

     **&quot;clientType&quot;: ****&quot;Person&quot;,**

     **&quot;notes&quot;: ****&quot;Add some notes to the client file&quot; ****,**

     **&quot;primaryContactExternalReference&quot;: ****&quot;REF123454&quot; ****,**

     **&quot;primaryContactTitle&quot;:****  &quot;Mr&quot; ****,**

     **&quot;primaryContactFirstName&quot;: ****&quot;John&quot; ****,**

     **&quot;primaryContactSurname&quot;: &quot;**** Smith ****&quot;,**

     **&quot;primaryContactDateOfBirth&quot;: &quot;**** 01/02/1985 ****&quot;,**

     **&quot;primaryContactNINumber&quot;: &quot;**** NI1234344 ****&quot;,**

    **&quot;tabs&quot;: [**

         **{**

             **&quot;title&quot;: &quot;**** Insurance ****&quot;,**

             **&quot;position&quot;: **** 0 ****,**

             **&quot;colour&quot;: **** 2 ****,**

            **&quot;rows&quot;: [**

                 **{**

                     **&quot;title&quot;: &quot;**** T1-R1 ****&quot;,**

                     **&quot;position&quot;: **** 0 ****,**

                    **&quot;boxes&quot;: [**

                         **{**

                             **&quot;title&quot;: &quot;**** T1-R1-B1 ****&quot;,**

                            **&quot;tags&quot;: [**

                                 **&quot;**** TAG\_12ABC ****&quot;**

                            **]**

                         **},**

                         **{**

                             **&quot;title&quot;: &quot;**** T1-R1-B2 ****&quot;**

                         **}**

                    **]**

                 **},**

                 **{**

                     **&quot;title&quot;: &quot;**** T1-R2 ****&quot;,**

                     **&quot;position&quot;: **** 0 ****,**

                    **&quot;boxes&quot;: [**

                         **{**

                             **&quot;title&quot;: ****&quot;T1-R2-B1&quot;**

                         **},**

                         **{**

                             **&quot;title&quot;: ****&quot;T1-R2-B2&quot;**

                         **},**

                         **{**

                             **&quot;title&quot;: ****&quot;T1-R2-B3&quot;**

                         **},**

                         **{**

                             **&quot;title&quot;: ****&quot;T1-R2-B4&quot;**

                         **}**

                    **]**

                 **}**

            **]**

         **},**

         **{**

             **&quot;title&quot;: &quot;**** Forecast ****&quot;,**

             **&quot;position&quot;: **** 1 ****,**

             **&quot;colour&quot;: **** 5 ****,**

            **&quot;rows&quot;: [**

                 **{**

                     **&quot;title&quot;: &quot;**** T2-R1 ****&quot;,**

                     **&quot;position&quot;: **** 0 ****,**

                    **&quot;boxes&quot;: [**

                         **{**

                             **&quot;title&quot;: &quot;**** T2-R1-B1 ****&quot;**

                         **},**

                         **{**

                             **&quot;title&quot;: &quot;**** T2-R1-B2 ****&quot;**

                         **}**

                    **]**

                 **},**

                 **{**

                     **&quot;title&quot;: &quot;**** T2-R2 ****&quot;,**

                     **&quot;position&quot;: **** 0 ****,**

                    **&quot;boxes&quot;: [**

                         **{**

                             **&quot;title&quot;: &quot;**** T2-R2-B1 ****&quot;**

                         **},**

                         **{**

                             **&quot;title&quot;: &quot;**** T2-R2-B2 ****&quot;,**

                            **&quot;tags&quot;: [**

                                 **&quot;**** TAG\_12ABC ****&quot;,**

                                 **&quot;**** TAG\_34DEF ****&quot;**

                            **]**

                         **},**

                         **{**

                             **&quot;title&quot;: &quot;**** T2-R2-B3 ****&quot;**

                         **}**

                    **]**

                 **}**

            **]**

         **}**

    **]**

**}**

Curl Example:

curl --location --request POST &#39;https://apihotfix.papercloudelite.co.uk/api/v2/client/create&#39; \

--header &#39;Content-Type: application/json&#39; \

--header &#39;Accept: application/json&#39; \

--header &#39;Authorization: Bearer eyJhbGciOi…\

--data-raw &#39;{

    &quot;clientType&quot;: &quot;Person&quot;,

    &quot;fileName&quot;: &quot;&quot;,

    &quot;notes&quot;: null,

    &quot;primaryContactExternalReference&quot;: &quot;&quot;,

    &quot;primaryContactTitle&quot;: &quot;Mr&quot;,

    &quot;primaryContactFirstName&quot;: &quot;Template 7&quot;,

    &quot;primaryContactSurname&quot;: &quot;Test 7&quot;,

    &quot;primaryContactDateOfBirth&quot;: null,

    &quot;primaryContactNINumber&quot;: &quot;&quot;,

    &quot;tabs&quot;: [

        {

            &quot;title&quot;: &quot;T1&quot;,

            &quot;position&quot;: 0,

            &quot;colour&quot;: 2,

            &quot;rows&quot;: [

                {

                    &quot;title&quot;: &quot;T1-R1&quot;,

                    &quot;position&quot;: 0,

                    &quot;boxes&quot;: [

                        {

                            &quot;title&quot;: &quot;T1-R1-B1&quot;,

                            &quot;tags&quot;: [

                                &quot;TAG\_12ABC&quot;

                            ]

                        },

                        {

                            &quot;title&quot;: &quot;T1-R1-B2&quot;

                        }

                    ]

                },

                {

                    &quot;title&quot;: &quot;T1-R2&quot;,

                    &quot;position&quot;: 0,

                    &quot;boxes&quot;: [

                        {

                            &quot;title&quot;: &quot;T1-R2-B1&quot;

                        },

                        {

                            &quot;title&quot;: &quot;T1-R2-B2&quot;

                        },

                        {

                            &quot;title&quot;: &quot;T1-R2-B3&quot;

                        },

                        {

                            &quot;title&quot;: &quot;T1-R2-B4&quot;

                        }

                    ]

                }

            ]

        },

        {

            &quot;title&quot;: &quot;T2&quot;,

            &quot;position&quot;: 1,

            &quot;colour&quot;: 5,

            &quot;rows&quot;: [

                {

                    &quot;title&quot;: &quot;T2-R1&quot;,

                    &quot;position&quot;: 0,

                    &quot;boxes&quot;: [

                        {

                            &quot;title&quot;: &quot;T2-R1-B1&quot;

                        },

                        {

                            &quot;title&quot;: &quot;T2-R1-B2&quot;

                        }

                    ]

                },

                {

                    &quot;title&quot;: &quot;T2-R2&quot;,

                    &quot;position&quot;: 0,

                    &quot;boxes&quot;: [

                        {

                            &quot;title&quot;: &quot;T2-R2-B1&quot;

                        },

                        {

                            &quot;title&quot;: &quot;T2-R2-B2&quot;,

                            &quot;tags&quot;: [

                                &quot;TAG\_12ABC&quot;,

                                &quot;TAG\_34DEF&quot;

                            ]

                        },

                        {

                            &quot;title&quot;: &quot;T2-R2-B3&quot;

                        }

                    ]

                }

            ]

        }

    ],

    &quot;cabinetId&quot;: 1,

    &quot;cabinetName&quot;: &quot;Cabinet 1&quot;

}&#39;

# Jumping to an entity (ClientFile, Tab, Box, Page)

A Jump is simply a means to send some defining data to the API that essentially drives the front end of Papercloud in context of the authenticated user.

This endpoint is demoed via &quot;Flow6A&quot; of the ApiV2FlowGuide.

This functionality requires vx.x.x.x or later of Connect to be installed on the client machine.

The call to initiate a jump is as follows:

 ![](RackMultipart20220608-1-mjrzu0_html_df1eff0f6933cd60.png)

The Body of this call should contain the following:

{

  &quot;elementType&quot;: &quot;&quot;,

  &quot;elementId&quot;: -12345

}

The element types accepted for this call are as follows:

ClientFile **=** 3

Tab **=** 4

Box **=** 6

Paper **=** 7

The endpoint also allows the jump to be initiated with the use of the ExternalReference, this is done with the following structure:

{

    &quot;elementType&quot;: 3,

    &quot;elementId&quot;: 0,

    &quot;externalReference&quot;: &quot;String&quot;

}

The elementId relates to the item that needs to be brought to the attention of the end user of Papercloud.

Curl Example:

curl --location --request POST &#39;https://apihotfix.papercloudelite.co.uk/api/messageHub/jump&#39; \

--header &#39;Content-Type: application/json&#39; \

--header &#39;Accept: application/json&#39; \

--header &#39;Authorization: Bearer eyJhbGci…&#39;

--data-raw &#39;{

  &quot;elementType&quot;: &quot;3&quot;,

  &quot;elementId&quot;: 6

}&#39;

# Download a Paper item by ID

Paper in Papercloud is the individual items contained within a document box. This could be a single image or Office Word Document as examples. This specific call provides the document for download to the caller.

This endpoint is demoed via &quot;Flow5C&quot; and &quot;Flow5D&quot; of the ApiV2FlowGuide.

There are two version of the call, one returns the physical paper item that a user can download to view, e.g., a .docx document that the user could then &quot;Download&quot; in the browser for access. The other allows the return of the paper in Base64 format, this would be useful if the requestion application wanted to display\alter the document within their front-end application.

## File version:

![](RackMultipart20220608-1-mjrzu0_html_cddde0afe3e50468.png)

Required Parameter:

- PaperID

Curl Example:

curl **--**** location ****--** request GET &#39;https://apihotfix.papercloudelite.co.uk/api/v2/paper/3892/download&#39; \

**--** header &#39;Accept: application/octet-stream&#39; \

**--** header &#39;Authorization: Bearer eyJhbGciOiJSUz…&#39;

## Base64:

![](RackMultipart20220608-1-mjrzu0_html_f2e5c53b579842a4.png)

Required Parameter:

- PaperID

Curl Example:

curl --location --request GET &#39;https://apihotfix.papercloudelite.co.uk/api/v2/paper/3892/downloadBase64&#39; \

--header &#39;Accept: application/json&#39; \

--header &#39;Authorization: Bearer eyJhbGciOiJSUzI1NiIs&#39;

# Get client files with all Tabs, Rows and Boxes

This endpoint returns the entire structure of a client file.

This endpoint is demoed via &quot;Flow4A&quot; of the ApiV2FlowGuide.

![](RackMultipart20220608-1-mjrzu0_html_ff7f2d4e441f15f9.png)

Required Parameters:

- Reference (ExternalReference)
- shallow = false

Curl Example:

curl --location --request GET &#39;https://apihotfix.papercloudelite.co.uk/api/v2/client/ref/JON123?shallow=false&#39; \

--header &#39;Accept: application/json&#39; \

--header &#39;Authorization: Bearer eyJhbGc…&#39;

# Return all paper items within a box

This endpoint returns the contents of a document box.

This endpoint is demoed via &quot;Flow5A&quot; of the ApiV2FlowGuide.

![](RackMultipart20220608-1-mjrzu0_html_46fd3fd3650f53f7.png)

Required Parameters:

- id (boxId)
- shallow = false

Curl Example:

curl --location --request GET &#39;https://apihotfix.papercloudelite.co.uk/api/v2/paper/papersForBox/1163&#39; \

--header &#39;Accept: application/json&#39; \

--header &#39;Authorization: Bearer eyJhbGciO…&#39;

# Download an entire box contents

This endpoint is demoed via &quot;Flow5B&quot; of the ApiV2FlowGuide.

![](RackMultipart20220608-1-mjrzu0_html_2735e8ea484d4a55.png)

Curl Example:

curl --location --request GET &#39;https://apihotfix.papercloudelite.co.uk/api/v2/boxes/1234/download?printable=false&#39; \

--header &#39;Accept: application/octet-stream&#39;

--header &#39;Authorization: Bearer eyJhbGciO…&#39;

# Retrieve items via tag search

This endpoint is demoed via &quot;Flow4B&quot; of the ApiV2FlowGuide.

![](RackMultipart20220608-1-mjrzu0_html_981706a552abea7f.png)

curl --location --request POST &#39;https://apihotfix.papercloudelite.co.uk/api/v2/tags/search&#39; \

--header &#39;Content-Type: application/json&#39; \

--header &#39;Authorization: Bearer eyJhbGciO…&#39;

--data-raw &#39;{

    &quot;ClientId&quot;: null,

    &quot;Tag&quot;: &quot;TAG1&quot;,

    &quot;From&quot;: null,

    &quot;To&quot;: null,

    &quot;BoxTitle&quot;: null

}&#39;

Tag searches can also be done within a client file, the endpoint for this is as below:

![](RackMultipart20220608-1-mjrzu0_html_9dff37d5094a1899.png)

Responses:

200 – a successful request will return a set of JSON WHAT ARE ELEMENT?

**[**

**{**

**&quot;elementId&quot;:**  **0**** , --This is an internal field and can be ignored**

**&quot;elementType&quot;:**  **0**** , --This is an internal field and can be ignored**

**&quot;elementDate&quot;:**  **&quot;2022-05-31T15:47:14.953Z&quot;**** , --This is an internal field and can be ignored**

**&quot;clientId&quot;:**  **0**** ,**

**&quot;clientFileName&quot;:**  **&quot;string&quot;**** ,**

**&quot;tabId&quot;:**  **0**** ,**

**&quot;tabTitle&quot;:**  **&quot;string&quot;**** ,**

**&quot;rowId&quot;:**  **0**** ,**

**&quot;rowTitle&quot;:**  **&quot;string&quot;**** ,**

**&quot;boxId&quot;:**  **0**** ,**

**&quot;boxTitle&quot;:**  **&quot;string&quot;**** ,**

**&quot;paperId&quot;:**  **0**** ,**

**&quot;paperTitle&quot;:**  **&quot;string&quot;**** ,**

**&quot;pageCount&quot;:**  **0**** ,**

**&quot;tagCount&quot;:**  **0**

**}**

**]**

Example of multiple return items:

SHOW EXAMPLES

# Upload Paper items

![](RackMultipart20220608-1-mjrzu0_html_a4476649dbd51e50.png)

Parameters:

- Files – Required – the File to be sent
- Upload Itinerary:
  - { &quot;ClientId&quot;:, &quot;TabId&quot;:, &quot;RowId&quot;:, &quot;BoxId&quot;:, &quot;FileInformation&quot;: [{ &quot;FileName&quot;: &quot;&quot;, &quot;CreatedDate&quot;: &quot;&quot;}] }

![](RackMultipart20220608-1-mjrzu0_html_e0a47e0fcc0ddd24.png)

Body:

**{**

**&quot;appendToFront&quot;**** : **** true****, --REQUIRED (set the location to either the front\rear of the box)**

**&quot;paperBase64String&quot;**** : ****&quot;string&quot;****, --REQUIRED (this is the paper item to be stored)**

**&quot;thumbnailBase64String&quot;**** : ****&quot;string&quot;****, --OPTIONAL (ability to send a thumbnail with the item)**

**&quot;filename&quot;**** : ****&quot;string&quot;****, --OPTIONAL (filename to be set on the item)**

**&quot;filedate&quot;**** : ****&quot;2022-05-12&quot;****, --OPTIONAL (todays date is used if not supplied)**

**&quot;paperType&quot;**** : ****&quot;INT&quot;****, --REQUIRED (see PaperType lookup below)**

**&quot;uploadItinerary&quot;**** : { ****&quot;boxID&quot;: &quot;INT&quot; **** }, --REQUIRED (defines the box that the paper should be placed)**

    &quot;uploadItinerary&quot;: {

        &quot;boxId&quot;: 2351

    },

**&quot;tags&quot;**** : [ --OPTIONAL (define any tags to be added to the item in a comma separated list)**

**&quot;string&quot;**

**]**

**}**

PaperType lookup by extension:

&quot;.tif&quot; or &quot;.tiff&quot; : 0

&quot;.doc&quot;: 1

&quot;.xls&quot;: 2

&quot;.txt&quot;: 3

&quot;.pdf&quot;: 4

&quot;.msg&quot;: 5

&quot;.mp3&quot;: 6

&quot;.ppt&quot;: 7

&quot;.jpg&quot; or &quot;.jpeg&quot; : 10

&quot;.docx&quot;: 11

&quot;.xlsx&quot;: 12

&quot;.pptx&quot;: 13

&quot;.wav&quot;: 14

&quot;.zip&quot;: 15

&quot;.xlsm&quot;: 16

&quot;.dmsg&quot;: 17

&quot;&quot;: 9

&quot;other&quot; : 8

# Send Thumbnails with paper items

This is optional for all items paperwork however this is specifically useful for Office items as server-side thumbnail generation is near impossible due to Office being a client-side application. Any Office documents will be added to the system without thumbnails if this is not supplied. (Note: thumbnails will be applied once the version is updated within PCE via Watermark Connect.)

COME BACK TO

# Paper Deletes

When removing paperwork this is classed as a soft delete. As with Papercloud front end the paperwork will be placed within the relative users recycle bin.

![](RackMultipart20220608-1-mjrzu0_html_9b0a745efbb9d043.png)

Required Parameters:

- Id (PaperID)

Return values:

- TBC ONCE CHANGES ARE MADE

# Box Deletes

When removing boxes this is classed as a soft delete. As with Papercloud front end the box and containing paperwork will be placed within the relative users recycle bin.

![](RackMultipart20220608-1-mjrzu0_html_d6c6bd440f47392d.png)

Required Parameters:

- Id (BoxID)

Return values:

- TBC ONCE CHANGES ARE MADE

# Update existing client file details

# To do:

- Updates for existing items
- See Templates
- Is it possible to remove these fields from the response while creating a client file with file type: Other

![](RackMultipart20220608-1-mjrzu0_html_b2ee116575890b1c.png)

- See Cabinets
- Send Thumbnails for posted papers
- Deletes
- Return codes
- Example of uploading paper
  - Upload Itinerary
  - Base64 upload with file types
  -

Also this documentation can&#39;t be considered as descriptive enough as

- It covers only happy path i.e. status 200 . No details or other status codes and error messages. Dev team must need to handle all -ve conditions and should be aware of these. These also needs to be added in the test cases.
- There is no definition for request parameters, field limits not defined. Just for e.g. what does shallow mean in Get client by reference?

![](RackMultipart20220608-1-mjrzu0_html_bcee2896674425d.jpg)

- Similarly response parameters have no description – no idea what is element id and  element type (\&quot;elementId\&quot;: 47326852,\n  \&quot;elementType\&quot;: \&quot;None). Although most are intuitive enough by name but not all.
- Take example of Flow 4 B, in case there more than one documents in a box matching tag, no idea how response will be returned, as a array or each record will be listed in a flat structure.

In general for a publically available apis, documentation should be much more thorough.
