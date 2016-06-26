# Summary

* [前言](README.md)
* [（基础背景篇）OpenStack基础结构和组件](introduction/README.md)
   * [OpenStack概述](introduction/openstack_brief.md)
   * [OpenStack基础组件](introduction/components.md)
       * [Nova](introduction/basic_components/nova.md)
       * [Glance](introduction/basic_components/glance.md)
       * KeyStone
   * OpenStack可扩展基础设施型组件
       * Swift
       * Neutron
       * Cinder
       * Designate和Ironic
   * 1.4    OpenStack可选增强型组件
       * Ceilometer
       * [1.4.2    Horizon](optional_enhanced_components/horizon.md)
       * 1.4.3    Babican
       * 1.5    OpenStack 消费服务型组件
           * 1.5.1    Trove
           * 1.5.2    Heat
           * 1.5.3    Sahara
           * 1.5.4    Macorni
* （基础背景篇）OpenStack部署
   * DevStack
       * 配置第一个本地OpenStack开发环境
       * 多节点部署
       * 结合Vagrant部署
   * [RPM/RDO部署](deployment/rpm_rdo.md)
   * 通过定制光盘和脚本安装
       * [准备RPM源](deployment/RPM_repos.md)
   * 利用Ansible部署
* 企业级开发中的第三方Python库
   * SQLAlchemy
   * Request
   * Oslo.conf
   * gevent/greenlet/eventlet
* （基础背景篇）OpenStack企业级应用开发
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
* （高级篇）关系型数据库
   * MySQL
   * Redis
* （高级篇）网络和存储解决方案
   * 网络布线
   * 网段规划
   * 网络吞吐和时延
   * 存储设备方案
       * Ceph
       * NAS
       * SAN
* （高级篇）服务高可用
   * 控制节点HA
   * 数据库Master/Master和Master/Slave
   * 服务单点热点
* （高级篇）OpenStack其他应用实践与难点
   * 负载均衡
       * 硬件
       * 软件
       * 数据库
   * 业务迁移
   * 资源弹性扩展
       * Heat4CloudProviders
       * [Senlin](practice_and_difficulties/senlin.md)
   * 定制化付费
   * 报警与处理故障
* （实例篇）某IDC公有云架构
   * 业务背景
   * 初期运营及部署方案
   * 遇到的问题
   * 反思
* （实例篇）某外资企业混合结构
   * 重构原因
   * 整合openstack后的结构
   * 维护中踩到的坑
   * 持续集成和改进
* （实例篇）某司私有云方案
   * 初期设计
   * 需求
   * 定制化改进
   * 规模化服务
* （实例篇）基于Swift的视频存储播放方案
   * 业务背景
   * 部署方案
   * 遇到的问题
   * 反思
* （调优与扩展篇）企业应用调优与排错
   * 调试
       * pdb
       * PyDev Server/Client
   * 优化
       * 数据库
       * RPC，长连接
       * IO
           * 网络IO
               * TCP/IP协议栈
           * 磁盘IO
               * IO栈
* （调优与扩展篇）OpenStack企业应用扩展
   * OpenStack和SDN、CDN、DaaS的关系
   * 性能调优
       * CPU消耗
       * 内存
       * 网络IO
       * 磁盘IO
       * systemtap
   * OpenStack和Docker
   * OpenStack升级
       * [Horizon从Juno到Mitaka升级实践](extension/openstack_upgration/upgrade_horizon_from_juno_to_mitaka.md)

