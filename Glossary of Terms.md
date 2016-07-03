# API Blueprint Glossary of Terms
# API Blueprint 专业术语

A brief list of terms as used in the [API Blueprint](http://apiblueprint.org) context.

一个简要术语列表应用在[API Blueprint](http://apiblueprint.org)范围中。

## Glossary
## 词汇表

<a name="def-action"></a>
### Action
An **HTTP transaction** (a request-response transaction).

**HTTP事务**（请求 - 响应事务）。

Actions are specified by an [HTTP request method](#def-method) within a [resource](#def-resource).

Action由一个[资源](#def-resource)中的 [HTTP请求方法](#def-method) 而指定。

<a name="def-api"></a>
### API
An **HTTP Application programming interface**. Might refer to an API
description. See [**API Blueprint**](#def-api-blueprint).

一个 **HTTP应用程序编程接口** 。可能是指一个API描述。见[**API Blueprint**](#def-api-blueprint)。

<a name="def-api-blueprint"></a>
### API Blueprint
The **API Blueprint language**. A format used to describe API in an API blueprint file.

该 **API Blueprint 语言**。用在一个 API blueprint 格式文件描述API。

<a name="def-asset"></a>
### Asset
**Atomic data**. Most often representing one resource representation in the form of message-body or its validation schema.

**原子数据**。大多数情况下代表消息体或者其验证架构形式的资源表示。

<a name="def-attribute"></a>
### Attribute
Based on the context, attribute (property) of a message-body data structure, or
attribute of a resource, or an input attribute of a transition –
[Action](#def-action).

//TODO
基于消息主体数据结构，或资源的属性，或过渡的输入属性的上下文中，属性（属性） - 行动。

<a name="def-blueprint"></a>
### Blueprint
An **API description**. A **blueprint file** (or a set of files) that describes an API using the API Blueprint language.

一个 **API描述** 。使用 **API蓝图文件**（或一组文件）用 API Blueprint 语言描述API​​。

<a name="def-data-structure"></a>
### Data Structure
A particular data organization, or a description of it. In API Blueprint, data
structures and their [Attributes](#def-attribute) are described using the
Markdown Syntax for Object Notation – [MSON][].

一个特定数据组织，或描述。在 API Blueprint 中，数据结构和它们的[属性](#def-attribute)是使用 Markdown 对象表示语法 – [MSON][]来描述。

<a name="def-entity"></a>
### Entity
[**Entity**](http://www.w3.org/Protocols/rfc2616/rfc2616-sec7.html) being transferred in a [payload](#def-payload).

[**实体**](http://www.w3.org/Protocols/rfc2616/rfc2616-sec7.html) 被转移为中[payload](#def-payload)。

<a name="def-header"></a>
### Header
A [**message-header**](#def-message-header).

[**消息头**](#def-message-header).

<a name="def-method"></a>
### Method
An [**HTTP Request Method**](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods).

[**HTTP 请求方法**](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods).

<a name="def-message"></a>
### Message
An **HTTP transaction message**.

**HTTP 事务消息**.

<a name="def-message-body"></a>
### Message body
An [**asset**](#def-asset) representing [**HTTP transaction message body**](http://en.wikipedia.org/wiki/HTTP_body_data).

代表[**HTTP 事务消息体**](http://en.wikipedia.org/wiki/HTTP_body_data)的[**资产**](#def-asset)。

<a name="def-message-header"></a>
### Message header
An [**asset**](#def-asset) representing [**HTTP transaction message header**](http://en.wikipedia.org/wiki/List_of_HTTP_header_fields).

代表[**HTTP 事务消息头**](http://en.wikipedia.org/wiki/List_of_HTTP_header_fields)的[**资产**](#def-asset)。

<a name="def-parameter"></a>
### Parameter
An [**URI template**](#def-uri-template) **variable**.

[**URI 模板**](#def-uri-template) **变量**.

<a name="def-payload"></a>
### Payload
An **HTTP transaction message** including its **discussion** and any additional [**assets**](#def-asset) such as entity-body validation schema.

**HTTP事务消息** 包括其 **讨论** 和任何其他[**资产**](#def-asset)，如实体主体验证模式。

A payload may have an **identifier** – a string for a [request](#def-request)
payload or an
[HTTP status code](http://en.wikipedia.org/wiki/List_of_HTTP_status_codes) for a
[response](#def-response) payload.

有payload可能有一个 **标识** - 一个[请求](#def-request)payload的字符串或[响应](#def-response)payload的[HTTP状态码](http://en.wikipedia.org/wiki/List_of_HTTP_status_codes)。

<a name="def-property"></a>
### Property
An [entity](#def-entity) field (attribute).

[实体](#def-entity) 字段（属性）。

<a name="def-request"></a>
### Request
A [**payload**](#def-payload) containing one specific [HTTP Request](http://www.w3.org/TR/di-gloss/#def-http-request).

包含一个特定的[HTTP请求](http://www.w3.org/TR/di-gloss/#def-http-request)的[**payload**](#def-payload)。

<a name="def-response"></a>
### Response
A [**payload**](#def-payload) containing one specific [HTTP Response](http://www.w3.org/TR/di-gloss/#def-http-response).
包含一个特定的[HTTP响应](http://www.w3.org/TR/di-gloss/#def-http-response)的[**payload**](#def-payload)。

<a name="def-resource"></a>
### Resource
An API [**resource**](http://www.w3.org/TR/di-gloss/#def-resource) specified by
its *URI*. It can also refer to a [**set of resources**](#def-resource)
matching one [**URI template**](#def-uri-template).

通过 *URI* 指定的API[**资源**](http://www.w3.org/TR/di-gloss/#def-resource)。它也用一个[**URI 模板**](#def-uri-template)匹配指定[**资源组**](#def-resource)。

<a name="def-resource-model"></a>
### Resource Model
One [**manifestation of a resource**](http://www.w3.org/TR/di-gloss/#def-resource-manifestation) in the
form of a [payload](#def-payload). A resource model is an example
representation of its resource. Can be referenced later in the place of a
[payload](#def-payload).

[payload](#def-payload)是资源的一种[**资源表现**](http://www.w3.org/TR/di-gloss/#def-resource-manifestation)。资源模型是其资源的例子表现。可以在[payload](#def-payload)中引用。

<a name="def-resource-set"></a>
### Resource Set
A set of API [**resources**](http://www.w3.org/TR/di-gloss/#def-resource). Its
*URI* matches one specific [**URI template**](#def-uri-template).

一组API[**资源**](http://www.w3.org/TR/di-gloss/#def-resource)。它的 *URI* 匹配一个特定[**URI 模板**](#def-uri-template)。

<a name="def-trait"></a>
### Trait
A quality or characteristic of an API Blueprint SECTION.

一个 API Blueprint 片段的质量或性能。

<a name="def-schema"></a>
### Schema
A **validation schema** in a form of an [**asset**](#def-asset) used to validate (or describe) a [**message-body**](#def-message-body).

在[**资产**](#def-asset)的形式的 **验证模式** 用于验证（或描述）的[**消息体**](#def-message-body)。

<a name="def-uri-template"></a>
### URI template
A compact sequence of characters for describing a range of **Uniform Resource Identifiers** through **variable** expansion, see [**RFC 6570**](http://tools.ietf.org/html/rfc6570).

通过紧凑序列字符串 **变量** 表达式描述 **统一资源标识符** ，请参见[**RFC 6570**](http://tools.ietf.org/html/rfc6570)。

## Additional resources
## 其他资源

+ [HTTP/1.1 Terminology](http://www.w3.org/Protocols/rfc2616/rfc2616-sec1.html#sec1.3)
+ [W3C Glossary of Terms for Device Independence](http://www.w3.org/TR/di-gloss)
+ [Know your HTTP well](https://github.com/for-GET/know-your-http-well)
+ [Markdown Syntax for Object Notation][MSON]



[MSON]: https://github.com/apiaryio/mson
