# 准备RPM源















为了方便，打包服务器和Git源代码托管服务器在同一个服务器git.zhouzhengxi.com上。

* 获取源代码并压缩为tar.gz包
  * 准备文件sourcerepo.list

> 1 #/var/opt/gitlab/git-data/repositories/dev/nova.git
2 #/var/opt/gitlab/git-data/repositories/dev/trove.git
3 #/var/opt/gitlab/git-data/repositories/dev/ceilometer.git
4 #/var/opt/gitlab/git-data/repositories/dev/glance.git
5 #/var/opt/gitlab/git-data/repositories/dev/keystone.git
8 #/var/opt/gitlab/git-data/repositories/dev/horizon.git
9 #/var/opt/gitlab/git-data/repositories/dev/cinder.git
10 #/var/opt/gitlab/git-data/repositories/dev/documents.git
11 #/var/opt/gitlab/git-data/repositories/dev/neutron.git
12 #/var/opt/gitlab/git-data/repositories/dev/oslo.messaging.git
13 #/var/opt/gitlab/git-data/repositories/dev/oslo-db.git
15 #/var/opt/gitlab/git-data/repositories/dev/neutron-lbaas.git
16 #/var/opt/gitlab/git-data/repositories/dev/django_openstack_auth.git
17 #/var/opt/gitlab/git-data/repositories/dev/python-cloudbillingclient.git
18 #/var/opt/gitlab/git-data/repositories/dev/python-cinderclient.git
19 #/var/opt/gitlab/git-data/repositories/dev/python-novaclient.git
20 #/var/opt/gitlab/git-data/repositories/dev/python-neutronclient.git


