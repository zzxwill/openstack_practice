# Nova
Nova是OpenStack工程的核心组件之一，它提供了对计算资源power massively scalable、按需地、自助式服务访问的功能。
Nova是OpenStack计算服务组件，它允许用户控制IaaS云计算服务平台，用户可以控制实例和网络，并且可以通过users和project来管理云的访问权限。
计算服务并不提供虚拟化软件，它定义驱动，这些驱动与运行在你的宿主机上的底层的虚拟化机制交互，并且通过web-based API暴露功能。

OpenStack Compute包括以下几个组件。

* 控制节点。它代表了全局状态，并且会与其他组件交互。API server作为控制节点的web service front end。计算的控制节点提供计算服务器资源，通常也包含计算服务。
* 对象存储。它是一个提供存储服务的可选组件。you can also use OpenStack Object Storage instead.
* 认证管理。当使用Copmute系统时，它提供认证和授权服务。you can also use OpenStack Identity as a separate authentication service instead.
* 磁盘控制。它为计算服务提供快速持久的块级别存储。
* 网络控制。它提供虚拟网络，允许计算服务器之间及与公共网络之间的交互， You can also use OpenStack Networking instead.
* 调度器。它用来选择最合适的计算控制器来host实例。
