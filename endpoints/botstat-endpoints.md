---
description: The actual BotStat API Endpoints. Some require an API key.
---

# BotStat Endpoints

{% api-method method="get" host="https://tmuniversal-api.herokuapp.com/api/v1" path="/botstat/:id" %}
{% api-method-summary %}
Get Bot Stats
{% endapi-method-summary %}

{% api-method-description %}
Get information about a bot. This includes the owner; amounts of guilds, channels and users.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Discord Bot ID.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Information retrieved.
{% endapi-method-response-example-description %}

```
{
      "owner": {
            "id": "291272018773671937",
            "username": "Nigel",
            "discriminator": "8226"
      },
      "id": "717773060446486528",
      "guilds": 7,
      "channels": 217,
      "users": 531,
      "lastUpdated": "2020-06-17T15:56:09.498Z"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
No Bot with this ID was found.
{% endapi-method-response-example-description %}

```
{    "error": "ID not recognised"    }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
An error with the database has occurred.
{% endapi-method-response-example-description %}

```
{    "error": "An error has occured!"    }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://tmuniversal-api.herokuapp.com/api/v1" path="/cmdstat/:id" %}
{% api-method-summary %}
Get Command Stats \(all commands\)
{% endapi-method-summary %}

{% api-method-description %}
Statistics about all commands of a bot.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Discord Bot ID.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Data found.
{% endapi-method-response-example-description %}

```
{
    "xp": {
        "botID": "717773060446486528",
        "uses": 6,
        "lastUpdated": "2020-06-17T15:56:11.101Z"
    },
    "test": {
        "botID": "717773060446486528",
        "uses": 3,
        "lastUpdated": "2020-06-18T20:17:48.332Z"
    },
    ...
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
No bot with this ID was found.
{% endapi-method-response-example-description %}

```
{    "error": "ID not recognized"    }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
An error with the database has occurred.
{% endapi-method-response-example-description %}

```
{    "error": "An error has occurred!"    }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://tmuniversal-api.herokuapp.com/api/v1" path="/cmdstat/:id/:cmd" %}
{% api-method-summary %}
Get Command Stats \(specific\)
{% endapi-method-summary %}

{% api-method-description %}
Retrieve statistics about a specific command.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=false %}
Discord Bot ID.
{% endapi-method-parameter %}

{% api-method-parameter name="cmd" type="string" required=false %}
Command to look for
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successfully found
{% endapi-method-response-example-description %}

```
{
     "botID": "717773060446486528",
     "command": "xp",
     "uses": 2,
     "lastUpdated": "2020-06-17T15:56:11.101Z"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
No command given.
{% endapi-method-response-example-description %}

```
{    "error": "Insufficient parameters!"    }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
No bot with this ID was found. OR The given command does not exist \(yet\).
{% endapi-method-response-example-description %}

```
{    "error": "ID not recognized"    }

OR

{    "error": "No entry with this ID."    }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
An error with the database has occurred.
{% endapi-method-response-example-description %}

```
{    error": "An error has occurred!"    }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="patch" host="https://tmuniversal-api.herokuapp.com/api/v1" path="/botstat/:id" %}
{% api-method-summary %}
Update Bot Stats
{% endapi-method-summary %}

{% api-method-description %}
Update user base statistics of your bot. Requires at least one of the body parameters to be set.  
Requires API key.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Discord Bot ID.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="users" type="string" required=false %}
Current amount of users the bot can see.
{% endapi-method-parameter %}

{% api-method-parameter name="channels" type="string" required=false %}
Current amount of channels the bot can see.
{% endapi-method-parameter %}

{% api-method-parameter name="guilds" type="number" required=false %}
Current amount of guilds the bot is in.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Stats updated successfully.
{% endapi-method-response-example-description %}

```
{
     "owner": {
          "id": "291272018773671937",
          "username": "Nigel",
          "discriminator": "8226"
     },
     "id": "717773060446486528",
     "guilds": 77,
     "channels": 666,
     "users": 54321,
     "lastUpdated": "2020-12-31T23:61:09.498Z"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
No valid data was provided.
{% endapi-method-response-example-description %}

```
{    "error": "No valid properties specified!"    }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Occurs when the API key used was not issued for the bot that's being updated.
{% endapi-method-response-example-description %}

```
{    "error": "You may only update your own bot!"    }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
An error with the database has occurred.
{% endapi-method-response-example-description %}

```
{    "error": "An error has occurred!"    }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://tmuniversal-api.herokuapp.com/api/v1" path="/cmdstat/:id" %}
{% api-method-summary %}
Update Command Stats
{% endapi-method-summary %}

{% api-method-description %}
Update command usage statistics.  
Requires API key.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=true %}
Discord Bot ID.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="command" type="string" required=true %}
The command to update.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Stats updated successfully.
{% endapi-method-response-example-description %}

```
{
     "botID": "717773060446486528",
     "command": "xp",
     "uses": 3,
     "lastUpdated": "2020-12-31T23:61:09.498Z"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Occurs when no command is passed through request body.
{% endapi-method-response-example-description %}

```
{    "error": "No valid properties specified!"    }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Occurs when the API key used was not issued for the bot that's being updated.
{% endapi-method-response-example-description %}

```
{    "error": "You may only update your own bot!"    }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
An error with the database has occurred
{% endapi-method-response-example-description %}

```
{    "error": "An error has occurred!"    }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://tmuniversal-api.herokuapp.com/api/v1" path="/cmdstat/:id/:cmd" %}
{% api-method-summary %}
Update Command Stats \(new method\)
{% endapi-method-summary %}

{% api-method-description %}
Update command usage statistics. New method with more comfortable usage.  
Requires API key.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=false %}
Discord Bot ID.
{% endapi-method-parameter %}

{% api-method-parameter name="cmd" type="string" required=false %}
The command to update.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Stats updated successfully.
{% endapi-method-response-example-description %}

```
{
     "botID": "717773060446486528",
     "command": "xp",
     "uses": 3,
     "lastUpdated": "2020-12-31T23:61:09.498Z"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Occurs when no command is passed as path parameter.
{% endapi-method-response-example-description %}

```
{    "error": "No valid properties specified!"    }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Occurs when the API key used was not issued for the bot that's being updated.
{% endapi-method-response-example-description %}

```
{    "error": "You may only update your own bot!"    }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
An error with the database has occurred.
{% endapi-method-response-example-description %}

```
{    "error": "An error has occurred!"    }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

