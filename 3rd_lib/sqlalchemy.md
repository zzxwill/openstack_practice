SQLAlchemy官网：[http://www.sqlalchemy.org/](http://www.sqlalchemy.org/)

SQLAlchemy is the Python SQL toolkit and Object Relational Mapper that gives application developers the full power and flexibility of SQL.

It provides a full suite of well known enterprise-level persistence patterns, designed for efficient and high-performing database access, adapted into a simple and Pythonic domain language.

SQLAlchemy的哲学：

相比于对象集合，SQL数据库在大小和性能上更占优势；相比于表和行，对象集合在抽象层次上更占优势。SQLAlchemy目标是采两者只长。

SQLALchemy将数据库当成关系代数引擎，而不仅仅是表的集合。行不仅可以通过表、连接和其他查询描述中查询到，任何这些_单元_都能组成一个更大的结构。SQLALchemy的表达式语言就是基于这个根本概念建立起来的。

SQLALchemy因其对象关系映射（ORM）而知名，这是一个提供数据映射模式的可选组件，在该模式里，类被映射为数据库，在多种方式下允许形成对象模型和数据库模型。

对于这些问题，SQLAlchemy总的解决办法与大多数其他SQL/ORM工具完全不一样，它根本上是一种面向complimentarity的方法。它没有将SQL和对象关系细节隐藏在自动化的强后，所有的处理完全暴露在一系列composable,透明的工具中。SQLAlchemy库扮演自动化重复任务的职责，开发者控制数据库怎么组织以及SQL怎么构建。

SQLAlchemy的主要目标就是改变你思考数据库和SQL的方式。

