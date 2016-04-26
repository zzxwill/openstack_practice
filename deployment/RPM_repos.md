# 准备RPM源


TODO:
Git库搭建











为了方便，打包服务器和Git源代码托管服务器在同一个服务器git.zhouzhengxi.com上。
打包的源，分为三类
* Python基础依赖包
* OpenStack的依赖包
* OpenStack各个组件包


以打包Horzion为例。

打包目录如下：
[root@git-new zzfancy]# pwd
/zzfancy
[root@git-new zzfancy]# ls
IaaS_backup  backup  build_all  buildsource  build.vim  cdrom  create_tar_from.sh  xyz-b2b  origin_srpms  sourcerepo.list  srpms  trash  vda_custom.iso

* 获取源代码并压缩为tar.gz包
  * 准备文件sourcerepo.list
```
1 #/var/opt/gitlab/git-data/repositories/dev/nova.git
2 #/var/opt/gitlab/git-data/repositories/dev/trove.git
3 #/var/opt/gitlab/git-data/repositories/dev/ceilometer.git
4 #/var/opt/gitlab/git-data/repositories/dev/glance.git
5 #/var/opt/gitlab/git-data/repositories/dev/keystone.git
8 /var/opt/gitlab/git-data/repositories/dev/horizon.git
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
```
第8行horizon的git位置处于生效状态，改行标记了Horizion组件的源代码位置。
  * 获取源代码
```
source_list=${1:-sourcerepo.list}

cat $source_list |grep -v ^# | while read repo; do
    create_and_copy_tar $repo
done 
```
"grep -v ^#"取出不以"#"开头的行——待获取源代码的组件。
```
[root@builder zzfancy]# source_list=${1:-sourcerepo.list}
[root@builder zzfancy]# cat $source_list | grep -v ^# | while read repo; do echo $repo; done
/var/opt/gitlab/git-data/repositories/dev/horizon.git
```
通过输出$repo，发现的确是horizon.git。






























