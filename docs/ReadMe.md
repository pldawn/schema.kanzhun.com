1、行业标准
（1）w3.org
    万维网联盟（World Wide Web Consortium，W3C），又称W3C理事会，是万维网的主要国际标准组织。为解决网络应用中不同平台、技术和开发者带来的不兼容问题，保障网络信息的顺利和完整流通，万维网联盟制定了一系列标准并督促网络应用开发者和内容提供者遵循这些标准。标准的内容包括使用语言的规范，开发中使用的导则和解释引擎的行为等等。W3C也制定了包括XML和CSS等的众多影响深远的标准规范。
	
	W3C通过词汇表（Vocabulary）的方式提供标准规范，并为每个词汇表定义专门的命名空间。在语义网（Semantic Web）方面，词汇表定义了描述和表征特定领域的概念和关系（也称为“术语”）。词汇表用于对可在特定应用程序中使用的术语进行分类，表征可能的关系，并定义使用这些术语的可能约束。在实践中，词汇表可能非常复杂（有数千个术语）或非常简单（仅描述一个或两个概念）。词汇表是语义网推理技术的基本构建块。
	
	与语义网相关的常用命名空间和对应的词汇表如下：
	owl    http://www.w3.org/2002/07/owl#              该词汇表定义了OWL通用的类和属性，构成了OWL2的RDF/XML语法的基础。
	rdf    http://www.w3.org/1999/02/22-rdf-syntax-ns# 该词汇表定义了RDF命名空间中术语的Schema，描述和表征构成RDF的术语及其属性关系。
	rdfs   http://www.w3.org/2000/01/rdf-schema#       该词汇表更加详细地定义了RDF命名空间中术语的属性关系，增强了RDF词汇表的描述和表征能力。
	xsd    http://www.w3.org/2001/XMLSchema#           该词汇表定义了XML命名空间，是XML的标准规范，通常用于构建RDF/XML语法。
	schema https://schema.org/                         该词汇表定义了层次化的术语，这些术语用于描述和表征现实和抽象世界的各种概念和关系。Schema.org由Google，Microsoft，Yahoo和Yandex支持，是一个开放的社区，并具有良好的拓展性。核心词汇表目前包含598种类型（Types）、862种属性（Properties）和114种枚举值（Enumeration Values）。  

（2）owl和owl2
	Web Ontologoy Language（OWL）是用于定义和实例化Web本体的语言。本体论是一个来自哲学的术语，是指描述世界上各种实体及其相互关系的科学。一个OWL本体可以是各种类、属性及其实例的描述。通过OWL形式语义（formal semantics），一个OWL本体可以描述与之相关的逻辑结果（logical consequences），即某种现实不存在但是由语义引起的事实。
	
	owl  https://www.w3.org/TR/owl-guide/     W3C在2004年发布的OWL规范，定义了OWL的基本类（Class）和属性（Property）、定义了个体（individual）并断言（Assertion）相关的事实。
	owl2 https://www.w3.org/TR/owl2-overview/ W3C在2009年发布的增强版规范，在OWL基础上新增了新的逻辑特性，增强OWL的表现能力。
	
	交换语法（Exchange syntaxes）是指将OWL转换为可供传输、储存的其他格式文件的语法。其他格式包括RDF/XML、Json-ld、Turtle等。关系如下：
	图1.

（3）URI规范
	统一资源标识符（Universal Resource Identifiers
   in WWW, URI）提供了一种用于标识资源的简单且可扩展的方法。URI语法和语义规范源自“World Wide Web global information initiative”，并于1990年在“Universal Resource Identifiers in WWW”[RFC1630]中描述。该语法旨在满足“Functional Recommendations for Internet Resource Locators”[RFC1736]和“Functional Requirements for Uniform Resource Names”[RFC1737]中列出的建议。
   
   最新的URI规范由“Uniform Resource Identifier (URI): Generic Syntax”[RFC3698]描述，https://www.ietf.org/rfc/rfc3986.txt。
   
   URI规范形式如下：
   URI = scheme ":" hier-part [ "?" query ] [ "#" fragment ]
   hier-part = "//" authority path-abempty
                / path-absolute
                / path-rootless
                / path-empty

（4）JSON-LD规范
	关联数据[LINKED-DATA]是一种在不同文档和网站上创建基于标准的机器可解释数据网络的方法。它允许应用程序从一个关联数据开始，跟踪分布在不同文档和网站的其他关联数据链接。
	JSON-LD是一种轻量级语法，用于在JSON中序列化关联数据。它只需进行最少的更改，就可以将现有JSON解释为关联数据。JSON-LD提供一种便捷的方法，可以在基于Web的编程环境中使用关联数据，构建可交互的Web服务以及在基于JSON的存储引擎中存储关联数据。由于JSON-LD与JSON100%兼容，因此可以重用大部分JSON解析器和库。
	
	JSON—LD规定了一些语法标记和关键字，它们是该语法的核心部分，规范细节见https://www.w3.org/TR/2014/REC-json-ld-20140116/。
	
	@context : 用于定义文档中的上下文（context）信息，与XML中的命名空间类似。定义context后，可以通过ns:Vocab的方式代表一个OWL词汇的绝对路径。
	@graph   : 用于标记图，表示被标记的object是一个graph。
	@id      : 用于唯一性地标记包含该key的object，值是URI或其变体。当该object出现在graph中，表示该object是一个node。
	@type    : 用于指定object的类型。与@id一起出现，表示指定node object的类型（X Class or Y Property）；与@value一起出现，表示指定value object的类型（Text, Integer or Float）。
	@value   : 用于表示value object的值。
	@reverse : 用于表示方向相反的Property。

2、新的schema
（1）自定义的Class和Property
	本次新的schema设计，包括新的Class和新的Property设计，综合考虑两方面的内容：
	（A）W3C推荐的schema不够细化，词汇表无法涵盖我司所有的数据，不足以完全支持在我司各种业务场景下的使用；
	（B）W3C推荐的schema经过多机构多年的联合设计，词汇表包含的词汇经过严格的定义和语义边界区分，并且包含复杂完备的层次关系和继承关系，对词汇的定义域和值域也有良好的限定。	因此设计基于我司业务场景的新schema时，将schema.org的schema作为顶层设计，基于我司数据代表的低层次的、具体的语义，寻找包含该语义的高层次的、抽象的词汇，在该词汇下创建新的子类。按照语法，该子类可以继承父类的全部属性，并可以创建独有的新属性，放大或缩小原属性的定义域和值域等。
	
	schema顶层规范: https://schema.org/docs/schemas.html
	
	我司设计的新的Class和Property，具体细节见https://schema.kanzhun.com/schema

（2）新的JSON-LD关键字
	JSON-LD语法指定了语法标记和关键字，均以“@”开头，例如：@id。JSON-LD语法处理数据时，若该key可以和关键字完全匹配，则认为识别到了关键字并进行相应的处理，否则均视为非关键字，即使以“@”开头。	对于非关键字，JSON-LD语法尝试分辨该key是否是linked-data。语法将其识别为link-data的情况包括：（A）该key的形式符合URI规范，可以解析为URI（B）在“@context”中进行了定义，定义指向URI。当该key识别为linked-data时，则按照相应方式进行处理，否则忽略该key。	为了方便我司实际数据处理过程，同时不影响JSON-LD语法解析过程，设计了一些新的关键字。这些关键字以“@”开头，但不同于JSON-LD保留的关键字，同时不在“@context”中对其进行定义，使得JSON-LD语法不会将其识别为linked-data。我司在数据处理过程中可以单独处理该关键字，而不影响开源的JSON-LD解析工具。
	
	我司设计的新的关键字，该设计可以根据需要不断拓展：
	@example     : 表示实际案例，每个案例对应一种实际数据处理过程，可以直接使用。
	@comment     : 表示注释。
	@enumaration : 表示有效值枚举，包含该key的属性指向的值只能是枚举中的值。
	@domain      : 表示属性的定义域。
	@range       : 表示值域的定义域。

（3）contexts说明
	为提高JSON-LD文档解析效率，基于实际数据处理过程，设计了相应的context.jsonld。contexts具有时间戳，方便增加拓展，每次拓展可以是基于新的数据处理流程，也可以是对现有流程的调整。
	
	最新的contexts的时间戳是20190112，包含1种基础声明，4种枚举声明和11种数据处理过程，细节见https://schema.kanzhun.com/contexts/20190112/
