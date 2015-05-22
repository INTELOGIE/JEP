# JEP
Jason Exchange Protocol

### Request

The request object 
```javascript
{
  id:  "The request sequential ID",
  sid: "The session unique ID if sessions are enabled",
  sessionHash: "The session hash",
  params:  [{ParamObject}]
  actions: [{ActionObject}]
}



```

Field name | Description | Type | Required
---------- | ----------- | ---- | --------
id | Unique sequential id for request | numeric | Yes
sid | Session ID | string | Optional
sessionHash | Session Hash | string | Optional
params | Array of global parameters for the request. These parameters will be passed to all actions | Array of ParamObject | Optional
actions | Array of actions to execute | Array of ActionObject | Yes

The ActionObject 
```javascript
{
  controller : "controller name",
  action : "action name",
  params : [{ParamObject}],
  onError: "What action to do if this action fails"
}

```

Field name | Description | Type | Required
---------- | ----------- | ---- | --------
controller | Name of the controller class that will be called | string | Yes
action | Name of the action that will be called | string | Yes
params | Array of parameters for the action | Array of ParamObject | Optional
onError | Indicates what to do if action fails. Possible values are : continue or stop | string (enum) | Optional (default stop) 

The ParamObject 
```javascript
{
  name : "Parameter name",
  value : {Parameter value}
}

```

Field name | Description | Type | Required
---------- | ----------- | ---- | --------
name | Name of parameter | string | Yes
value | Value of parameter | mixed | Yes

### Response

