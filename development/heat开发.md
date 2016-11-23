



**HOT —— OpenStack Heat从入门到实践**





HOT即Heat Orchestration Template，初学者可能会不大好理解Orchestration这个词，WikiPedia的解释比较贴切。

**Orchestration \(computers\)**

**Orchestration** describes the automated arrangement, coordination, and management of complex computer systems, [middleware](dict://key.317097B6E814E043839A3467BA8F4CCE/middleware), and services.

It is often discussed as having an inherent [intelligence \(trait\)](dict://key.317097B6E814E043839A3467BA8F4CCE/intelligence%20%28trait%29) or even implicitly [autonomic](dict://key.317097B6E814E043839A3467BA8F4CCE/autonomic) control, but those are largely aspirations or analogies rather than technical descriptions. In reality, _orchestration_ is largely the effect of [automation](dict://key.317097B6E814E043839A3467BA8F4CCE/automation) or systems deploying elements of [control theory](dict://key.317097B6E814E043839A3467BA8F4CCE/control%20theory).

This usage of _orchestration_ is often discussed in the context of [virtualization](dict://key.317097B6E814E043839A3467BA8F4CCE/virtualization), [provisioning](dict://key.317097B6E814E043839A3467BA8F4CCE/provisioning), and **dynamic datacenter** topics. It is often used as a [buzzword](dict://key.317097B6E814E043839A3467BA8F4CCE/buzzword).

中文可以理解为“编排”，“编制”。直白的理解就是用模板\(template，一个文本文件\)的形式，以约定的格式，把你所需要的元素放入其中，然后通过分析处理这个模板文件来自动化处理某种操作。

比如，你使用云主机时，需要将主机的内存从1G改到2G，一般是登录到云主机控制后台，更改主机配置中的内存。使用“编排”则是将模板中的内存属性从1改为2，然后自动化的去更改主机的内存大小。



![](/assets/change_size_of_instance)

下面我们以一个实际的例子来学习HOT。

[https:\/\/github.com\/zzxwill\/Heat4CloudProviders\/blob\/master\/qingcloud\_heat\_plugin\/template\/qingcloud\_single\_vm\_stack.yaml](https://github.com/zzxwill/Heat4CloudProviders/blob/master/qingcloud_heat_plugin/template/qingcloud_single_vm_stack.yaml)





**第一部分： heat\_template\_version**

指这个HOT的版本，请看官方的解释

[http:\/\/docs.openstack.org\/developer\/heat\/template\_guide\/hot\_spec.html](http://docs.openstack.org/developer/heat/template_guide/hot_spec.html)

2013-05-23

The key with value 2013-05-23 indicates that the YAML document is a HOT template and it may contain features implemented until the **Icehouse** release. This version supports the following functions \(some are back ported to this version\):

2015-04-30

The key with value 2015-04-30 indicates that the YAML document is a HOT template and it may contain features added and\/or removed up until the **Kilo** release. This version adds the repeatfunction. So the complete list of supported functions is:





**第二部分： description**

顾名思义。这个YAML是创建虚拟机用的。





**第三部分：parameters**

![](/assets/heat_parameter)



parameters值传入Heat的参数，创建一个虚拟机时，需要指定创建虚拟机所用到的镜像——image\_id（CentOS 7.0？Ubuntu 14.04?）；需要指定虚拟机创建之后的登录方式——login\_mode（密码登录？SSH Key登录？）





**第四部分： resources**

![](/assets/heat_resources)



resources部分是template的YAML对应的heat resource type，“server”指resource name, "COM::TwoFellows::Server"指resource type，properties指的是resource type的一系列属性，与template里的parameters相对应。具体对应关系，将在后面讲解。





**第五部分： outputs**





outputs指的是resource type的输出，其与Heat resource type类里的attribute相对应，具体对应关系，将在后面讲解。

![](/assets/heat_output)



截止到现在，HOT基本讲解完毕（第四\/五部分将在后面再加强理解）。同时，OpenStack Heat官方也给出了一个Hello World template，你也可以参考下，[https:\/\/github.com\/openstack\/heat-templates\/blob\/master\/hot\/hello\_world.yaml](https://github.com/openstack/heat-templates/blob/master/hot/hello_world.yaml)。











**Heat resource plug-in 开发 —— OpenStack Heat从入门到实践**

Heat resource是什么？通过命令“heat resource-type-list”，我们可以略窥一二。

![](/assets/6871F945-B4CC-4D98-8EC5-04F98F232824.png)

橙色部分是Heat自带的一些resource type，红色部分是我们自己开发的resource type（如果开发工作还没开始，则不会显示）。更准确的说，Heat resource type是以XXX::YYY::ZZZ标志的，一个继承了heat.engine.resource.Resource的Python类，该类可以扩展加强Heat本身的服务。

下面以[https:\/\/github.com\/zzxwill\/Heat4CloudProviders\/blob\/master\/qingcloud\_heat\_plugin\/resources\/server.py](https://github.com/zzxwill/Heat4CloudProviders/blob/master/qingcloud_heat_plugin/resources/server.py)为例，说明resource type COM::TwoFellows::Server。该resource type用来创建、更新、删除一个虚拟机。

方法 def handle\_create\(self\)用来创建resource type，具体而言，是通过方法run\_instances\(）调用青云的API，在青云的云平台上创建一个虚拟机。

ret = conn.run\_instances\(

image\_id=qingcloud\_image\_id,

cpu=1,

memory=1024,

\#vxnets=\['vxnet-0'\],

login\_mode= qingcloud\_login\_mode,

login\_passwd= qingcloud\_login\_passwd\)

方法 def check\_create\_complete\(self, token\)用来检查虚拟机是否创建成功，具体而言，是通过方法describe\_instances（）调用青云的API，检查主机的创建状态。如果主机创建成功，则返回Ture, 标记stack的状态为“CREATE\_COMPLETE”；如果主机创建不成功，则返回False, 标记stack的状态为“CREATE\_FAILED”。

关于如何写handle\_create\(\)和check\_create\_complete（），我会在后面介绍。下面直观的感受一下通过创建stack来创建resource。

执行命令heat stack-create stack-vm-2015092101 -f \/usr\/lib\/heat\/qingcloud\_heat\_plugin\/template\/qingcloud\_vm\_stack.yaml

![](/assets/0542ECC9-90DD-4F0C-B1A6-C1AD44609F73.png)

等一会儿，检查stack状态，stack已经创建成功了。

![](/assets/CBE4DAA6-BA7D-4A32-9A96-EA041D319C11.png)

![](/assets/3FE3D3E2-F005-4357-9B46-D22C935AD813.png)

同时，可以看到一个主机在青云上已经创建好了。

![](/assets/08227716-E923-4CEB-9B92-AE99B342B613.png)

resource type的详情如下。

![](/assets/4A281423-B74B-4DB3-AB51-87FE05CCD14C.png)

我们发现，resource type详情中的perperties和attributes跟上节讲到的HOT十分相关。下篇，我们将讲到这个问题。











**水乳交融的HOT和Resource type Python类 —— OpenStack Heat从入门到实践**





HOT的YAML文件：[https:\/\/github.com\/zzxwill\/Heat4CloudProviders\/blob\/master\/qingcloud\_heat\_plugin\/template\/qingcloud\_vm\_stack.yaml](https://github.com/zzxwill/Heat4CloudProviders/blob/master/qingcloud_heat_plugin/template/qingcloud_vm_stack.yaml)

Heat Resource type Python类：[https:\/\/github.com\/zzxwill\/Heat4CloudProviders\/blob\/master\/qingcloud\_heat\_plugin\/resources\/server.py](https://github.com/zzxwill/Heat4CloudProviders/blob/master/qingcloud_heat_plugin/resources/server.py)





**1. YAML和Python类是怎么关联起来的？**



![](/assets/AF5FD8E1-3470-4D55-BB2F-4281AFC24FC8.png)

创建一个虚拟机的命令是heat stack-create stack-vm-2015092101 -f \/usr\/lib\/heat\/qingcloud\_heat\_plugin\/template\/qingcloud\_vm\_stack.yaml

这个Heat命令是调用Python类server.py。那YAML和Python类是怎么关联起来的呢？

YAML里定义的resource type是“ COM::TwoFellows::Server”，Python里有如下mapping。



![](/assets/CFC05AA6-FB93-4528-9582-6C52DACA8301.png)

即“ COM::TwoFellows::Server” mapping到了QingCloudServer类，而这个类，正好就是server.py。

这样，-f后面YAML就能够指定由那个Python类来执行操作。





**2. YAML怎么传值给Python类？**

![](/assets/BB4DD7CF-D9FD-40CB-867C-CC3F52FAAF18.png)

这里的properties是指类QingCloudServer，该类的properties image\_id通过get\_param获取YAML里parameters里的server\_image\_id

![](/assets/362FA089-5A65-48D6-B064-F2D5E6ED5D45.png)







模板里的parameter server\_image\_id的值trustysrvx64e会根据如下定义“get\_param”



![](/assets/Image.png)

传递给properties\_schema里的IMAGE\_ID.



![](/assets/7374C309-6470-4613-9F47-96F932F16640.png)

IMAGE\_ID表示'image\_id'



![](/assets/362FA089-5A65-48D6-B064-F2D5E6ED5D45.png)

然后，通过self.perperties\[\]获取到YAML模板的传值。



![](/assets/B6503604-F552-4BDC-B6FC-9DFF69F70279.png)

总结：YAML里的parameters根据get\_param将值传递给resource class的properties。





3. Python类是怎么给YAML传值的？

使用stack-show命令可以查看resource的outputs。



![](/assets/354DDC6D-4BF2-46F0-AB1B-304F8AEE74A0.png)

outputs输出那些，是由YAML决定的。



![](/assets/3C5FAAFA-D836-42FF-A867-1707027316D7.png)

instance\_id的值是从server的attribute instance\_id获取的。

server是什么？—— resource type COM::TwoFellows::Server的别称。



![](/assets/E15491C9-87C5-42A0-9B64-6E44669A6FDE.png)

具体的获取方式，是由QingCloudServer类的方法\_resolve\_attribute决定的。

![](/assets/AECAF071-CABB-4AD7-BD63-BAF58D278552.png)



总结：resource type的outputs是由YAML模板决定，根据resource type的\_resolve\_attribute\(\)获取后，通过get\_attr传递给resource type。





这样，HOT和Resource type Python类水乳交融的关系就里清了。













