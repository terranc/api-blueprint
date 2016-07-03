# Advanced API Blueprint Tutorial
# API Blueprint 高级教程

Welcome to the advanced API Blueprint tutorial! This tutorial will take you
through advanced topics like JSON Schema, request and response attributes, data
structures and relation types.

欢迎来到 API Blueprint 高级教程！这个教程将带你了解高级特性例如JSON Schema，请求与响应属性，
数据结构和类型关系。

This tutorial assumes that you have read the [API Blueprint Tutorial](https://github.com/apiaryio/api-blueprint/blob/master/Tutorial.md).

本教程假定你已经阅读[API Blueprint 教程](https://github.com/apiaryio/api-blueprint/blob/master/Tutorial.md)。

## JSON Schema
## JSON Schema

Action request and response bodies can have associated schemas that describe
the allowed structure of the body content. JSON bodies are typically described
with [JSON Schema](http://json-schema.org/). Given a simple JSON response body
we can describe the structure of the response with JSON Schema in a `+ Schema`
section.

操作请求体和响应体可以关联模式从而描述允许的主体内容结构。
JSON内容体通常使用[JSON Schema](http://json-schema.org/)来描述。
给定一个简单的 JSON 响应体我们可以通过使用 JSON Schema 在`+ Schema`段落中描述响应的结构。

The schema can describe the type of each member, which members are required,
default values, and support a number of other advanced features. Below is an
example, taken from the
[Polls API](https://raw.github.com/apiaryio/api-blueprint/master/examples/Polls%20API.md)
blueprint:

该模式可以描述类型的每个成员，哪些成员是必需的，默认值，并支持其他一些高级功能。
下面是一个例子，来自 [Polls API](https://raw.github.com/apiaryio/api-blueprint/master/examples/Polls%20API.md) blueprint：

```apib
### Create a New Question [POST]
You may create your own question using this action. It takes a JSON object
containing a question and a collection of answers in the form of choices.

+ Request (application/json)

    + Body

            {
              "question": "Favourite language?"
              "choices": [
                "Swift",
                "Objective-C"
              ]
            }

    + Schema

            {
              "$schema": "http://json-schema.org/draft-04/schema#",
              "type": "object",
              "properties": {
                "question": {
                  "type": "string
                },
                "choices": {
                  "type": "array",
                  "items": {
                    "type": "string"
                  },
                  "minItems": 2
                }
              }
            }
```

## Attributes
## 属性

Another way of describing examples and the structure of your request and
response content is by using [MSON](https://github.com/apiaryio/mson#readme).
MSON, like API Blueprint, allows you to use human-readable plain text to
describe things rather than formats designed for computer parsing like JSON or
YAML. Where API Blueprint allows you to describe your API, MSON allows you to
describe data structures.

另一种描述请求和响应内容的结构和例子的方式是通过使用[MSON](https://github.com/apiaryio/mson#readme)。
MSON，与 API Blueprint类似，允许您使用人类可读的纯文本描述的东西，而不是专为计算机解析像 JSON 或 YAML 格式。
API Blueprint 允许你描述 API ， MSON 允许你描述数据结构。

MSON can be added to resources, actions, and individual requests or responses
via an `+ Attributes` section.

MSON 可以添加到资源，操作和个别的请求或响应通过`+ Attributes`作为属性部分。

Creating a new question in the polls API can be modeled using MSON:

在民意调查 API 中可以使用 MSON 建模描述一个问题的创建：

```apib
### Create a New Question [POST]
You may create your own question using this action. It takes a JSON object
containing a question and a collection of answers in the form of choices.

+ Request (application/json)

    + Attributes

        + question: Favourite Language? (required)
        + choices: Swift, `Objective-C` (array, required)

```

When the above blueprint is parsed it will have a JSON body and JSON Schema
example generated for it from the MSON attributes. Note, however, that the
generated JSON Schema may differ from a hand-written one. In this example, the
`minItems` will not be set. If you have such constraints you can override the
generated schema by providing your own, in which case only the JSON body will
be generated.

当上述 blueprint 解析将使用 MSON 属性为其生成一个 JSON 的请求体和 JSON Schema 例子。
但是请注意，所生成的 JSON Schema 可能与手写有相差。
在这个例子中，`minItems`将不被设置。
如果您有这样的限制，你可以重写模式生成，在这种情况下，将只产生JSON内容体。

*Note*: MSON is still considered a beta feature!
*注意*：MSON 仍然被认为是测试版功能！

## Data Structures
## 数据结构

Once you start using MSON, you may find yourself wanting to reuse certain
commonly used or nested data structure components. This is possible with the
`## Data Structures` section. Attributes sections can then reference the data
structures defined in the Data Structures or other resource sections by name.

一旦你开始使用 MSON ，你会发现自己想重用某些常用或嵌套数据结构组件。
这可以通过`## Data Structures`章节部分完成。
然后属性章节部分可以通过名字引用数据结构或其他资源章节中定义的数据结构。

For example, using the polls API question collection resource, we can split out
the `Question` and `Choice` objects:

例如，使用投票 API 问题集合资源，我们可以分割出的`Question`和`Choice`对象：

```apib
### List All Questions [GET]
+ Response 200 (application/json)

    + Attributes (array[Question])

## Data Structures

### Question
+ question: Favourite programming language? (required)
+ published_at: `2014-11-11T08:40:51.620Z` (required)
+ url: /questions/1 (required)
+ choices (array[Choice], required)

### Choice
+ choice: Javascript (required)
+ url: /questions/1/choices/1 (required)
+ votes: 2048 (number, required)

```

## Relation Types
## 关系类型

Actions in a blueprint can define a semantic domain-specific meaning by
defining a relation type using a `+ Relation` section. This means that an
action can have a specific meaning regardless of its URI or name, and allows
clients to be built based on the domain of the API rather than specific URIs.

在 blueprint 操作可以通过定义关系`+ Relation`部分的关系类型定义语义域特定含义。
这意味着，一个动作可以具有特定的含义，无论它的 URI 或名称是什么，并且允许客户端基于 API 的域而不是特定的 URI 来构建。

For example, in the polls API:

例如，在民意调查API中：

```apib
## Question [/question/{id}]
### View a Question Detail [GET]
+ Relation: self

### Delete a Question [DELETE]
+ Relation: delete

## Questions Collection [/questions]
### List All Questions [GET]
+ Relation: self
```

A server or client implementation can now use this information to handle the
specific API resource and action URIs. Please see the
[Web Linking RFC 5988](https://tools.ietf.org/html/rfc5988) and the
[IANA Link Relation Types](http://www.iana.org/assignments/link-relations/link-relations.xhtml) for
more information.

服务器或客户端的实现，现在可以使用这些信息来处理特定的 API 资源和操作 URI 。
更多信息请请查看
[Web Linking RFC 5988](https://tools.ietf.org/html/rfc5988)和
[IANA Link Relation Types](http://www.iana.org/assignments/link-relations/link-relations.xhtml)

## Conclusion
## 结论

This tutorial has covered some advanced API Blueprint topics.
For more in-depth information and other advanced topics,
please see the [API Blueprint Specification](https://github.com/apiaryio/api-blueprint/blob/master/API%20Blueprint%20Specification.md).

本教程涵盖了 API Blueprint 的一些高级特性。
为了更深入的学习其他高级特性，请查看
[API Blueprint 规范](https://github.com/apiaryio/api-blueprint/blob/master/API%20Blueprint%20Specification.md).
