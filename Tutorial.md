# API Blueprint Tutorial
# API Blueprint 教程

Welcome to an API Blueprint Tutorial! This tutorial will take you through the
basics of the API Blueprint language. We’re going to build an API blueprint
step by step for a service called Polls – a simple API allowing consumers to
view polls and vote in them. You can take a look at the
[full version][Poll API Blueprint] of the blueprint used in this tutorial for
reference.

欢迎到一个 API Blueprint 教程！本教程将带您了解 API Blueprint 语言的基础知识。
我们将一步一步建造一个名字叫Polls的 API blueprint 服务 - 一个简单的API，允许用户投票和查看投票。
你可以参照[完整版本][Poll API Blueprint]学习本教程。（PS：Blueprint可翻译为蓝图）

> **Note:** **Additional API Blueprint Resources**
> **注意：** **其他 API Blueprint 资源**
>
> + [Language Specification][specification]
> + [语言规范][specification]
> + [Examples][API Blueprint Examples]
> + [例子][API Blueprint Examples]
> + [Glossary of Terms][API Blueprint Glossary of Terms]
> + [专业术语][API Blueprint Glossary of Terms]
> + [API Blueprint Map][map]
> + [API Blueprint 地图][map]
> + [Tools for API Blueprint][Tooling Section]
> + [API Blueprint 工具][Tooling Section]

## API Blueprint
## API Blueprint

The first step for creating a blueprint is to specify the API Name and
metadata. This step looks as follows:

创建 Blueprint 的第一步是要指定API名称和元数据。此步骤如下所示：

```apib
FORMAT: 1A

# Polls

Polls is a simple API allowing consumers to view polls and vote in them.
```

## Metadata
## 元数据

The blueprint starts with a metadata section. In this case we have specified
that `FORMAT` has the value of `1A`. The format keyword denotes the version of
the API Blueprint.

blueprint 通过元数据开始。在这种情况下，我们已指定`FORMAT`的值为`1A`。
格式关键字表示 API Blueprint 的版本。

## API Name & Description
## API 名称&描述

The first heading in the blueprint serves as the name of your API, which in
this case is "Polls". Headings start with one or more `#` symbols followed by a
title. The API Name here uses one hash to distinguish it as the first level.
The number of `#` you use will determine the level of the heading.

在 blueprint 的第一个标题将作为您的 API 名称，在例子中“Polls”即名称。
通过一个或多个`#`号后字符串形成一个标题。这里的 API 名称使用哈希来区分其他一级标题。
使用`#`的数目将确定的标题的等级。

Following the heading is a description of the API. You may use further headings
to break up the description section.

紧跟标题的是API的描述说明。您可以使用进一步标题头打破描述部分。

## Resource Groups
## 资源组

Now it's time to start documenting the API resources. Using the `Group` keyword
at the start of a heading, we've created a group of related resources.

现在是时候开始记录 API 资源了。使用`Group`关键词标题开始，我们已经创建了一组相关的资源。

```apib
# Group Questions

Resources related to questions in the API.
```

## Resource
## 资源

Within the questions resource group, we have a resource called "Question
Collection". This resource allows you to view a list of questions. The heading
specifies the URI used to access the resource inside of square brackets at the
end of the heading.

在这些问题资源组，我们有一个所谓的“问题集合”资源。此资源允许您查看的问题清单。
在标题结束后面的方括号内使用 URI 指定用于访问的资源。

```apib
## Question Collection [/questions]
```

### Actions
### 操作

API Blueprint allows you to specify each action you may make on a resource. An
action is specified with a sub-heading inside of a resource with the name of
the action followed by the HTTP method.

API Blueprint 允许你指定资源上的每个操作。
在资源内部子标题中指定操作名称和HTTP方法。

```apib
### List All Questions [GET]
```

An action should include at least one response from the server which must
include a status code and may contain a body. A response is defined as a list
item within an action. Lists are created by preceding list items with either a
`+`, `*` or `-`.

一个操作应该至少包含一个从服务器返回的响应，其中必须包括一个状态码，可以包含一个响应体。
响应被定义操作中的一个列表项。列表由列表项与`+`, `*` 或 `-`组合而来。

This action returns a `200` status code along with a JSON body.

这个操作返回状态码`200`并附带JSON响应体。

```apib
+ Response 200 (application/json)

        [
            {
                "question": "Favourite programming language?",
                "published_at": "2014-11-11T08:40:51.620Z",
                "url": "/questions/1",
                "choices": [
                    {
                        "choice": "Swift",
                        "url": "/questions/1/choices/1",
                        "votes": 2048
                    }, {
                        "choice": "Python",
                        "url": "/questions/1/choices/2",
                        "votes": 1024
                    }, {
                        "choice": "Objective-C",
                        "url": "/questions/1/choices/3",
                        "votes": 512
                    }, {
                        "choice": "Ruby",
                        "url": "/questions/1/choices/4",
                        "votes": 256
                    }
                ]
            }
        ]
```

> **Note:** Specifying the media type after the response status code generates
> a `Content-Type` HTTP header. You do not have to explicitly specify the
> `Content-Type` header.
> **注意：** 在响应状态代码之后指定媒体类型生成HTTP`Content-Type`头。
> 你不必明确指定`Content-Type`头

The polls resource has a second action which allows you to create a new
question. This action includes a description showing the structure you would
send to the server to perform this action.

polls资源有第二个操作，允许你创建一个新的问题。
这个操作包括发送到服务器用来执行此操作的结构和操作的描述。

```apib
### Create a New Question [POST]

You may create your own question using this action. It takes a JSON object
containing a question and a collection of answers in the form of choices.

+ question (string) - The question
+ choices (array[string]) - A collection of choices.
```

This action takes a JSON payload as part of the request as follows:

这个操作需要一个请求的一部分 JSON payload 如下：

```apib
+ Request (application/json)

            {
                "question": "Favourite programming language?",
                "choices": [
                    "Swift",
                    "Python",
                    "Objective-C",
                    "Ruby"
                ]
            }
```

This example returns a `201` status code, along with HTTP headers and a body.

这个例子返回`201`状态码，附带 HTTP 头和 HTTP 体。

```apib
+ Response 201 (application/json)

    + Headers

            Location: /questions/1

    + Body

                {
                    "question": "Favourite programming language?",
                    "published_at": "2014-11-11T08:40:51.620Z",
                    "url": "/questions/1",
                    "choices": [
                        {
                            "choice": "Swift",
                            "url": "/questions/1/choices/1",
                            "votes": 0
                        }, {
                            "choice": "Python",
                            "url": "/questions/1/choices/2",
                            "votes": 0
                        }, {
                            "choice": "Objective-C",
                            "url": "/questions/1/choices/3",
                            "votes": 0
                        }, {
                            "choice": "Ruby",
                            "url": "/questions/1/choices/4",
                            "votes": 0
                        }
                    ]
                }
```

The next resource is “Question”, which represents a single question.

下一个资源是“Question”，表示单个问题。

```apib
## Question [/questions/{question_id}]
```

### URI Template
### URI 模板

The URI for the “Question” resource uses a variable component, expressed by
[URI Template][]. In this case, there is an ID variable called `question_id`,
represented in the URI template as `{question_id}`.

对于“Question”资源通过使用[URI 模板][URI Template]表示了一个可变的部分，
在这种情况下，有一个名为`question_id`的ID变量，在 URI 模板中用`{question_id}`表示。

<a id="uri-parameters"></a>
### URI Parameters
### URI 参数

URI parameters should describe the URI using a list of Parameters. For
“Question” it would be as follows:

URI 参数应该使用参数列表描述。对于“Question”应该如下：

```apib
+ Parameters
    + question_id (number) - ID of the Question in the form of an integer
```

The `question_id` variable of the URI template is a parameter for every action
on this resource. It's defined here using an arbitrary type `number`, followed
by a description for the parameter.

URI 模板中的`question_id`变量是这个资源每个操作的参数。
在这里使用`number`类型定义，后面接着参数的描述。

> Refer to API Blueprint Specification's [URI Parameters Section][] for more
> examples.
> 请参阅 API Blueprint 规范的 [URI URI参数章节][URI Parameters Section] 以更多的例子。

### Actions
### 操作

This resource has an action to retrieve the question's detail.
该资源有一个操作来取得这个问题的细节。

```apib
### View a Questions Detail [GET]

+ Response 200 (application/json)

            {
                "question": "Favourite programming language?",
                "published_at": "2014-11-11T08:40:51.620Z",
                "url": "/questions/1",
                "choices": [
                    {
                        "choice": "Swift",
                        "url": "/questions/1/choices/1",
                        "votes": 2048
                    }, {
                        "choice": "Python",
                        "url": "/questions/1/choices/2",
                        "votes": 1024
                    }, {
                        "choice": "Objective-C",
                        "url": "/questions/1/choices/3",
                        "votes": 512
                    }, {
                        "choice": "Ruby",
                        "url": "/questions/1/choices/4",
                        "votes": 256
                    }
                ]
            }
```

#### Response Without a Body
#### 不含响应体的响应

This resource has a delete action. The server will return a 204 response
without a body.

该资源有一个删除操作。服务器将返回没有响应体的204响应。

```apib
### Delete [DELETE]

+ Response 204
```

## Complete Blueprint
## 完整的Blueprint

You can find an [implementation](http://github.com/apiaryio/polls-api) of this
API at http://polls.apiblueprint.org/ along with the complete
[Poll API Blueprint][] in the [API Blueprint Examples][] repository. You can
also enjoy it [rendered on Apiary][].

你可以在[API Blueprint 例子][API Blueprint Examples]资源库
查看 http://polls.apiblueprint.org/ API的完整[Poll API Blueprint][][实现](http://github.com/apiaryio/polls-api)
你也可以查看在[Apiary][rendered on Apiary]上的呈现。

> **Note:** Take a look at the [API Blueprint Glossary of Terms][] if you need
> clarification of some of the terms used though this document.
> **注意：** 看看[API Blueprint专业术语][API Blueprint Glossary of Terms]，如果你需要搞懂本文档中使用的术语。

## API Blueprint Tools
## API Blueprint 工具

Visit the [Tooling Section][] of [apiblueprint.org][] to find tools to use with
API Blueprints.

查看[apiblueprint.org][]的[工具章节][Tooling Section]来应用其中的工具。

[GitHub Gists]:                     https://gist.github.com
[API Blueprint Glossary of Terms]:  https://github.com/apiaryio/api-blueprint/blob/master/Glossary%20of%20Terms.md
[API Blueprint Identifier]:         https://github.com/apiaryio/api-blueprint/blob/1A/API%20Blueprint%20Specification.md#Identifiers
[HTTP Request Method]:              https://github.com/for-GET/know-your-http-well/blob/master/methods.md
[status code]:                      https://github.com/for-GET/know-your-http-well/blob/master/status-codes.md
[message-headers]:                  https://github.com/for-GET/know-your-http-well/blob/master/headers.md
[payload]:                          https://github.com/apiaryio/api-blueprint/blob/master/Glossary%20of%20Terms.md#payload
[URI Template]:                     https://github.com/apiaryio/api-blueprint/blob/master/Glossary%20of%20Terms.md#uri-template
[URI Parameters Section]:           https://github.com/apiaryio/api-blueprint/blob/master/API%20Blueprint%20Specification.md#def-uriparameters-section
[Markdown pre-formatted code blocks]: http://daringfireball.net/projects/markdown/syntax#precode
[URI Parameters]: #uri-parameters
[API Blueprint Examples]: https://github.com/apiaryio/api-blueprint/tree/master/examples
[Poll API Blueprint]: https://raw.github.com/apiaryio/api-blueprint/master/examples/Polls%20API.md
[Apiary]: http://docs.pollsapi.apiary.io
[工具章节]: http://apiblueprint.org/#tooling
[specification]: https://github.com/apiaryio/api-blueprint/blob/master/API%20Blueprint%20Specification.md
[map]: https://github.com/apiaryio/api-blueprint/wiki/API-Blueprint-Map
