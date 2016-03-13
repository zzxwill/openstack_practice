# Summary

* [前言](README.md)
* [(基础背景篇)OpenStack基础结构和组件](introduction/README.md)
   * [OpenStack基础组件](introduction/components.md)
       * [Nova](introduction/basic_components/nova.md)
       * [Glance](introduction/basic_components/glance.md)
       * KeyStone
   * OpenStack 可扩展基础设施型组件
       * Swift
       * Neutron
       * Cinder
       * Designate和Ironic
   * 1.4    OpenStack可选增强型组件
       * Ceilometer
       * 1.4.2    Horizon
       * 1.4.3    Babican
       * 1.5    OpenStack 消费服务型组件
           * 1.5.1    Trove
           * 1.5.2    Heat
           * 1.5.3    Sahara
           * 1.5.4    Macorni
* OpenStack部署
  * DevStack
    * 配置第一个本地OpenStack开发环境
    * 多节点部署
    * 结合Vagrant部署
  * RPM/RDO部署
  * 通过定制关盘和脚本脚本
  * 利用Ansible部署
* 企业级开发中的第三方Python库
  * SQLAlchemy
  * Request
  * Oslo.conf
  * gevent/greenlet/eventlet
* OpenStack企业级应用开发
  * Nova开发
    * 扩展Nova API
    * Instance快照
    * Nova Scheduler
    * Libvirt开发
      * CGroup
      * Python-libevirt和KVM
    * VMware驱动开发
  * Keystone开发
  * Neutron开发
  * Swift开发
  * BillBoard开发
  * Ceph开发
  * Horizon开发
  * Ceilometer开发
  * Heat开发
* (高级篇)关系型数据库
  * MySQL
  * Redis
第六章	网络和存储解决方案
6.1	网络布线
6.2	网段规划
6.3	网络吞吐和时延
6.4	存储设备方案
6.4.1	Ceph
6.4.2	NAS
6.4.3	SAN 
第七章	服务高可用
7.1	控制节点HA
7.2	数据库Master/Master和Master/Slave
7.3	服务单点热点
第八章 	OpenStack其他应用实践与难点
8.1	负载均衡
8.1.1	硬件
8.1.2	软件
8.1.3	数据库
8.2	业务迁移
8.3	资源弹性扩展
8.3.1	Heat4CloudProviders
8.3.2	Senlin
8.4	定制化付费
8.5	报警与处理故障
第三篇 实例篇
第九章	某IDC公有云架构
9.1    业务背景
9.2    初期运营及部署方案
9.3    遇到的问题
9.4    反思
第十章	某外资企业混合结构
10.1    重构原因
10.2    整合openstack后的结构
10.3    维护中踩到的坑
10.4    持续集成和改进
第十一章	某司私有云方案
11.1    初期设计
11.2    需求
11.3    定制化改进
11.4    规模化服务
第十二章	基于Swift的视频存储播放方案
12.1    业务背景
12.2    部署方案
12.3    遇到的问题
12.4    反思
第四篇 调优与扩展篇
第十三章	企业应用调优与排错
13.1	调试
13.1.1	pdb
13.1.2	PyDev Server/Client
13.2	优化
13.2.1	数据库
13.2.2	RPC，长连接
13.3	IO
13.3.1	网络IO
13.3.1.1TCP/IP协议栈
13.3.2	磁盘IO
13.3.2.1	IO栈
第十四章	OpenStack企业应用扩展
14.1	OpenStack和SDN、CDN、DaaS的关系
14.2	性能调优
14.2.1	CPU消耗
14.2.2	内存
14.2.3	网络IO
14.2.4	磁盘IO
14.2.5	systemtap
14.3	OpenStack和Docker


