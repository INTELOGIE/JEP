# JEP
Jason Exchange Protocol

### Request

Request object structure 
```javascript
{
  id:  "The request sequential ID",
  sid: "The session unique ID if sessions are enabled",
  sessionHash: "The session hash",
  parameters:  [{Parameter}]
  actions: [{RequestAction}]
}



```

Field name | Description | Type | Required
---------- | ----------- | ---- | --------
id | Unique sequential id for request | numeric | Yes
sid | Session ID | string | Optional
sessionHash | Session Hash | string | Optional
parameters | Array of global parameters for the request. These parameters will be passed to all actions | Array of ParamObject | Optional
actions | Array of actions to execute | Array of RequestAction | Yes

Action object structure
```javascript
{
  controller : "controller name",
  action : "action name",
  parameters : [{Parameter}],
  onError: "What action to do if this action fails"
}

```

Field name | Description | Type | Required
---------- | ----------- | ---- | --------
controller | Name of the controller class that will be called | string | Yes
action | Name of the action that will be called | string | Yes
parameters | Array of parameters for the action | Array of Parameter objects | Optional
onError | Indicates what to do if action fails. Possible values are : continue or stop | string (enum) | Optional (default stop) 

Parameter object structure
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

Response object structure

```javascript
{
  id : "The request sequential ID passed by the Request object",
  actions: [{ResponseAction}]
}

```
ResponseAction object structure

```javascript
{
  status: "Action status",
  statusMessage: "A message to explain the status",
  controller : "Name of controller to execute",
  action : "Name of action to execute"
  parameters : [Parameter array]
}

```
