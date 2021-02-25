---
description: >-
  Some basic functionality that has little to do with the actual API, but comes
  in handy at times.
---

# Basic API Endpoints

{% api-method method="get" host="https://api.tmuniversal.eu/statistics" path="/" %}
{% api-method-summary %}
Base Route
{% endapi-method-summary %}

{% api-method-description %}
This endpoint demonstrates that the API is online.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
API can answer and returns some information.
{% endapi-method-response-example-description %}

```
{
    "message": "TMUniversal's BotStat API",
    "version": 0.1.5
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.tmuniversal.eu/statistics" path="/version" %}
{% api-method-summary %}
API Version
{% endapi-method-summary %}

{% api-method-description %}
Returns the full API version.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Return the full API version.
{% endapi-method-response-example-description %}

```
{    "version": "0.1.5"    }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.tmuniversal.eu/statistics" path="/neko" %}
{% api-method-summary %}
Catgirl Generator
{% endapi-method-summary %}

{% api-method-description %}
Get a random catgirl image URL from the internet.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
A catgirl was successfully found.
{% endapi-method-response-example-description %}

```
{
    "url": "https://cdn.nekos.life/neko/neko223.jpeg",
    "source": "nekos.life"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.tmuniversal.eu/statistics" path="/spongetalk" %}
{% api-method-summary %}
Spongetalk
{% endapi-method-summary %}

{% api-method-description %}
Get a text returned as though Spongebob was mocking it.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="text" type="string" required=true %}
The text that is supposed to be _translated_
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The text was successfully translated and is returned to the user.
{% endapi-method-response-example-description %}

```
{
    "result": "YouR tExT"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The entered query text was invalid.
{% endapi-method-response-example-description %}

```
{
    "error": "no valid text received. try appending ?text=your text here"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

