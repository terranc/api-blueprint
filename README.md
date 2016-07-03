![logo](assets/logo_apiblueprint.png)

# API Blueprint
### API Design for Humans
### 针对人类而设计的API

[![slack](https://apiblueprint-slack.herokuapp.com/badge.svg)](https://apiblueprint-slack.herokuapp.com/)

A powerful high-level API design language for web APIs.

一个专门为 Web API 设计的强大高级API设计语言。

API Blueprint is simple and accessible to everybody involved in the API design
lifecycle. Its syntax is concise yet expressive.

API Blueprint 非常简单、便利让每个人参与到API设计的生命周期中。其语法简洁而传神。

With API Blueprint you can quickly prototype and model APIs to be created or
describe already deployed mission-critical APIs. From a [car][tesla] to the
largest Content Distribution Network (CDN) in the world.

使用 API Blueprint，你可以创建原型和模型 API 描述已经部署的关键任务 API 。
从[汽车][tesla]到世界上最大的内容分发网络（CDN）。

The API Blueprint is built to encourage dialogue and collaboration between
project stakeholders, developers and customers at any point in the API
lifecycle. At the same time, the API Blueprint [tools][] provide the support to
achieve the goals be it API development, governance or delivery.

API Blueprint 的建立是为了在 API 生命周期中促进开发商、客户、利益相关者之间的对话与合作而产生的。
与此同时，API Blueprint 提供[工具][tools] 支持，以实现 API 开发，管理或交付的目标。

![API Blueprint Lifecycle](assets/lifecycle.png)

[tesla]: https://github.com/timdorr/model-s-api/blob/master/apiary.apib
[tools]: http://apiblueprint.org/tools.html

## Open Source
## 开源
API Blueprint is completely open sourced under the MIT license.
Any [contribution][contribute] is highly appreciated.

API Blueprint是完全开放并采用 MIT 许可。任何[贡献][contribute] 表示高度欢迎的。

[contribute]: #Contribute

## At home on GitHub
## GitHub上面
API Blueprint language is recognized by GitHub. You can
[search for API Blueprint][search] or use the `apib` language identifier for
[syntax highlighting][gfm].

API Blueprint 语言由GitHub的认可。您可以[搜索 API Blueprint][search] 或使用 `apib` 语法识别符让[语法高亮][gfm]。

[search]: https://github.com/search?utf8=%E2%9C%93&q=language%3A%22API+Blueprint%22&type=Repositories&ref=advsearch&l=API+Blueprint&l=

[gfm]: https://help.github.com/articles/github-flavored-markdown/#syntax-highlighting

## Getting started
## 开始
All it takes to describe an endpoint of your API is to write:

只这样需要描述你的 API 端点：

```apib
# GET /message
+ Response 200 (text/plain)

        Hello World!
```

in your favorite plain text editor.

使用你喜欢的文本编辑器即可。

With this blueprint you can already get a [mock][], [documentation][] and
[test][] for your API before you even start coding.

有了这个蓝图，你已经可以为你的 API 的[模拟][mock]，[文档][documentation]和[测试[][test]在你开始编码之前。

To learn more about the API Blueprint syntax jump directly to the
[API Blueprint Tutorial][tutorial] or take a look at some [examples][].

要了解更多有关 API Blueprint 语法，请直接跳转到[API Blueprint 教程][tutorial]或者看看一些[例子][examples]。

[mock]: http://docs.apibstart.apiary.io/#reference/0/message/get?console=1
[documentation]: http://docs.apibstart.apiary.io
[test]: http://dredd.readthedocs.org/en/latest/
[tutorial]: Tutorial.md
[examples]: https://github.com/apiaryio/api-blueprint/tree/master/examples

## Media Type
## 媒体类型
The media type for API Blueprint is `text/vnd.apiblueprint`.

API Blueprint 的媒体类型是`text/vnd.apiblueprint`。（PS：媒体类型通常在Web Http中标识内容的格式或编码）

## Learn more
## 学习更多
- [Tutorial][tutorial]
- [教程][tutorial]
- [Advanced Tutorial][advanced_tutorial]
- [高级教程][advanced_tutorial]
- [Examples][examples]
- [例子][examples]
- [Wiki][wiki]
- [Wiki百科][wiki]
- [Glossary of Terms][glossary]
- [专业术语][glossary]
- [Specification][specification]
- [规范][specification]
- [List of Tools][tools]
- [工具][tools]
- [Developers][developers]
- [开发][developers]

[advanced_tutorial]: Advanced%20Tutorial.md
[glossary]: Glossary%20of%20Terms.md
[specification]: API%20Blueprint%20Specification.md
[wiki]: https://github.com/apiaryio/api-blueprint/wiki
[developers]: https://apiblueprint.org/developers.html

## Future
## 未来
The plans for API Blueprint are completely tracked on GitHub – see the
[API Blueprint Roadmap][roadmap].

对于 API Blueprint 计划完全可以在 GitHub 上跟踪 - 请参阅[API Blueprint 线图][roadmap]。

[roadmap]: https://github.com/apiaryio/api-blueprint/wiki/Roadmap

## Developers
## 开发
Building tools for API Blueprint is possible thanks to its machine-friendly face
provided by API Blueprint parser.

创建 API Blueprint 的工具可能要归功于通过 API Blueprint 解析器提供的机器友好接口。

If you are interested in building tools for API Blueprint check out the
[Developing tools for API Blueprint][developers].

如果你有兴趣构建 API Blueprint 的工具请检出检出[API Blueprint 开发工具][developers]。

## Contribute
## 贡献
Feel free report problems or propose new ideas using the API Blueprint GitHub
[issues][].
随意报告问题或提出使用新思路在 API Blueprint 的 GitHub [问题栏目][issues].。

We use an RFC process for proposing any substantial changes to the API
Blueprint language, specification and/or parsers.

我们使用 RFC 处理过程处理提议到 API
Blueprint 语言、规范、解析器的变更。

If you would like to propose a change, please consult our
[RFC process][rfc].

如果你想提出的改变，请咨询我们的[RFC 处理过程][rfc]。

[issues]: https://github.com/apiaryio/api-blueprint/issues
[rfc]: https://github.com/apiaryio/api-blueprint-rfcs

## Get in Touch
## 联系我们
- [@apiblueprint](https://twitter.com/apiblueprint)
- [Slack](https://apiblueprint-slack.herokuapp.com/)
- [Stack Overflow](http://stackoverflow.com/questions/tagged/apiblueprint)
- [GitHub Issues][issues]

## License
## 许可证
MIT License. See the [LICENSE](https://github.com/apiaryio/api-blueprint/blob/master/LICENSE)
file.

MIT许可证。更多请见[许可证](https://github.com/apiaryio/api-blueprint/blob/master/LICENSE)
file.
