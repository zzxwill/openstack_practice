# Horizon从Juno到Mitaka升级实践

当前版本：Horizon 2014.2.2 release https://launchpad.net/horizon/juno/2014.2.2/+download/horizon-2014.2.2.tar.gz
目标版本：Mitaka的stable-mitaka分支

## Keystone认证版本升级


Overrides for OpenStack API versions. Use this setting to force the
OpenStack dashboard to use a specific API version for a given service API.
NOTE: The version should be formatted as it appears in the URL for the
service API. For example, The identity service APIs have inconsistent
use of the decimal point, so valid options would be "2.0" or "3".


OPENSTACK_API_VERSIONS = {
     "identity": 3,
}

