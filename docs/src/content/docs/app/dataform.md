---
title: Dataform
description: Usage of dataform methods
---

In Kissflow apps, dataforms gather and store data, enabling users to submit data into an app.

Get dataform instance using `getDataform` method from app's interface.

##### Parameters

| Parameters | type   |
| ---------- | ------ |
| dataformId | String |

##### Syntax

```js
let dataformInstance = kf.app.getDataform(dataformId);
```

### Import CSV

Launches the import CSV popup, where you can upload CSV file and map columns to
the corresponding fields.

##### Parameters

| Parameters    | type   | Description                                                          |
| ------------- | ------ | -------------------------------------------------------------------- |
| defaultValues | Object | Object with keys as field Id and its values in respective data types |

##### Syntax

```js
let defaultValues = { fieldId: "value" };
dataformInstance.importCSV(defaultValues);
```

##### Example

Consider scenario where certain fields are not visible to the user(hidden in
form visibilty). In that case, default values can be used to populate data in
these hidden fields

```js
// Get the dataform with the dataform's flow_id
const dfInstance = kf.app.getDataform("Product_Dataform_A00"); // Product_Dataform_A00 is the flow_id

// Set field values for specific fields of the dataform
let defaultValues = { location: "India" }; // Location is the the field_id of a field inside the dataform

// Pass the field config into the import sdk method
dfInstance.importCSV(defaultValues); // All records imported through this importer would have Location field set as India
```

> Note:
>
> 1. Default values here is optional
> 2. Any variables or parameter can also be mapped in `defaultValues`.
> 3. End user can't pass this value if default value is set by dev.
> 4. Some fields cannot be set as default eg. Auto calculated fields, Sequence
>    numbers etc.
