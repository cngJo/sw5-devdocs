---
layout: default
title: REST API - Examples using filter
github_link: developers-guide/rest-api/examples/media/index.md
menu_title: Filter
menu_order: 300
indexed: true
menu_style: bullet
group: Developer Guides
subgroup: REST API
---

## Introduction

In this article, you will find examples of the provided resource usage for different operations.
For each analyzed scenario, we provide an example of the data that you are expected to provide to the API, as well as an example response.

## Filter by language

In this article you can read more about the filter function. The filter functionality is for limiting the result.

```php
$translationResource->getList(0, 10, array(
    array('property' => 'translation.shopId', 'value' => 2)
));
```

### Filter by language and article ID

```php
$translationResource->getList(0, 1, array(
    array('property' => 'translation.shopId', 'value' => 2),
    array('property' => 'translation.key', 'value' => 200),
    array('property' => 'translation.type', 'value' => 'article')
));
```

**Example output:**

```php
array('total' => 246, 'data' => array(
    array(
        'type' => 'article',
        'data' =>
            array(
                'name' => 'Dummy Translation',
                'description' => 'Dummy Translation',
                'descriptionLong' => 'Dummy Translation',
                'additionalText' => 'Dummy Translation',
                'keywords' => 'Dummy Translation',
                'packUnit' => 'Dummy Translation',
            ),
        'key' => 5,
        'shopId' => '2'
    ),
    array(
        'type' => 'article',
        'data' =>
            array(
                'name' => 'Dummy Translation',
                'description' => 'Dummy Translation',
                'descriptionLong' => 'Dummy Translation',
                'additionalText' => 'Dummy Translation',
                'keywords' => 'Dummy Translation',
                'packUnit' => 'Dummy Translation',
            ),
        'key' => 4,
        'shopId' => '2'
    )
));
```

## Example 1 - Filter products by name

{% include 'api_badge.twig' with {'route': '/api/articles?filter[name]=Lorem', 'method': 'GET'} %}

{% include 'api_badge.twig' with {'route': '/api/articles?filter[0][property]=name&filter[0][value]=Ipsum%', 'method': 'GET'} %}

{% include 'api_badge.twig' with {'route': '/api/articles?filter[0][property]=name&filter[0][expression]=LIKE&filter[0][value]=%Dolor%', 'method': 'GET'} %}

### Result

```json
{
    "data": [
        {},
        {},
        {}
    ],
    "success": true,
    "total": 3
}
```
