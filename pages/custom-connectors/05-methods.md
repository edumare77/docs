---
title: Connector Methods
sidebar: cyclr_sidebar
permalink: connector-methods
tags: [connector-creation]
---

## Settings

These are descriptions of the API endpoints in a standard format.

*   **Name **– the name of the method to appear in the Cyclr UI for the user to see. Should be short and snappy and have initial caps for nouns/verbs, lowercase for minor words (like “a” or “to”), e.g. “Delete Emails”, “Get All Contacts”, “Send to List”.
*   **Description **– this is the description of the method to appear in the Cyclr UI for the user to understand what the method does and be informed of any special/interesting values to pass. Can be quite lengthy if appropriate. Can also include links to helpful API documentation if useful.
*   **Hide **– this will hide the method in the Cyclr UI if set to true. Leave out if not hiding.
*   **Category **– used to group methods in the Cyclr UI. Try to keep to single, pluralised words, e.g. “Emails” or “Contacts”.
*   **MethodType **– this defines where the method will appear in the Cyclr UI: Action or Webhook.
*   **HttpMethod **– this is the action to be performed on the API method. Supported methods are GET, POST, PATCH, PUT, DELETE.
*   **DataType **– this is the data type used by the API, either Json, Xml, or Form. For GET, this is the Accept header. For POST, this is the request data. JSON is our recommended data type.
*   **Endpoint **– this is the URI to the API method. This is null if this method is a webhook.
*   **XmlRootElement **– the single root element for the XML document.
*   **RequestFormat **/ **ResponseFormat **– this contains the request or response message format Fields. Each Field has ConnectorField, SystemField, and DisplayName. ConnectorField is the field name used in the connector. If a field is inside an array, it needs to be defined as \[Array\].Field. Multiple-dimension arrays can be defined as \[Array1\].\[Array2\].Field, etc. What if there is a field called \[Array2\].Field inside an Array1? We use \[Array1\].\\Array2.Field\\ to explicitly define Array2.Field as a field name. SystemField is the system name for the field. We use PascalCasing for system names as a convention. DisplayName is the name shown in the Cyclr UI.
*   **Fields **– the names of fields to use in the API call. Fields must have been defined in the connector to appear here. Name, TriggerName, IdentifierKey, and HumanReadableKey are needed.

## Fields

*   **ConnectorField **– the name of the field as used by the remote application’s API. Use Cyclr notation to locate the value, e.g. _[records].EmailAddress_ when receiving an array and retrieving the _EmailAddress _attribute from an element within that array (see _RequestFormat / ResponseFormat_ documentation).
*   **SystemField **– the name to use internally within Cyclr. Use the field as capitalised by the API and remove any spaces. Apps that have the same SystemField name can auto match values in the builder, saving time and making life easier.
*   **DisplayFieldName **– to be displayed in the Cyclr UI to the user. Typically, take the _SystemField _value and add spaces or anything that might help describe it, e.g. in _G_oogle Sheets the _ConnectorField_ _entry.title_ used when working with Rows becomes simply _Row Title_. Think human readable.
*   **Description **– this is the description of the Field to appear in the Cyclr UI for the user to understand how the Field is used. Always include this and keep fairly short (no more than 100 characters).IsOptionalSet to `true` if the Field doesn’t have to be given a value. Leave out if it’s a required Field.

## Mergefields

A mergefields is placeholder will be substituted at runtime.
#### Supported Mergefields

*   LastSuccessfulRunDate – is the last time the cycle successfully ran the method. This is useful to find newly created or updated records in an app. A format string needs to be provided. For example, _{% raw %}{{LastSuccessfulRunDate format=yyyy-MM-ddTHH:mm:ssZ}}{% endraw %}_.
