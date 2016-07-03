---

Author: z@apiary.io
Version: 1A9

---

# API Blueprint
#### Format 1A revision 9

## [I. API Blueprint Language](#def-api-blueprint-language)
+ [Introduction](#def-introduction)
+ [API Blueprint](#def-api-blueprint)
+ [API Blueprint document](#def-api-blueprint-document)
+ [Blueprint section](#def-blueprint-section)
    + [Section types](#def-section-types)
    + [Section structure](#def-section-structure)
    + [Keywords](#def-keywords)
    + [Identifier](#def-identifier)
    + [Description](#def-description)
    + [Nested sections](#def-nested-sections)

## [II. Sections Reference](#def-sections-reference)

### Abstract
+ [Named section](#def-named-section)
+ [Asset section](#def-asset-section)
+ [Payload section](#def-payload-section)

### Section Basics
+ [Metadata section](#def-metadata-section)
+ [API name & overview section](#def-api-name-section)
+ [Resource group section](#def-resourcegroup-section)
+ [Resource section](#def-resource-section)
+ [Resource model section](#def-model-section)
+ [Schema section](#def-schema-section)
+ [Action section](#def-action-section)
+ [Request section](#def-request-section)
+ [Response section](#def-response-section)
+ [URI parameters section](#def-uriparameters-section)
+ [Attributes section](#def-attributes-section)
+ [Headers section](#def-headers-section)
+ [Body section](#def-body-section)

### Going Further
+ [Data Structures section](#def-data-structures)
+ [Relation section](#def-relation-section)


## [III. Appendix](#def-appendix)
+ [URI Templates](#def-uri-templates)


## [I. API Blueprint 语言](#def-api-blueprint-language)
+ [引言](#def-introduction)
+ [API Blueprint](#def-api-blueprint)
+ [API Blueprint 文档](#def-api-blueprint-document)
+ [Blueprint 片段](#def-blueprint-section)
    + [片段类型](#def-section-types)
    + [片段结构](#def-section-structure)
    + [关键字](#def-keywords)
    + [标识符](#def-identifier)
    + [描述](#def-description)
    + [片段嵌套](#def-nested-sections)

## [II. 片段引用](#def-sections-reference)

### 抽象
+ [命名片段](#def-named-section)
+ [资产片段](#def-asset-section)
+ [Payload 片段](#def-payload-section)

### 基本片段
+ [元数据片段](#def-metadata-section)
+ [API 命名 & 概述片段](#def-api-name-section)
+ [资源分组片段](#def-resourcegroup-section)
+ [资源片段](#def-resource-section)
+ [资源模型片段](#def-model-section)
+ [模式片段](#def-schema-section)
+ [操作片段](#def-action-section)
+ [请求片段](#def-request-section)
+ [响应片段](#def-response-section)
+ [URI 参数片段](#def-uriparameters-section)
+ [属性片段](#def-attributes-section)
+ [消息头片段](#def-headers-section)
+ [消息体片段](#def-body-section)

### 深入学习
+ [数据结构片段](#def-data-structures)
+ [关系片段](#def-relation-section)


## [III. 附录](#def-appendix)
+ [URI 模板](#def-uri-templates)

---

<br>

<a name="def-api-blueprint-language"></a>
# I. API Blueprint Language
# I. API Blueprint 语言

<a name="def-introduction"></a>
## Introduction
## 引言
This documents is a full specification of the API Blueprint format. For a less
formal introduction to API Blueprint visit the
[API Blueprint Tutorial](Tutorial.md) or check some of the [examples][].

此文档是 API Blueprint 格式的完整规范。
对于非正式的介绍请访问[API Blueprint 教程](Tutorial.md)或查看[例子][examples]。

<a name="def-api-blueprint"></a>
## API Blueprint
## API Blueprint
API Blueprint is a documentation-oriented web API description language. The
API Blueprint is essentially a set of semantic assumptions laid on top of the
Markdown syntax used to describe a web API.

API Blueprint 是一个面向文档的 Web API 描述语言。
API Blueprint 实际上是一组语义假设构建在 Markdown 语法之上来描述一个 Web API。

In addition to the regular [Markdown syntax][], API Blueprint conforms to the
[GitHub Flavored Markdown syntax][].

除了常规的[Markdown 语法][Markdown syntax]，API Blueprint符合[GitHub风格Markdown语法][GitHub Flavored Markdown syntax]。

<a name="def-api-blueprint-document"></a>
## API Blueprint document
## API Blueprint 文档
An API Blueprint document – a blueprint – is a plain text Markdown document
describing a Web API in whole or in part. The document is structured into
logical **sections**. Each section has its distinctive meaning, content and
position in the document.

一个 API Blueprint 文档 - 是蓝图 - 是纯文本的 Markdown 文档描述全部或部分 Web API。
文档结构通过符合逻辑的 **片段** 来组织。每个片段都有其独特的意义、确定的位置和确定的内容。

General section definition and structure is discussed in detail later in the
[Blueprint section](#def-blueprint-section) chapter.

通用片段和结构的详细信息在[Blueprint 片段](#def-blueprint-section)之后讨论。

All of the blueprint sections are optional. However, when present, a section
**must** follow the API Blueprint **document structure**.

所有的 blueprint 片段是可选的。然而，当存在时，一个片段 **必须** 遵循 API Blueprint **文档结构**。

### Blueprint document structure
### Blueprint 文档结构

+ [`0-1` **Metadata** section](#def-metadata-section)
+ [`0-1` **API Name & overview** section](#def-api-name-section)
+ [`0+` **Resource** sections](#def-resource-section)
    + [`0-1` **URI Parameters** section](#def-uriparameters-section)
    + [`0-1` **Attributes** section](#def-attributes-section)
    + [`0-1` **Model** section](#def-model-section)
        + [`0-1` **Headers** section](#def-headers-section)
        + [`0-1` **Attributes** section](#def-attributes-section)
        + [`0-1` **Body** section](#def-body-section)
        + [`0-1` **Schema** section](#def-schema-section)
    + [`1+` **Action** sections](#def-action-section)
        + [`0-1` **Relation** section](#def-relation-section)
        + [`0-1` **URI Parameters** section](#def-uriparameters-section)
        + [`0-1` **Attributes** section](#def-attributes-section)
        + [`0+` **Request** sections](#def-request-section)
            + [`0-1` **Headers** section](#def-headers-section)
            + [`0-1` **Attributes** section](#def-attributes-section)
            + [`0-1` **Body** section](#def-body-section)
            + [`0-1` **Schema** section](#def-schema-section)
        + [`1+` **Response** sections](#def-response-section)
            + [`0-1` **Headers** section](#def-headers-section)
            + [`0-1` **Attributes** section](#def-attributes-section)
            + [`0-1` **Body** section](#def-body-section)
            + [`0-1` **Schema** section](#def-schema-section)
+ [`0+` **Resource Group** sections](#def-resourcegroup-section)
    + [`0+` **Resource** sections](#def-resource-section) (see above)
+ [`0+` **Data Structures** section](#def-data-structures)


+ [`0-1` **元数据** 片段](#def-metadata-section)
+ [`0-1` **API 命名 & 概述** 片段](#def-api-name-section)
+ [`0+` **资源** 片段](#def-resource-section)
    + [`0-1` **URI 参数** 片段](#def-uriparameters-section)
    + [`0-1` **属性** 片段](#def-attributes-section)
    + [`0-1` **模型** 片段](#def-model-section)
        + [`0-1` **消息头** 片段](#def-headers-section)
        + [`0-1` **属性** 片段](#def-attributes-section)
        + [`0-1` **消息体** 片段](#def-body-section)
        + [`0-1` **模式** 片段](#def-schema-section)
    + [`1+` **操作** 片段](#def-action-section)
        + [`0-1` **关系** 片段](#def-relation-section)
        + [`0-1` **URI 参数** 片段](#def-uriparameters-section)
        + [`0-1` **属性** 片段](#def-attributes-section)
        + [`0+` **请求** 片段](#def-request-section)
            + [`0-1` **请求消息头** 片段](#def-headers-section)
            + [`0-1` **请求属性** 片段](#def-attributes-section)
            + [`0-1` **请求消息体片段** 片段](#def-body-section)
            + [`0-1` **请求模式** 片段](#def-schema-section)
        + [`1+` **响应** 片段](#def-response-section)
            + [`0-1` **响应消息头** 片段](#def-headers-section)
            + [`0-1` **响应属性** 片段](#def-attributes-section)
            + [`0-1` **响应消息体** 片段](#def-body-section)
            + [`0-1` **响应模式** 片段](#def-schema-section)
+ [`0+` **资源组** 片段](#def-resourcegroup-section)
    + [`0+` **资源** 片段](#def-resource-section) （同上）
+ [`0+` **数据结构** 片段](#def-data-structures)


> **NOTE:** The number prior to a section name denotes the allowed number of
> the section occurrences.

> **注意：** 片段名称前的数字表示片段允许出现的次数。

> **NOTE:** Refer to [Sections Reference](#def-sections-reference) for
> description of a specific section type.

> **注意：** 请参阅[片段引用](#def-sections-reference)了解特定片段的描述。

<a name="def-blueprint-section"></a>
## Blueprint section
## Blueprint 片段
A _Section_ represents a logical unit of an API Blueprint. For example: an API
overview, a group of resources or a resource definition.

一个 _片段_ 代表 API Blueprint 的一个逻辑单元。例如：一个 API 概述，一组资源或一个资源定义。

In general a section is **defined** using a **keyword** in a Markdown entity.
Depending on the type of section the keyword is written either as a Markdown
header entity or in a list item entity.

通常片段的 **定义** 通过在 Markdown 实体中使用 **关键字**。
片段依赖的类型通过关键字被写入到 Markdown 头实体中或列表项实体中。

A section definition **may** also contain additional variable components such
as its **identifier** and additional modifiers.

一个片段定义还 **可能** 包含额外的变量组件例如 **标识符** 和附加修饰符。

> **NOTE**: There are two special sections that are recognized by their
> position in the document instead of a keyword: The [Metadata section]() and
> the [API Name & Overview section](). Refer to the respective section entry
> for details on its definition.

> **注意：** 两个特殊的片段，由文档位置识别，而不是关键字：
> [元数据片段](Metadata section)和[API 命名 & 概述片段](API Name & Overview section)。
> 请参考各自的片段实体获得详细定义。

#### Example: Header-defined sections
#### 例子: 通过标题头定义片段

    # <keyword>

     ...

    # <keyword>

     ...


> **NOTE:** While this specification uses "atx" -style headers (using `#`s)
>  you can also use "Setext" [header syntax][] interchangeably:
>
>     <keyword>
>     =========
>
>     ...
>
>     <keyword>
>     =========
>
>     ...

> **注意：** 尽管本规范使用 “ATX”风格的标题（使用`#`），
> 你也可以用 “Setext” 风格的 [标题头语法][header syntax] 替换:
>
>     <keyword>
>     =========
>
>     ...
>
>     <keyword>
>     =========
>
>     ...

#### Example: List-defined sections
#### 例子: 通过列表定义片段

    + <keyword>

     ...

    + <keyword>

     ...

> **NOTE:**  While this specification uses pluses (`+`) as list markers you can
> use any Markdown [list syntax][] using asterisks (`*`), pluses (`+`) and
> hyphens (`-`) interchangeably:
>
>     * <keyword>
>
>     ...
>
>     - <keyword>
>
>     ...

> **注意：**  尽管本规范使用 (`+`) 风格的列表，
> 你也可以用 Markdown (`*`) 或 (`+`) 风格的 [列表语法][list syntax] 替换:
>
>     * <keyword>
>
>     ...
>
>     - <keyword>
>
>     ...

<a name="def-section-types"></a>
### Section types
### 片段类型
There are several types of API Blueprint sections. You can find the complete
listing of the section types in the
[Section Reference](#def-sections-reference).

这里有几种类型的 API Blueprint 片段。你可以在[片段引用](#def-sections-reference)中找到类型参考的完整列表。

**The Blueprint section chapter discusses the section syntax in general.**
**A specific section type may conform only to some parts of this general syntax.**
Always refer for respective section reference for details on its syntax.

**Blueprint 片段章节讨论片段语法的通用性。**
**特殊的片段类型可能只符合通用语法的某些部分。**
请务必参阅各个片段语法的详细语法参考。

<a name="def-section-structure"></a>
### Section structure
### 片段结构
A general structure of an API Blueprint section defined by a **keyword**
includes an **identifier** (name), section **description** and **nested
sections** or a specifically formatted content.

通用 API Blueprint 片段结构由 **关键字** 定义，包括一个 **标识符**（名称），
片段 **描述** 和 **嵌套片段** 或特定格式的内容。

#### Example: Header-defined section structure
#### 例子: 标题头定义片段结构

    # <keyword> <identifier>

    <description>

    <specific content>

    <nested sections>

#### Example: List-defined section structure
#### 例子: 列表定义片段结构

    + <keyword> <identifier>

        <description>

        <specific content>

        <nested sections>

<a name="def-keywords"></a>
### Keywords
### 关键字
Following reserved keywords are used in section definitions:

以下保留关键字在片段定义中使用：

#### Header keywords
#### 标题头关键字
- `Group`
- `Data Structures`
- [HTTP methods][httpmethods] (e.g. `GET, POST, PUT, DELETE`...)
- [URI templates][uritemplate] (e.g. `/resource/{id}`)
- Combinations of an HTTP method and URI Template (e.g. `GET /resource/{id}`)


- `Group` 分组
- `Data Structures` 数据结构
- [HTTP 方法][httpmethods] （例如`GET, POST, PUT, DELETE`...）
- [URI 模板][uritemplate] （例如`/resource/{id}`）
- 一个 HTTP 方法和 URI 模板的组合 （例如`GET /resource/{id}`）

#### List keywords
#### 关键字列表
- `Request`
- `Response`
- `Body`
- `Schema`
- `Model`
- `Header` & `Headers`
- `Parameter` & `Parameters`
- `Values`
- `Attribute` & `Attributes`
- `Relation`

> **NOTE: Avoid using these keywords in other Markdown headers or lists**

> **注意：避免在其他 Markdown 标题或列表使用这些关键字**

> **NOTE:** With the exception of HTTP methods keywords the section keywords
> are case insensitive.

> **注意：** HTTP 方法关键字是特例，片段关键字忽略大小写。

<a name="def-identifier"></a>
### Identifier
### 标识符
A section definition **may** or **must** include an identifier of the section.
An **identifier is any non-empty combination of any character except `[`, `]`,
`(`, `)` and newline characters**.

片段定义 **可以** 或 **必须** 包括片段标识符。
一个 **标识符是一个非空任意字符的组合，除`[`，`]`,`(`, `)`和换行符**。

An identifier **must not** contain any of the [keywords](#def-keywords).

标识符 **不能** 包含任何[关键字](#def-keywords)。

#### Example
#### 例子

```
Adam's Message 42
```

```
my-awesome-message_2
```


<a name="def-description"></a>
### Description
### 描述
A section description is any arbitrary Markdown-formatted content following the
section definition.

一个片段描述是在片段定义之后的任意 Markdown 格式内容。

It is possible to use any Markdown header or list item in a section description
as long as it does not clash with any of the
[reserved keywords](#def-keywords).

仍然可以在片段描述中使用任何 Markdown 标题头或 Markdown 列表项，只要不与任何[保留关键](#def-keywords)冲突。

> **NOTE:** It is considered good practice to keep the header level nested
> under the actual section.

> **注意：** 最好的做法，是将描述中的标题头嵌套在实际片段下。

<a name="def-nested-sections"></a>
### Nested sections
### 片段嵌套
A section **may** contain another nested section(s).

一个片段 **可能** 包含其他嵌套片段。

Depending on the nested section type, to nest a section simply increase its
header level or its list item indentation. Anything between the section start
and the start of following section at the same level is considered to be part
of the section.

根据嵌套片段类型，嵌套片段只是简单的增加其标题级别或其列表项缩进。
在同级别2个片段之间的任何东西被认为是前者的一部分。

What sections can be nested and where depends upon the section in case, as
described in the relevant section's entry.

哪些片段可以在哪里嵌套取决于片段的上级，如上所述在相关片段实体中。

#### Example: Nested header-defined section
#### 例子：嵌套标题头片段的定义

    # <section definition>

     ...

    ## <nested section definition>

     ...

#### Example: Nested list-defined section
#### 例子：嵌套列表片段的定义

    + <section definition>

         ...

        + <nested section definition>

         ...

> **NOTE:** While not necessary it is a good habit to increase the level of a
> nested section markdown-header.

> **注意：** 没有必要增加一个嵌套片段 markdown 标题头的缩进级别。

> **NOTE:** A markdown-list section is always considered to be nested under the
> preceding markdown-header section.

> **注意：** 一个 markdown 列表片段始终被认为嵌套在前面的 markdown 标题头片段。

---

<a name="def-sections-reference"></a>
# II. Sections Reference
# II. 片段引用
> **NOTE:** Sections marked as "Abstract" serve as a base for other sections
> and as such they **cannot** be used directly.

> **注意：** 标记为“Abstract”的片段作为其他片段的服务，因此它们 **不能** 直接使用。


# Abstract
# 抽象

<a name="def-named-section"></a>
## Named section
## 命名片段
- **Abstract**
- **Parent sections:** vary, see descendants
- **Nested sections:** vary, see descendants
- **Markdown entity:** header, list
- **Inherits from**: none

- **抽象的**
- **父级片段:** 不同，查看后续章节
- **子级（嵌套）片段:** 不同，查看后续章节
- **Markdown 实体:** 标题头，列表
- **继承自**: 无

#### Definition
#### 定义
Defined by a [keyword](#def-keywords) followed by an optional section name -
[identifier](#def-identifier) in a Markdown header or list entity.

在 Markdown 标题头或列表实体中，通过[关键字](#def-keywords)后面跟着可选的片段名称 - [标识符](#def-identifier)而定义。

```
# <keyword> <identifier>
```

```
+ <keyword> <identifier>
```

#### Description
#### 描述
Named section is the base section for most of the API Blueprint sections. It
conforms to the [general section](#def-section-structure) and as such it is
composed of a section name (identifier), description and nested sections or
specific formatted content (see descendants descriptions).

命名片段是大多数 API Blueprint 的基本片段。
它符合[通用片段](#def-section-structure)，
因此它是由片段名称（标识），描述，嵌套片段和具体格式化内容组成（查看后续描述）。

#### Example
#### 例子

    # <keyword> Section Name
    This the `Section Name` description.

    - one
    - **two**
    - three

    <nested sections> |  <formatted content>

---

<a name="def-asset-section"></a>
## Asset section
## 资产片段
- **Abstract**
- **Parent sections:** vary, see descendants
- **Nested sections:** none
- **Markdown entity:** list
- **Inherits from**: none

- **抽象的**
- **父级片段:** 不同，查看后续章节
- **子级（嵌套）片段:** 无
- **Markdown 实体:** 列表
- **继承自**: 无

#### Definition
#### 定义
Defined by a [keyword](#def-keywords) in Markdown list entity.

通过[关键字](#def-keywords)在 Markdown 列表实体中定义。

    + <keyword>

#### Description
#### 描述
The asset section is the base section for atomic data in API Blueprint. The content
of this section is expected to be a
[pre-formatted code block](http://daringfireball.net/projects/markdown/syntax#precode).

资产片段是描述 API Blueprint 原子数据的片段。
其内容预计是一个
[预格式化的代码块](http://daringfireball.net/projects/markdown/syntax#precode)。

#### Example
#### 例子

    + <keyword>

            {
                "message": "Hello"
            }

#### Example: Fenced code blocks
#### 例子：使用围栏代码块

    + <keyword>

        ```
        {
            "message": "Hello"
        }
        ```

---

<a name="def-payload-section"></a>
## Payload section
## Payload 片段
- **Abstract**
- **Parent sections:** vary, see descendants
- **Nested sections:** [`0-1` Headers section](#def-headers-section), [`0-1` Attributes section](#def-attributes-section), [`0-1` Body section](#def-body-section), [`0-1` Schema section](#def-schema-section)
- **Markdown entity:** list
- **Inherits from**: [Named section](#def-named-section)

- **抽象的**
- **父级片段:** 不同，查看后续章节
- **子级（嵌套）片段:** [`0-1` 标题头片段](#def-headers-section), [`0-1` 属性片段](#def-attributes-section), [`0-1` 消息体片段](#def-body-section), [`0-1` 模式片段](#def-schema-section)
- **Markdown 实体:** 列表
- **继承自**: [命名片段](#def-named-section)

#### Definition
#### 定义
Defined by a [keyword](#def-keywords) in Markdown list entity. The keyword **may** be followed by identifier.
The definition **may** include payload's media-type enclosed in braces.

在 Markdown 列表实体中由[关键字](#def-keywords)定义。关键字之后 **可能** 跟随标识符。
该定义 **可能** 包括小括号括起来的 payload 媒体类型。

    + <keyword> <identifier> (<media type>)

> **NOTE:** Refer to descendant for the particular section type definition.

> **注意：** 请参阅后面的特定片段类型定义。

#### Description
#### 描述
Payload sections represent the information transferred as a payload of an HTTP
request or response messages. A Payload consists of optional meta information
in the form of HTTP headers and optional content in the form of an HTTP body.

Payload 片段代表信息从 HTTP 请求或响应消息转换而来的 payload 信息。
Payload 由 HTTP 头中可选的媒体信息和 HTTP 体中的内容组成。

Furthermore, in API Blueprint context, a payload includes its description,
description of its message-body attributes and a message-body validation
schema.

此外，在 API Blueprint 上下文中，payload 包括它的描述，描述其消息主体属性和消息正文的验证方法。

A payload **may** have its media type associated. A payload's media type
represents the metadata received or sent in the form of a HTTP `Content-Type`
header. When specified a payload **should** include nested
[Body section](#def-body-section).

payload **可以** 有与其相关联的媒体类型。
payload 的媒体类型表示可接受媒体类型数据或在 HTTP `Content-Type`头中发送的媒体类型数据。
当指定 payload **应该** 包括嵌套的[消息体片段](#def-body-section)。

This section **should** include at least one of the following nested sections:

本片段 **应该** 至少包含以下嵌套部分之一：

- [`0-1` Headers section](#def-headers-section)
- [`0-1` 消息头片段](#def-headers-section)
- [`0-1` Attributes section](#def-attributes-section)
- [`0-1` 属性片段](#def-attributes-section)
- [`0-1` Body section](#def-body-section)
- [`0-1` 消息体片段片段](#def-body-section)
- [`0-1` Schema section](#def-schema-section)
- [`0-1` 模式片段](#def-schema-section)

If there is no nested section the content of the payload section is considered
as content of the [Body section](#def-body-section).

如果 payload 片段中没有嵌套部分，则其内容被认为是[消息体片段](#def-body-section)。

#### Relation of Body, Schema and Attributes sections
#### 主体关系，模式和属性片段
Each of body, schema and attributes sections describe a message payload's body.
These descriptions **should** be consistent, not violating each other. When
multiple body descriptions are provided they **should** be prioritized as
follows:

每个消息体，模式和属性片段描述了一个 payload 消息体。
这些描述 **应该** 是一致的，而不是相互违背的。
当要提供多个主体的描述时，**应该** 优先考虑如下结构：

1. For resolving message-body schema
    1. Schema section
    2. Attributes section
    3. Body section

1. 为了解决消息主体模式
    1. 模式片段
    2. 属性片段
    3. 消息体片段

2. For resolving message-body example
    1. Body section
    2. Attributes section
    3. Schema section

1. 为了解决消息主体例子
    1. 消息体片段
    2. 属性片段
    3. 模式片段

#### Referencing
#### 引用
Instead of providing a payload section content, a
[model payload section](#def-model-section) can be referenced using the
Markdown implicit [reference syntax][]:

为代替提供 payload 片段内容，可以使用 Markdown 隐式[引用语法][reference syntax]引用 payload [模型片段](#def-model-section)：

    [<identifier>][]

#### Example
#### 例子

    + <keyword> Payload Name (application/json)

        This the `Payload Name` description.

        + Headers

         ...

        + Body

         ...

        + Schema

        ...

#### Example: Referencing model payload
#### 例子：引用模型的 payload

    + <keyword> Payload Name

        [Resource model identifier][]

---


# Section Basics
# 基本片段


<a name="def-metadata-section"></a>
## Metadata section
## 元数据片段
- **Parent sections:** none
- **Nested sections:** none
- **Markdown entity:** special
- **Inherits from**: none

- **父级片段:** 无
- **子级（嵌套）片段:** 无
- **Markdown 实体:** 特别
- **继承自**: 无

#### Definition
#### 定义
Key-value pairs. Each key is separated from its value by a colon (`:`). One
pair per line. Starts at the beginning of the document and ends with the first
Markdown element that is not recognized as a key-value pair.

键-值对。每个键和值由冒号（`:`）分隔。每行一对。
于文档的开头，到第一个 Markdown 元素结束，这之间的信息会被识别为键-值对。

#### Description
#### 描述
Metadata keys and their values are tool-specific. Refer to relevant tool
documentation for the list of supported keys.

元数据键和值是专用工具。请参阅相关的工具文档支持列表。

#### Example
#### 例子

    FORMAT: 1A
    HOST: http://blog.acme.com

---

<a name="def-api-name-section"></a>
## API name & overview section
## API 命名 & 概述片段
- **Parent sections:** none
- **Nested sections:** none
- **Markdown entity:** special, header
- **Inherits from**: [Named section](#def-named-section)

- **父级片段:** 无
- **子级（嵌套）片段:** 无
- **Markdown 实体:** 特殊, 标题头
- **继承自**: [命名片段](#def-named-section)

#### Definition
#### 定义
Defined by the **first** Markdown header in the blueprint document, unless it
represents another section definition.

由 blueprint 文档中 **第一** Markdown 标题头定义，除非其使用了其他片段的定义方法。

#### Description
#### 描述
Name and description of the API

API 的名称和描述

#### Example
#### 例子

    # Basic ACME Blog API
    Welcome to the **ACME Blog** API. This API provides access to the **ACME
    Blog** service.

---

<a name="def-resourcegroup-section"></a>
## Resource group section
## 资源组片段
- **Parent sections:** none
- **Nested sections:** [`0+` Resource section](#def-resource-section)
- **Markdown entity:** header
- **Inherits from**: [Named section](#def-named-section)

- **父级片段:** 无
- **子级（嵌套）片段:** [`0+` 资源片段](#def-resource-section)
- **Markdown 实体:** 标题头
- **继承自**: [命名片段](#def-named-section)

#### Definition
#### 定义
Defined by the `Group` keyword followed by group [name (identifier)](#def-identifier):

通过`Group`关键字后面跟[名称 (标识符)](#def-identifier)定义：

    # Group <identifier>

#### Description
#### 描述
This section represents a group of resources (Resource Sections). **May**
include one or more nested [Resource Sections](#def-resource-section).

本片段是代表一组资源（资源片段）。**可以** 包含一个或多​​个嵌套[资源片段](#def-resource-section)。

#### Example
#### 例子

```apib
# Group Blog Posts

## Resource 1 [/resource1]

 ...

# Group Authors
Resources in this groups are related to **ACME Blog** authors.

## Resource 2 [/resource2]

 ...
```

---

<a name="def-resource-section"></a>
## Resource section
## 资源片段
- **Parent sections:** none, [Resource group section](#def-resourcegroup-section)
- **Nested sections:** [`0-1` Parameters section](#def-uriparameters-section), [`0-1` Attributes section](#def-attributes-section), [`0-1` Model section](#def-model-section), [`1+` Action section](#def-action-section)
- **Markdown entity:** header
- **Inherits from**: [Named section](#def-named-section)

- **父级片段:** 无, [资源组片段](#def-resourcegroup-section)
- **子级（嵌套）片段:** [`0-1` 参数片段](#def-uriparameters-section), [`0-1` 属性片段](#def-attributes-section), [`0-1` 模型片段](#def-model-section), [`1+` 操作片段](#def-action-section)
- **Markdown 实体:** 标题头
- **继承自**: [命名片段](#def-named-section)

#### Definition
#### 定义
Defined by an [URI template][uritemplate]:

由[URI 模板][uritemplate]定义：

    # <URI template>

**-- or --**

**-- 或者 --**

Defined by a resource [name (identifier)](#def-identifier) followed by an
[URI template][uritemplate] enclosed in square brackets `[]`.

由资源[名称 (标识符)](#def-identifier)后面跟中括号`[]`修饰[URI 模板][uritemplate]定义：

    # <identifier> [<URI template>]

**-- or --**

**-- 或者 --**

Defined by an [HTTP request method][httpmethods] followed by [URI template][uritemplate]:

由[HTTP 请求方法][httpmethods]后面跟[URI 模板][uritemplate]定义：

    # <HTTP request method> <URI template>

**-- or --**

**-- 或者 --**

Defined by a resource [name (identifier)](#def-identifier) followed by an
[HTTP request method][httpmethods] and an [URI template][uritemplate] enclosed
in square brackets `[]`:

由资源[名称 (标识符)](#def-identifier)后面跟大括号`[]`修饰的[HTTP 请求方法][httpmethods]和[URI 模板][uritemplate]定义：

    # <identifier> [<HTTP request method> <URI template>]

> **NOTE:** In the latter two cases the rest of this section represents the
> [Action section](#def-action-section) including its description and nested
> sections and **follows the rules of the Action section instead**.

> **注意：** 在后两种情况下，片段的其余部分代表[操作片段](#def-action-section)，
> 包括它的描述和嵌套的片段，并 **遵循操作片段代替规则**。

#### Description
#### 描述
An API [resource](http://www.w3.org/TR/di-gloss/#def-resource) as specified by
its *URI* or a set of resources (a resource template) matching its *URI
template*.

API [资源](http://www.w3.org/TR/di-gloss/#def-resource)通过匹配一个资源的 *URI*
或匹配一组资源（资源模板）的 *URI 模板* 指定。

This section **should** include at least one nested
[Action section](#def-action-section) and **may** include following nested
sections:

本片段 **应该** 至少包含一个嵌套的[操作片段](#def-action-section)，**可能** 包括以下嵌套部分：

- [`0-1` URI parameters section](#def-uriparameters-section)
- [`0-1` URI 参数片段](#def-uriparameters-section)

    URI parameters defined in the scope of a Resource section apply to
    _any and all_ nested Action sections except when an [URI template][uritemplate] has
    been defined for the Action.

    在资源片段范围中定义 URI 参数适用于 _任何_ 嵌套的操作片段，除非使用[URI 模板][uritemplate]描述操作。

- [`0-1` Attributes section][]
- [`0-1` 属性片段][]

    Attributes defined in the scope of a Resource section represent Resource
    attributes. If the resource is defined with a name these attributes **may**
    be referenced in [Attributes sections][].

    在资源片段的范围中定义属性即代表资源属性。
    如果资源使用一个名称定义，其属性 **可以** 引用属性片段。

- [`0-1` Model section](#def-model-section)
- [`0-1` 模型片段](#def-model-section)

- Additional [Action sections](#def-action-section)
- 附加 [操作片段](#def-action-section)

> **NOTE:** A blueprint document may contain multiple sections for the same
> resource (or resource set), as long as their HTTP methods differ. However it
> is considered good practice to group multiple HTTP methods under one resource
> (resource set).

> **注意：** blueprint 文档可以包含同一资源（或资源集）的多个片段，只要他们的 HTTP 方法不同。
> 然而最好的做法是，将多个 HTTP 方法放到一个资源（资源集）分组中。

#### Example
#### 例子

```apib
# Blog Posts [/posts/{id}]
Resource representing **ACME Blog** posts.
```

```apib
# /posts/{id}
```

```apib
# GET /posts/{id}
```

---

<a name="def-model-section"></a>
## Resource model section
## 资源模型片段
- **Parent sections:** [Resource section](#def-resource-section)
- **Nested sections:** [Refer to payload section](#def-payload-section)
- **Markdown entity:** list
- **Inherits from**: [Payload section](#def-payload-section)

- **父级片段:** [资源片段](#def-resource-section)
- **子级（嵌套）片段:** [引用的 payload 片段](#def-payload-section)
- **Markdown 实体:** 列表
- **继承自**: [Payload 片段](#def-payload-section)


#### Definition
#### 定义
Defined by the `Model` keyword followed by an optional media type:

通过`Model`关键字后跟一个可选的媒体类型定义：

    + Model (<media type>)

#### Description
#### 描述
A [resource manifestation](http://www.w3.org/TR/di-gloss/#def-resource-manifestation) - one
exemplary representation of the resource in the form of a
[payload](#def-payload-section).

一个[资源表现](http://www.w3.org/TR/di-gloss/#def-resource-manifestation) -
一个[payload](#def-payload-section)形式的资源示范性表示。

#### Referencing
#### 引用
The payload defined in this section **may** be referenced in any response or
request section in the document using parent section's identifier. You can
refer to this payload in any of the following [Request](#def-request-section)
or [Response](#def-response-section) payload sections using the Markdown
implicit [reference syntax][].

在本片段中定义的 payload **可以** 被文档中的任何请求或响应使用片段标识符引用。
你可以在任何 payload [请求](#def-request-section)或[响应](#def-response-section)中
使用 Markdown [引用语法][reference syntax]引用这个 payload 片段。

#### Example
#### 例子

```apib
# My Resource [/resource]

+ Model (text/plain)

        Hello World

## Retrieve My Resource [GET]

+ Response 200

    [My Resource][]
```

---

<a name="def-schema-section"></a>
## Schema section
## 模式片段
- **Parent sections:** [Payload section](#def-payload-section)
- **Nested sections:** none
- **Markdown entity:** list
- **Inherits from**: [Asset section](#def-asset-section)

- **父级片段:** [Payload 片段](#def-payload-section)
- **子级（嵌套）片段:** 无
- **Markdown 实体:** 列表
- **继承自**: [资产片段](#def-asset-section)

#### Definition
#### 定义
Defined by the `Schema` keyword in Markdown list entity.

通过`Schema`关键字在 Markdown 列表实体中定义。

    + Schema

#### Description
#### 描述
Specifies a validation schema for the HTTP message-body of parent payload section.

指定父级 payload 片段的 HTTP 消息体验证模式。

---

<a name="def-action-section"></a>
## Action section
## 操作片段
- **Parent sections:** [Resource section](#def-resource-section)
- **Nested sections:**
    [`0-1` Relation section](#def-relation-section),
    [`0-1` URI parameters section](#def-uriparameters-section),
    [`0-1` Attributes section](#def-attributes-section),
    [`0+` Request section](#def-request-section),
    [`1+` Response section](#def-response-section)
- **Markdown entity:** header
- **Inherits from**: [Named section](#def-named-section)

- **父级片段:** [资源片段](#def-resource-section)
- **子级（嵌套）片段:**
    [`0-1` 关系片段](#def-relation-section),
    [`0-1` URI 参数片段](#def-uriparameters-section),
    [`0-1` 属性片段](#def-attributes-section),
    [`0+` 请求片段](#def-request-section),
    [`1+` 响应片段](#def-response-section)
- **Markdown 实体:** 标题头
- **继承自**: [命名片段](#def-named-section)

#### Definition
#### 定义
Defined by an [HTTP request method][httpmethods]:

通过[HTTP 请求方法][httpmethods]定义：

    ## <HTTP request method>

**-- or --**

**-- 或者 --**

Defined by an action [name (identifier)](#def-identifier) followed by an
[HTTP request method][httpmethods] enclosed in square brackets `[]`.

通过操作[命名 (标识符)](#def-identifier)后面跟中括号`[]`描述的[HTTP 请求方法][httpmethods]。

    ## <identifier> [<HTTP request method>]

**-- or --**

**-- 或者 --**

Defined by an action [name (identifier)](#def-identifier) followed by an
[HTTP request method][httpmethods] and
[URI template][uritemplate] enclosed in square brackets `[]`.

通过操作[命名 (标识符)](#def-identifier)后面跟中括号`[]`描述的[HTTP 请求方法][httpmethods]和[URI 模板][uritemplate]。

    ## <identifier> [<HTTP request method> <URI template>]

#### Description
#### 描述
Definition of at least one complete HTTP transaction as performed with the
parent resource section. An action section **may** consist of multiple HTTP
transaction examples for the given HTTP request method.

至少有个一个完整的 HTTP 事务作为父级资源片段的定义。
一个操作片段 **可以** 由多个 HTTP 事务示例组成一个给定的 HTTP 请求方法。

This section **may** include one nested
[URI parameters section](#def-uriparameters-section) describing any URI
parameters _specific_ to the action – URI parameters discussed in the scope of
an Action section apply to the respective Action section ONLY.

此片段 **可以** 包含一个嵌套[URI 参数片段](#def-uriparameters-section)描述操作的任意 _具体_ 的 URI 参数 -
在操作片段范围内讨论的 URI 参数只适用于此操作片段。

This section **may** include one nested [Attributes section][] defining the
input (request) attributes of the section. If present, these attributes
**should** be inherited in every Action's [Request section][] unless specified
otherwise.

这个片段 **可以** 包括一个嵌套的[属性片段][Attributes section]定义这个片段的输入（必选）属性。
如果存在，这些属性 **应该** 被操作的每一个[请求片段][Request section]继承，除非另有规定。

Action section **should** include at least one nested
[Response section](#def-response-section) and **may** include additional nested
[Request](#def-request-section) and [Response](#def-response-section) sections.

操作片段 **应该** 包括至少一个嵌套的[响应片段](#def-response-section)，
**可能** 包括额外的嵌套[请求片段](#def-request-section)和[响应片段](#def-response-section)。

Nested Request and Response sections **may** be ordered into groups where each
group represents one transaction example. The first transaction example group
starts with the first nested Request or Response section. Subsequent groups
start with the first nested Request section following a Response section.

嵌套的请求片段和响应片段，**可以** 在分组中有序，每个分组代表一个事务例子。
第一个事务例子分组通过第一个请求片段或响应片段开始。
随后的分组通过第一个事务的响应片段后面的请求分组开始。

Multiple Request and Response nested sections within one transaction example
**should** have different identifiers.

一个嵌套了多个请求和响应的事务例子 **应该** 使用不同的标识符。

#### Example
#### 例子

```apib
# Blog Posts [/posts{?limit}]
 ...

## Retrieve Blog Posts [GET]
Retrieves the list of **ACME Blog** posts.

+ Parameters
    + limit (optional, number) ... Maximum number of posts to retrieve

+ Response 200

        ...

## Create a Post [POST]

+ Attributes

        ...

+ Request

        ...

+ Response 201

        ...

## Delete a Post [DELETE /posts/{id}]

+ Parameters
    + id (string) ... Id of the post

+ Response 204
```

#### Example Multiple Transaction Examples
#### 多事务例子

```apib
# Resource [/resource]
## Create Resource [POST]

+ request A

        ...

+ response 200

        ...

+ request B

        ...

+ response 200

        ...

+ response 500

        ...

+ request C

        ...

+ request D

        ...

+ response 200

        ...
```

> **NOTE:** The "Multiple Transaction Examples" example demonstrates three
> transaction examples for one given action:
>
> 1. 1st example: request `A`, response `200`
> 2. 2nd example: request `B`, responses `200` and `500`
> 3. 3rd example: requests `C` and `D`, response `200`

> **注意：** “多事务例子”演示了一个包含3个事务的操作：
>
> 1. 第一个例子：请求 `A`, 响应 `200`
> 2. 第二个例子：请求 `B`, 响应 `200` 和 `500`
> 3. 第三个例子：请求 `C` 和 `D`, 响应 `200`

---

<a name="def-request-section"></a>
## Request section
## 请求片段
- **Parent sections:** [Action section](#def-action-section)
- **Nested sections:** [Refer to payload section](#def-payload-section)
- **Markdown entity:** list
- **Inherits from**: [Payload section](#def-payload-section)

- **父级片段:** [操作片段](#def-action-section)
- **子级（嵌套）片段:** [引用的 payload 片段](#def-payload-section)
- **Markdown 实体:** 列表
- **继承自**: [Payload 片段](#def-payload-section)

#### Definition
#### 定义
Defined by the `Request` keyword followed by an optional [identifier](#def-identifier):

通过`Request`关键字后跟一个可选的[标识符](#def-identifier)定义：

    + Request <identifier> (<Media Type>)

#### Description
#### 描述
One HTTP request-message example – payload.

一个 HTTP 请求消息例子。

#### Example
#### 例子

```apib
+ Request Create Blog Post (application/json)

        { "message" : "Hello World." }
```

---

<a name="def-response-section"></a>
## Response section
## 响应片段
- **Parent sections:** [Action section](#def-action-section)
- **Nested sections:** [Refer to payload section](#def-payload-section)
- **Markdown entity:** list
- **Inherits from**: [Payload section](#def-payload-section)

- **父级片段:** [操作片段](#def-action-section)
- **子级（嵌套）片段:** [引用的 payload 片段](#def-payload-section)
- **Markdown 实体:** 列表
- **继承组**: [Payload 片段](#def-payload-section)

#### Definition
#### 定义
Defined by the `Response` keyword. The response section definition **should**
include an [HTTP status code][] as its identifier.

通过`Response`关键字定义。响应片段定义 **应该** 包含一个作为标识符的[HTTP 状态码][HTTP status code]。

    + Response <HTTP status code> (<Media Type>)

#### Description
#### 描述
One HTTP response-message example – payload.

一个 HTTP 响应消息例子。

#### Example
#### 例子

```apib
+ Response 201 (application/json)

            { "message" : "created" }
```

---

<a name="def-uriparameters-section"></a>
## URI parameters section
## URI 参数片段
- **Parent Sections:** [Resource section](#def-resource-section) | [Action section](#def-action-section)
- **Nested Sections:** none
- **Markdown entity:** list
- **Inherits from**: none, special

- **父级片段:** [资源片段](#def-resource-section) | [操作片段](#def-action-section)
- **子级（嵌套）片段:** 无
- **Markdown 实体:** 列表
- **继承自**: 无, 特殊

#### Definition
#### 定义
Defined by the `Parameters` keyword written in a Markdown list item:

通过`Parameters`关键字写到 Markdown 列表项中定义：

    + Parameters

#### Description
#### 描述
Discussion of URI parameters _in the scope of the parent section_.

在 _父级片段的范围_ 讨论 URI 参数。

This section **must** be composed of nested list items only. This section
**must not** contain any other elements. Each list item describes a single URI
parameter. The nested list items subsections inherit from the
[Named section](#def-named-section) and are subject to additional formatting as
follows:

这个片段 **必须** 在嵌套列表项中唯一。此片段 **不应该** 包含任何其他元素。
每个列表项描述一个 URI 参数。这个片段嵌套列表项从[命名片段](#def-named-section)继承，其接受的格式如下：

    + <parameter name>: `<example value>` (<type> | enum[<type>], required | optional) - <description>

        <additional description>

        + Default: `<default value>`

        + Members
            + `<enumeration value 1>`
            + `<enumeration value 2>`
            ...
            + `<enumeration value N>`

Where:

位置：

+ `<parameter name>` is the parameter name as written in
  [Resource Section](#ResourceSection)'s URI (e.g. "id").
+ `<parameter name>`
  [资源片段](#ResourceSection) URI 中参数的名称（例如“id”）。
+ `<description>` is any **optional** Markdown-formatted description of the
  parameter.
+ `<description>` 任何 **可选项** Markdown 格式参数描述。
+ `<additional description>` is any additional **optional** Markdown-formatted
  [description](#SectionDescription) of the parameter.
+ `<additional description>` 任何额外 **可选项** Markdown 格式的参数。
  [描述](#SectionDescription)。
+ `<default value>` is an **optional** default value of the parameter – a value
  that is used when no value is explicitly set (optional parameters only).
+ `<default value>` **可选** 参数默认值 – 当没有设置明确值（仅限可选参数）。
  that is used when no value is explicitly set (optional parameters only).
+ `<example value>` is an **optional** example value of the parameter (e.g. `1234`).
+ `<example value>` **可选** 参数例子值（例如`1234`）。
+ `<type>` is the **optional** parameter type as expected by the API (e.g.
  "number", "string", "boolean"). "string" is the **default**.
+ `<type>` **可选** API预期参数类型（如“number”，“string”，“boolean”）。“string”是 **默认的**。
+ `Members` is the **optional** enumeration of possible values.
  `<type>` should be surrounded by `enum[]` if this is present.
  For example, if enumeration values are present for a parameter whose type is
  `number`, then `enum[number]` should be used instead of `number` to.
+ `Members` **可选** 有限的枚举值。如果`<type>`存在，应该由`enum[]`修饰。
  例如，如果枚举值呈现为`number`, 则应该由`enum[number]`替代`number`。
+ `<enumeration value n>` represents an element of enumeration type.
+ `<enumeration value n>` 代表枚举类型的元素。
+ `required` is the **optional** specifier of a required parameter
  (this is the **default**)
+ `required` **可选** 必需参数的说明（这是 **默认** 的）。
+ `optional` is the **optional** specifier of an optional parameter.
+ `optional` **可选** 可选参数的说明。

> **NOTE:** This section **should only** contain parameters that are specified
> in the parent's resource URI template, and does not have to list every URI
> parameter.

> **注意：** 本片段 **应该只能** 包含在父级资源 URI 模板指定的参数，并且没有必要列出所有 URI 参数。

#### Example
#### 例子

```apib
# GET /posts/{id}
```

```apib
+ Parameters
    + id - Id of a post.
```

```apib
+ Parameters
    + id (number) - Id of a post.
```

```apib
+ Parameters
    + id: `1001` (number, required) - Id of a post.
```

```apib
+ Parameters
    + id: `1001` (number, optional) - Id of a post.
        + Default: `20`
```

```apib
+ Parameters
    + id (enum[string])

        Id of a Post

        + Members
            + `A`
            + `B`
            + `C`
```
---

<a name="def-attributes-section"></a>
## Attributes Section
## 属性片段
- **Parent sections:** [Resource section](#def-resource-section) | [Action section](#def-action-section) | [Payload section](#def-payload-section)
- **Nested sections:** See **[Markdown Syntax for Object Notation][MSON]**
- **Markdown entity:** list
- **Inherits from**: none

- **父级片段:** [资源片段](#def-resource-section) | [操作片段](#def-action-section) | [Payload 片段](#def-payload-section)
- **子级（嵌套）片段:** 参阅 **[Markdown 对象表示法][MSON]**
- **Markdown 实体:** 列表
- **继承自**: 无

#### Definition
#### 定义
Defined by the `Attributes` keyword followed by an optional
[MSON Type Definition][] enclosed in parentheses.

通过`Attributes`关键字后面跟可选的用尖括号修饰的[MSON 类型定义][MSON Type Definition]定义。

    + Attributes <Type Definition>

`<Type Definition>` is the type definition of the data structure being
described. If the `<Type Definition>` is not specified, an `object` base type
is assumed. See [MSON Type Definition][] for details.

`<Type Definition>` 是描述数据结构的类型定义。如果`<Type Definition>`没有被指定，则其类型是`object`。
参见[MSON 类型定义][MSON Type Definition]了解更多。

##### Example
##### 例子

```apib
+ Attributes (object)
```

#### Description
#### 描述
This section describes a data structure using the
**[Markdown Syntax for Object Notation][MSON] (MSON)**.
Based on the parent section, the data structure being described is one of the
following:

本片段将介绍如何使用 **[Markdown 对象表示法][MSON] (MSON)** 表示数据结构。
基于父级片段，所描述的数据结构是下列之一：

1. Resource data structure attributes ([Resource section](#def-resource-section))
1. 资源数据结构属性 ([资源片段](#def-resource-section))
2. Action request attributes ([Action section](#def-action-section))
2. 操作片段属性 ([操作片段](#def-action-section))
3. Payload message-body attributes ([Payload section](#def-payload-section))
3. Payload 消息体属性 ([Payload 片段](#def-payload-section))

Data structures defined in this section **may** refer to any arbitrary data
structures defined in the [Data Structures section](#def-data-structures) as
well as to any data structures defined by a named resource attributes
description (see below).

在本片段中定义的数据结构 **可以** 引用任意在[数据结构片段](#def-data-structures)定义的数据结构，
以及通过一个命名资源属性描述（见下文）定义的任意数据结构。

#### Resource Attributes description
#### 资源属性描述
Description of the resource data structure.

描述资源的数据结构

If defined in a named [Resource section](#def-resource-section), this data
structure **may** be referenced by other data structures using the resource
name.

如果在命名[资源片段](#def-resource-section)中定义，这个数据结构 **可以** 被其他数据结构通过资源名称引用。

##### Example
##### 例子

```apib
# Blog Post [/posts/{id}]
Resource representing **ACME Blog** posts.

+ Attributes
    + id (number)
    + message (string) - The blog post article
    + author: john@appleseed.com (string) - Author of the blog post
```

> **NOTE:** This data structure can be later referred as:
>
>     + Attributes (Blog Post)
>

> **注意：** 该数据结构可以被简称为：
>
>     + Attributes (Blog Post)
>

#### Action Attributes description
#### 操作属性描述
Description of the default request message-body data structure.

默认请求消息体数据结构描述。

If defined, all the [Request sections](#def-request-section) of the respective
[Action section](#def-action-section) inherits these attributes unless
specified otherwise.

如果定义，除非另有规定，相应[操作片段](#def-action-section)的所有[请求片段](#def-request-section)继承这些属性。

##### Example
##### 例子

```apib
## Create a Post [POST]

+ Attributes
    + message (string) - The blog post article
    + author: john@appleseed.com (string) - Author of the blog post

+ Request (application/json)

+ Request (application/yaml)

+ Response 201
```

#### Payload Attributes description
#### Payload 属性描述
Description of payload (request, response, model) message-body attributes.

payload（请求，响应，模型）消息体属性的描述。

Not every attribute has to be described. However, when an attribute is
described, it **should** appear in the respective
[Body section](#def-body-section) example, if a Body section is provided.

不是每个属性都有描述。
然而，当一个属性有描述时，它 **应该** 出现在各个[消息体片段](#def-body-section)例子中，如果消息体片段有提供。

If defined, the [Body section](#def-body-section) **may** be omitted and the
example representation **should** be generated from the attributes description.

如果定义，[消息体片段](#def-body-section) **可以** 省略，即表示其属性 **应该** 从属性描述来生成。

The description of message-body attributes **may** be used to describe
message-body validation if no [Schema section](#def-schema-section) is
provided. When a Schema section is provided, the attributes description
**should** conform to the schema.

消息体属性的描述 **可以** 用于描述消息主体的验证，如果没有提供[模式片段](#def-schema-section)。
当提供了模式片段，属性的描述 **应该** 符合模式。

##### Example
##### 例子

```apib
## Retrieve a Post [GET]

+ Response 200 (application/json)

    + Attributes (object)
        + message (string) - Message to the world

    + Body

            { "message" : "Hello World." }
```

---

<a name="def-headers-section"></a>
## Headers section
## 消息头片段
- **Parent sections:** [Payload section](#def-payload-section)
- **Nested sections:** none
- **Markdown entity:** list
- **Inherits from**: none

- **父级片段:** [Payload 片段](#def-payload-section)
- **子级（嵌套）片段:** 无
- **Markdown 实体:** 列表
- **继承自**: 无

#### Definition
#### 定义
Defined by the `Headers` keyword in Markdown list entity.

通过`Headers`关键字在 Markdown 列表实体中定义。

    + Headers

#### Description
#### 描述
Specifies the HTTP message-headers of the parent payload section. The content
this section is expected to be a [pre-formatted code block](http://daringfireball.net/projects/markdown/syntax#precode)
with the following syntax:

指定父级 payload 片段的 HTTP 消息头。
这个片段的内容预计将使用如下[预格式化代码块](http://daringfireball.net/projects/markdown/syntax#precode)语法：

    <HTTP header name>: <value>

One HTTP header per line.

一个 HTTP 头一行。

#### Example
#### 例子

```apib
+ Headers

        Accept-Charset: utf-8
        Connection: keep-alive
        Content-Type: multipart/form-data, boundary=AaB03x
```

---

<a name="def-body-section"></a>
## Body section
## 消息体片段
- **Parent sections:** [Payload section](#def-payload-section)
- **Nested sections:** none
- **Markdown entity:** list
- **Inherits from**: [Asset section](#def-asset-section)

- **父级片段:** [Payload 片段](#def-payload-section)
- **子级（嵌套）片段:** 无
- **Markdown 实体:** 列表
- **继承自**: [资产片段](#def-asset-section)

#### Definition
#### 定义
Defined by the `Body` keyword in Markdown list entity.

通过`Body`关键字在 Markdown 列表实体中定义。

    + Body

#### Description
#### 描述
Specifies the HTTP message-body of a payload section.

指定 payload 片段的 HTTP 消息体。

#### Example
#### 例子

```apib
+ Body

        {
            "message": "Hello"
        }
```

---


<a name="def-data-structures"></a>
## Data Structures section
## 数据结构片段
- **Parent sections:** none
- **Nested sections:** _MSON Named Type definition_ (see below)
- **Markdown entity:** header
- **Inherits from**: none

- **父级片段:** 无
- **子级（嵌套）片段:** _MSON 命名类型定义_ （见下面）
- **Markdown 实体:** 标题头
- **继承自**: 无

#### Definition
#### 定义
Defined by the `Data Structures` keyword.

通过`Data Structures`关键字定义。

    # Data Structures

#### Description
#### 描述
This section holds arbitrary data structures definitions defined in the form of
[MSON Named Types][].

本片段以持有[MSON 命名类型][MSON Named Types]的形式定义的任意数据结构。

Data structures defined in this section **may** be used in any [Attributes section][].
Similarly, any data structures defined in a [Attributes section][] of a named
[Resource Section][] **may** be used in a data structure definition.

在本片段中定义的数据结构 **可以** 用于任何[属性片段][Attributes section]。
类似地，任何在[属性片段][]中定义命名[资源片段][] **可以** 被用于数据结构定义中。

Refer to the [MSON][] specification for full details on how to define an MSON Named type.

请参阅 [MSON][] 规范了解如何定义一个 MSON 命名类型的全部细节。

#### Example
#### 例子

```apib
# Data Structures

## Message (object)

+ text (string) - text of the message
+ author (Author) - author of the message

## Author (object)

+ name: John
+ email: john@appleseed.com
```

#### Example reusing Data Structure in Resource
#### 在资源中复用数据结构的例子

```apib
# User [/user]

+ Attributes (Author)

# Data Structures

## Author (object)

+ name: John
+ email: john@appleseed.com
```

#### Example reusing Resource-defined Data Structure
#### 复用资源中定义的数据结构的例子

```apib
# User [/user]

+ Attributes
    + name: John
    + email: john@appleseed.com

# Data Structures

## Author (User)
```

---

<a name="def-relation-section"></a>
## Relation section
## 关系片段
- **Parent sections:** [Action section](#def-action-section)
- **Nested Sections:** none
- **Markdown entity:** list
- **Inherits from**: none

- **父级片段:** [操作片段](#def-action-section)
- **子级（嵌套）片段:** 无
- **Markdown 实体:** 列表
- **继承自**: 无

#### Definition
#### 定义
Defined by the `Relation` keyword written in a Markdown list item followed by a
colon (`:`) and a link relation identifier.

通过`Relation`关键字在 Markdown 列表项后跟冒号（`:`）连接链接关系标识符。

    + Relation: <link relation identifier>

#### Description
#### 描述
This section specifies a [link relation type](https://tools.ietf.org/html/rfc5988#section-4)
for the given action as specified by [RFC 5988](https://tools.ietf.org/html/rfc5988).

本片段指定一个[连接关系类型](https://tools.ietf.org/html/rfc5988#section-4)
其给定操作由[RFC 5988](https://tools.ietf.org/html/rfc5988)规定。

> **NOTE:** The link relation identifiers should be unique per resource in the blueprint document.

> **注意：** 链接关系标识符应该在 blueprint 文档中唯一标识资源。

#### Example
#### 例子

```apib
# Task [/tasks/{id}]

+ Parameters
    + id

## Retrieve Task [GET]

+ Relation: task
+ Response 200

        { ... }

## Delete Task [DELETE]

+ Relation: delete
+ Response 204
```

---


<br>

<a name="def-appendix"></a>
# III. Appendix
# III. 附录

<a name="def-uri-templates"></a>
## URI Templates
## URI 模板

The API Blueprint uses a subset of [RFC6570][rfc6570] to define a resource URI Template.

API Blueprint使用[RFC6570][rfc6570]子集定义资源的 URI 模板。

### URI Path Segment
### URI 路径分隔

At its simplest form – without any variables – a path segment of an
URI Template is identical to an URI path segment:

在最简单的形式 - 没有任何变量 - 一个被路径分隔符描述的 URI 模板等同于一个 URI 路径分隔：

```
/path/to/resources/42
```

### URI Template Variable
### URI 模板变量

Variable names are case-sensitive. The variable name may consists of following
characters **only**:

变量名称是区分大小写的。变量名可能 **仅仅** 包含以下字符：

- ASCII alpha numeric characters (`a-z`, `A-Z`)
- ASCII 字母数字字符（`a-z`， `A-Z`）
- Decimal digits (`0-9`)
- 小数数字 (`0-9`)
- `_`
- `_`下划线
- [Percent-encoded][pct-encoded] characters
- [百分比编码][pct-encoded]字符
- `.`
- `.`点

Multiple variables are separated by the comma **without** any leading or
trailing spaces. A variable(s) **must** be enclosed in braces – `{}`
**without** any additional leading or trailing whitespace.

多变量由逗号分隔并且 **没有** 任何前缀或尾随空格。
一个变量 **必须** 由大括号 – `{}`修饰并 **没有** 任何附加前缀或尾随空格。

#### Operators
#### 算子

The first variable in the braces **might** be preceded by an operator.
API Blueprint currently supports the following operators:

在括号中的第一变量 **可能** 由算子开头。 API Blueprint 目前支持以下几个算子：

- `#` – _fragment identifier_ operator
- `+` – _reserved value_ operator
- `?` – _form-style query_ operator
- `&` – _form-style query continuation_ operator

- `#` – _片段标识符_ 算子
- `+` – _保留值_ 算子
- `?` – _表单-样式查询_ 算子
- `&` – _表单-样式查询连接_ 算子

#### Examples

```
{var}
{var1,var2,var3}
{#var}
{+var}
{?var}
{?var1,var2}
{?%24var}
{&var}
```

> **NOTE:** The [explode variable modifier][uri-explode] is also supported.
> Refer to RFC6570 for its description.

> **注意：** [爆炸变量][uri-explode]也是支持的。参阅 RFC6570 的描述。

#### Variable Reserved Values
#### 变量保留值

Following characters are **reserved** in variable _values_:

以下字符在变量 _值_ 中被 **保留**：

`:` / `/` / `?` / `#` / `[` / `]` / `@` / `!` / `$` / `&` / `'` / `(` / `)` / `*` / `+` / `,` / `;` / `=`

### Path Segment Variable
### 路径分隔变量

Simple path segment component variable is defined without any operator:

简单的路径分隔符变量定义不包含任何算子：

```
/path/to/resources/{var}
```

With `var := 42` the expansion is `/path/to/resources/42`.

当 `var := 42` 则 `/path/to/resources/42`.

> **NOTE:** RFC6570 – Level 1

> **注意：** RFC6570 – Level 1

### Fragment Identifier Variable
### 片段标识符变量

URI Template variables for fragment identifiers are defined using the
crosshatch (`#`) operator:

对于包含片段标识符的 URI 模板变量使用井号（`#`）运算符定义：

```
/path/to/resources/42{#var}
```

With `var := my_id` the expansion is `/path/to/resources/42#my_id`.

当 `var := my_id` 则 `/path/to/resources/42#my_id`.

> **NOTE:** RFC6570 – Level 2

> **注意：** RFC6570 – Level 2

### Variable with Reserved Characters Values
### 变量中使用保留字符的值

To define URI Template variables with reserved URI characters,
use the plus (`+`) operator:

为了在URI 模板变量中包含保留字符，使用加号（`+`）运算符：

```
/path/{+var}/42
```

With `var := to/resources` the expansion is `/path/to/resources/42`.

当 `var := to/resources` 则 `/path/to/resources/42`.

> **NOTE:** RFC6570 – Level 2

> **注意：** RFC6570 – Level 2

### Form-style Query Variable
### 表单-风格查询变量

To define variables for a form-style query use the question mark (`?`) operator

为了定义一个表单-风格查询变量，使用问号（`?`）运算符：

```
/path/to/resources/{varone}{?vartwo}
```

With `varone := 42` and `vartwo = hello` the expansion is `/path/to/resources/42?vartwo=hello`.

当 `varone := 42` 和 `vartwo = hello` 则 `/path/to/resources/42?vartwo=hello`.

To continue a form-style query use the ampersand (`&`) operator:

继续使用表单-风格查询使用连接符（`&`）运算符：

```
/path/to/resources/{varone}?path=test{&vartwo,varthree}
```

With `varone := 42`, `vartwo = hello`, `varthree = 1024` the expansion is `/path/to/resources/42?path=test&vartwo=hello&varthree=1024`.

当 `varone := 42`, `vartwo = hello`, `varthree = 1024` 则 `/path/to/resources/42?path=test&vartwo=hello&varthree=1024`.

> **NOTE:** RFC6570 – Part of Level 3

> **注意：** RFC6570 – Part of Level 3

---

[apiblueprint.org]: http://apiblueprint.org
[markdown syntax]: http://daringfireball.net/projects/markdown
[reference syntax]: http://daringfireball.net/projects/markdown/syntax#link
[gitHub flavored markdown syntax]: https://help.github.com/articles/github-flavored-markdown
[httpmethods]: https://github.com/for-GET/know-your-http-well/blob/master/methods.md#know-your-http-methods-well
[uritemplate]: #def-uri-templates
[rfc6570]: http://tools.ietf.org/html/rfc6570
[HTTP status code]: https://github.com/for-GET/know-your-http-well/blob/master/status-codes.md
[header syntax]: https://daringfireball.net/projects/markdown/syntax#header
[list syntax]: https://daringfireball.net/projects/markdown/syntax#list
[pct-encoded]: http://en.wikipedia.org/wiki/Percent-encoding
[uri-explode]: http://tools.ietf.org/html/rfc6570#section-2.4.2
[examples]: https://github.com/apiaryio/api-blueprint/tree/master/examples

[MSON]: https://github.com/apiaryio/mson
[MSON Named Types]: https://github.com/apiaryio/mson/blob/master/MSON%20Specification.md#22-named-types
[MSON Type Definition]: https://github.com/apiaryio/mson/blob/master/MSON%20Specification.md#35-type-definition

[`0-1` Attributes section]: #def-attributes-section
[Attributes section]: #def-attributes-section
[Attributes sections]: #def-attributes-section

[Resource Section]: #def-resource-section

[Request section]: #def-request-section
