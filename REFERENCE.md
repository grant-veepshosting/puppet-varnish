# Reference

<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Table of Contents

### Classes

#### Public Classes

* [`varnish`](#varnish): Installs and configures Varnish.
* [`varnish::controller::agent`](#varnish--controller--agent): Installs and manages Varnish Controller Agent
* [`varnish::firewall`](#varnish--firewall): Uses `puppetlabs/firewall` module to open varnish listen port
* [`varnish::hitch`](#varnish--hitch): Installs Hitch the SSL Offloading Proxy of Varnish Enterprise
* [`varnish::install`](#varnish--install): Installs Varnish
* [`varnish::ncsa`](#varnish--ncsa): Allows setup of varnishncsa
* [`varnish::repo`](#varnish--repo): This class installs aditional repos for varnish
* [`varnish::shmlog`](#varnish--shmlog): Mounts shmlog as tempfs
* [`varnish::vcl`](#varnish--vcl): Manages the Varnish VCL configuration

#### Private Classes

* `varnish::service`: Manages the Varnish service

### Defined types

#### Public Defined types

* [`varnish::vcl::acl`](#varnish--vcl--acl): Defines an ACL Type of Varnish. Defined ACL's must be used in VCL
* [`varnish::vcl::acl_member`](#varnish--vcl--acl_member)
* [`varnish::vcl::backend`](#varnish--vcl--backend): Defines a Backend for VCL
* [`varnish::vcl::director`](#varnish--vcl--director): Defines a backend director in varnish vcl
* [`varnish::vcl::probe`](#varnish--vcl--probe): Defines a VCL Probe, that can be used for healthchecks for backends
* [`varnish::vcl::selector`](#varnish--vcl--selector): Adds a selector to handle multiple backends

#### Private Defined types

* `varnish::vcl::includefile`: Used by vcl.pp to create the config files with header sections

### Data types

* [`Varnish::Controller::Agent_name`](#Varnish--Controller--Agent_name): Type for supported Agent Name of Controller Agent
* [`Varnish::Vclversion`](#Varnish--Vclversion): Type for supported VCL Versions

## Classes

### <a name="varnish"></a>`varnish`

Installs and configures Varnish.

#### Examples

##### Installs Varnish

```puppet
# enables Varnish service
# uses default VCL '/etc/varnish/default.vcl'
include varnish
```

##### Installs Varnish with custom options

```puppet
# sets Varnish to listen on port 80
# storage size is set to 2 GB
# vcl file is '/etc/varnish/my-vcl.vcl'
class { 'varnish':
  varnish_listen_port  => 80,
  varnish_storage_size => '2G',
  varnish_vcl_conf     => '/etc/varnish/my-vcl.vcl',
}
```

#### Parameters

The following parameters are available in the `varnish` class:

* [`service_ensure`](#-varnish--service_ensure)
* [`reload_vcl`](#-varnish--reload_vcl)
* [`nfiles`](#-varnish--nfiles)
* [`memlock`](#-varnish--memlock)
* [`storage_type`](#-varnish--storage_type)
* [`varnish_vcl_conf`](#-varnish--varnish_vcl_conf)
* [`varnish_user`](#-varnish--varnish_user)
* [`varnish_jail_user`](#-varnish--varnish_jail_user)
* [`varnish_group`](#-varnish--varnish_group)
* [`varnish_listen_address`](#-varnish--varnish_listen_address)
* [`varnish_listen_port`](#-varnish--varnish_listen_port)
* [`varnish_proxy_listen_address`](#-varnish--varnish_proxy_listen_address)
* [`varnish_proxy_listen_port`](#-varnish--varnish_proxy_listen_port)
* [`varnish_admin_listen_address`](#-varnish--varnish_admin_listen_address)
* [`varnish_admin_listen_port`](#-varnish--varnish_admin_listen_port)
* [`varnish_min_threads`](#-varnish--varnish_min_threads)
* [`varnish_max_threads`](#-varnish--varnish_max_threads)
* [`varnish_thread_timeout`](#-varnish--varnish_thread_timeout)
* [`varnish_storage_size`](#-varnish--varnish_storage_size)
* [`varnish_secret_file`](#-varnish--varnish_secret_file)
* [`varnish_storage_file`](#-varnish--varnish_storage_file)
* [`mse_config`](#-varnish--mse_config)
* [`mse_config_file`](#-varnish--mse_config_file)
* [`varnish_ttl`](#-varnish--varnish_ttl)
* [`varnish_enterprise`](#-varnish--varnish_enterprise)
* [`varnish_enterprise_vmods_extra`](#-varnish--varnish_enterprise_vmods_extra)
* [`vcl_dir`](#-varnish--vcl_dir)
* [`shmlog_dir`](#-varnish--shmlog_dir)
* [`shmlog_tempfs`](#-varnish--shmlog_tempfs)
* [`version`](#-varnish--version)
* [`add_repo`](#-varnish--add_repo)
* [`manage_firewall`](#-varnish--manage_firewall)
* [`varnish_conf_template`](#-varnish--varnish_conf_template)
* [`conf_file_path`](#-varnish--conf_file_path)
* [`additional_parameters`](#-varnish--additional_parameters)
* [`default_version`](#-varnish--default_version)
* [`add_hitch`](#-varnish--add_hitch)

##### <a name="-varnish--service_ensure"></a>`service_ensure`

Data type: `Stdlib::Ensure::Service`

Ensure for varnishservice

Default value: `'running'`

##### <a name="-varnish--reload_vcl"></a>`reload_vcl`

Data type: `Boolean`

V4 paramter if Varnish will be reloaded - deprecated
Will be removed when support for RHEL7 is dropped

Default value: `true`

##### <a name="-varnish--nfiles"></a>`nfiles`

Data type: `String`

passed to varnish conf-file

Default value: `'131072'`

##### <a name="-varnish--memlock"></a>`memlock`

Data type: `String`

passed to varnish conf-file

Default value: `'100M'`

##### <a name="-varnish--storage_type"></a>`storage_type`

Data type: `String`

which storage will be used for varnish - default malloc

Default value: `'malloc'`

##### <a name="-varnish--varnish_vcl_conf"></a>`varnish_vcl_conf`

Data type: `Stdlib::Absolutepath`

path to main vcl file

Default value: `'/etc/varnish/default.vcl'`

##### <a name="-varnish--varnish_user"></a>`varnish_user`

Data type: `String`

passed to varnish-conf

Default value: `'varnish'`

##### <a name="-varnish--varnish_jail_user"></a>`varnish_jail_user`

Data type: `String`

passed to varnish-conf

Default value: `'vcache'`

##### <a name="-varnish--varnish_group"></a>`varnish_group`

Data type: `String`

passed to varnish-conf

Default value: `'varnish'`

##### <a name="-varnish--varnish_listen_address"></a>`varnish_listen_address`

Data type: `Optional[String[1]]`

Address varnish will bind to - default ''

Default value: `undef`

##### <a name="-varnish--varnish_listen_port"></a>`varnish_listen_port`

Data type: `Stdlib::Port`

port varnish wil bind to

Default value: `6081`

##### <a name="-varnish--varnish_proxy_listen_address"></a>`varnish_proxy_listen_address`

Data type: `String`

address varnish binds to in proxy mode

Default value: `'127.0.0.1'`

##### <a name="-varnish--varnish_proxy_listen_port"></a>`varnish_proxy_listen_port`

Data type: `Optional[Stdlib::Port]`

port varnish binds to in proxy mode

Default value: `undef`

##### <a name="-varnish--varnish_admin_listen_address"></a>`varnish_admin_listen_address`

Data type: `String`

address varnish binds to in admin mode

Default value: `'localhost'`

##### <a name="-varnish--varnish_admin_listen_port"></a>`varnish_admin_listen_port`

Data type: `Stdlib::Port`

port varnish binds to in admin mode

Default value: `6082`

##### <a name="-varnish--varnish_min_threads"></a>`varnish_min_threads`

Data type: `String`

minumum no of varnish worker threads

Default value: `'5'`

##### <a name="-varnish--varnish_max_threads"></a>`varnish_max_threads`

Data type: `String`

maximum no of varnish worker threads

Default value: `'500'`

##### <a name="-varnish--varnish_thread_timeout"></a>`varnish_thread_timeout`

Data type: `String`



Default value: `'300'`

##### <a name="-varnish--varnish_storage_size"></a>`varnish_storage_size`

Data type: `String`

defines the size of storage (depending of storage_type)

Default value: `'1G'`

##### <a name="-varnish--varnish_secret_file"></a>`varnish_secret_file`

Data type: `Stdlib::Absolutepath`

path to varnish secret file

Default value: `'/etc/varnish/secret'`

##### <a name="-varnish--varnish_storage_file"></a>`varnish_storage_file`

Data type: `Stdlib::Absolutepath`

defines the filepath of storage (depending of storage_type)

Default value: `'/var/lib/varnish-storage/varnish_storage.bin'`

##### <a name="-varnish--mse_config"></a>`mse_config`

Data type: `Optional[String[1]]`

MSE Config, see https://docs.varnish-software.com/varnish-cache-plus/features/mse/

Default value: `undef`

##### <a name="-varnish--mse_config_file"></a>`mse_config_file`

Data type: `Stdlib::Absolutepath`

filepath where mse config file will be stored

Default value: `'/etc/varnish/mse.conf'`

##### <a name="-varnish--varnish_ttl"></a>`varnish_ttl`

Data type: `String`

default ttl for items

Default value: `'120'`

##### <a name="-varnish--varnish_enterprise"></a>`varnish_enterprise`

Data type: `Boolean`

passed to varnish::install

Default value: `false`

##### <a name="-varnish--varnish_enterprise_vmods_extra"></a>`varnish_enterprise_vmods_extra`

Data type: `Boolean`

passed to varnish::install

Default value: `false`

##### <a name="-varnish--vcl_dir"></a>`vcl_dir`

Data type: `Optional[Stdlib::Absolutepath]`

dir where varnish vcl will be stored

Default value: `undef`

##### <a name="-varnish--shmlog_dir"></a>`shmlog_dir`

Data type: `Stdlib::Absolutepath`

location for shmlog

Default value: `'/var/lib/varnish'`

##### <a name="-varnish--shmlog_tempfs"></a>`shmlog_tempfs`

Data type: `Boolean`

mounts shmlog directory as tmpfs

Default value: `true`

##### <a name="-varnish--version"></a>`version`

Data type: `String[1]`

passed to puppet type 'package', attribute 'ensure'

Default value: `present`

##### <a name="-varnish--add_repo"></a>`add_repo`

Data type: `Boolean`

if set to false (defaults to true), the yum/apt repo is not added

Default value: `false`

##### <a name="-varnish--manage_firewall"></a>`manage_firewall`

Data type: `Boolean`

passed to varnish::firewall

Default value: `false`

##### <a name="-varnish--varnish_conf_template"></a>`varnish_conf_template`

Data type: `String[1]`

Template that will be used for varnish conf

Default value: `'varnish/varnish-conf.erb'`

##### <a name="-varnish--conf_file_path"></a>`conf_file_path`

Data type: `Stdlib::Absolutepath`

path where varnish conf will be stored

Default value: `'/etc/varnish/varnish.params'`

##### <a name="-varnish--additional_parameters"></a>`additional_parameters`

Data type: `Hash`

additional parameters that will be passed to varnishd with -p

Default value: `{}`

##### <a name="-varnish--default_version"></a>`default_version`

Data type: `Integer`

Default major version of Varnish for that OS release

Default value: `6`

##### <a name="-varnish--add_hitch"></a>`add_hitch`

Data type: `Boolean`

Add varnish::hitch class to install hitch

Default value: `false`

### <a name="varnish--controller--agent"></a>`varnish::controller::agent`

Installs and manages Varnish Controller Agent

#### Examples

##### 

```puppet
include varnish::controller::agent
```

#### Parameters

The following parameters are available in the `varnish::controller::agent` class:

* [`base_url`](#-varnish--controller--agent--base_url)
* [`nats_server`](#-varnish--controller--agent--nats_server)
* [`nats_server_port`](#-varnish--controller--agent--nats_server_port)
* [`nats_server_user`](#-varnish--controller--agent--nats_server_user)
* [`nats_server_password`](#-varnish--controller--agent--nats_server_password)
* [`agent_name`](#-varnish--controller--agent--agent_name)
* [`invalidation_host`](#-varnish--controller--agent--invalidation_host)
* [`package_name`](#-varnish--controller--agent--package_name)
* [`package_ensure`](#-varnish--controller--agent--package_ensure)
* [`service_ensure`](#-varnish--controller--agent--service_ensure)

##### <a name="-varnish--controller--agent--base_url"></a>`base_url`

Data type: `Stdlib::HTTPUrl`

see https://docs.varnish-software.com/varnish-controller/installation/agents/#base-url

##### <a name="-varnish--controller--agent--nats_server"></a>`nats_server`

Data type: `Stdlib::Host`

Server for NATS Connection

##### <a name="-varnish--controller--agent--nats_server_port"></a>`nats_server_port`

Data type: `Stdlib::Port`

Port for Nats Connection

Default value: `4222`

##### <a name="-varnish--controller--agent--nats_server_user"></a>`nats_server_user`

Data type: `Optional[String]`

User for Nats Connection

Default value: `undef`

##### <a name="-varnish--controller--agent--nats_server_password"></a>`nats_server_password`

Data type: `Optional[Variant[Sensitive[String],String]]`

Password for Nats Connection

Default value: `undef`

##### <a name="-varnish--controller--agent--agent_name"></a>`agent_name`

Data type: `Varnish::Controller::Agent_name`

see https://docs.varnish-software.com/varnish-controller/installation/agents/#setting-the-agent-name

Default value: `$facts['networking']['hostname']`

##### <a name="-varnish--controller--agent--invalidation_host"></a>`invalidation_host`

Data type: `String[1]`

see https://docs.varnish-software.com/varnish-controller/installation/agents/#varnish-interaction

Default value: `'127.0.0.1:80'`

##### <a name="-varnish--controller--agent--package_name"></a>`package_name`

Data type: `String[1]`

Name of the Package used for installation

Default value: `'varnish-controller-agent'`

##### <a name="-varnish--controller--agent--package_ensure"></a>`package_ensure`

Data type: `String[1]`

Ensure of the Package

Default value: `'present'`

##### <a name="-varnish--controller--agent--service_ensure"></a>`service_ensure`

Data type: `Stdlib::Ensure::Service`

Ensure of Agent Service

Default value: `'running'`

### <a name="varnish--firewall"></a>`varnish::firewall`

Uses `puppetlabs/firewall` module to open varnish listen port

#### Parameters

The following parameters are available in the `varnish::firewall` class:

* [`manage_firewall`](#-varnish--firewall--manage_firewall)
* [`varnish_listen_port`](#-varnish--firewall--varnish_listen_port)

##### <a name="-varnish--firewall--manage_firewall"></a>`manage_firewall`

Data type: `Boolean`

Manage firewall

Default value: `false`

##### <a name="-varnish--firewall--varnish_listen_port"></a>`varnish_listen_port`

Data type: `Stdlib::Port`

Port where varnish listens to

Default value: `6081`

### <a name="varnish--hitch"></a>`varnish::hitch`

Installs Hitch the SSL Offloading Proxy of Varnish Enterprise

* **See also**
  * https://github.com/varnish/hitch/blob/master/hitch.conf.man.rst

#### Examples

##### 

```puppet
include varnish::hitch
```

#### Parameters

The following parameters are available in the `varnish::hitch` class:

* [`package_name`](#-varnish--hitch--package_name)
* [`package_ensure`](#-varnish--hitch--package_ensure)
* [`service_ensure`](#-varnish--hitch--service_ensure)
* [`service_name`](#-varnish--hitch--service_name)
* [`config_path`](#-varnish--hitch--config_path)
* [`config_template`](#-varnish--hitch--config_template)
* [`frontends`](#-varnish--hitch--frontends)
* [`backend`](#-varnish--hitch--backend)
* [`pem_files`](#-varnish--hitch--pem_files)
* [`ssl_engine`](#-varnish--hitch--ssl_engine)
* [`tls_protos`](#-varnish--hitch--tls_protos)
* [`ciphers`](#-varnish--hitch--ciphers)
* [`ciphersuites`](#-varnish--hitch--ciphersuites)
* [`workers`](#-varnish--hitch--workers)
* [`backlog`](#-varnish--hitch--backlog)
* [`keepalive`](#-varnish--hitch--keepalive)
* [`chroot`](#-varnish--hitch--chroot)
* [`user`](#-varnish--hitch--user)
* [`group`](#-varnish--hitch--group)
* [`log_level`](#-varnish--hitch--log_level)
* [`syslog`](#-varnish--hitch--syslog)
* [`syslog_facility`](#-varnish--hitch--syslog_facility)
* [`daemon`](#-varnish--hitch--daemon)
* [`write_proxy`](#-varnish--hitch--write_proxy)
* [`sni_nomatch_abort`](#-varnish--hitch--sni_nomatch_abort)
* [`tcp_fastopen`](#-varnish--hitch--tcp_fastopen)
* [`alpn_protos`](#-varnish--hitch--alpn_protos)
* [`additional_parameters`](#-varnish--hitch--additional_parameters)

##### <a name="-varnish--hitch--package_name"></a>`package_name`

Data type: `String[1]`

Define used package name

Default value: `'varnish-plus-addon-ssl'`

##### <a name="-varnish--hitch--package_ensure"></a>`package_ensure`

Data type: `String[1]`

Ensure package

Default value: `'present'`

##### <a name="-varnish--hitch--service_ensure"></a>`service_ensure`

Data type: `Stdlib::Ensure::Service`

Ensure Service status

Default value: `'running'`

##### <a name="-varnish--hitch--service_name"></a>`service_name`

Data type: `String[1]`

Service name for hitch (must match installed)

Default value: `'hitch'`

##### <a name="-varnish--hitch--config_path"></a>`config_path`

Data type: `Stdlib::Absolutepath`

Path for hitch config

Default value: `'/etc/hitch/hitch.conf'`

##### <a name="-varnish--hitch--config_template"></a>`config_template`

Data type: `String[1]`

Used EPP Config template

Default value: `'varnish/hitch.conf.epp'`

##### <a name="-varnish--hitch--frontends"></a>`frontends`

Data type: `Array[Struct[{ host => String[1],port => Stdlib::Port }],1]`

Define Frontends for hitch

Default value: `[{ 'host'=> '*', 'port'=> 443, }]`

##### <a name="-varnish--hitch--backend"></a>`backend`

Data type: `String[1]`

Define Backend

Default value: `'[127.0.0.1]:8443'`

##### <a name="-varnish--hitch--pem_files"></a>`pem_files`

Data type: `Array[Stdlib::Absolutepath,1]`

PEM Files that will be loaded

##### <a name="-varnish--hitch--ssl_engine"></a>`ssl_engine`

Data type: `Optional[String[1]]`

Set the ssl-engine

Default value: `undef`

##### <a name="-varnish--hitch--tls_protos"></a>`tls_protos`

Data type: `String[1]`

allowed TLS Protos

Default value: `'TLSv1.2 TLSv1.3'`

##### <a name="-varnish--hitch--ciphers"></a>`ciphers`

Data type: `String[1]`

allowed ciphers

Default value: `'EECDH+AESGCM:EDH+AESGCM'`

##### <a name="-varnish--hitch--ciphersuites"></a>`ciphersuites`

Data type: `String[1]`

allowd cipersuites for TLS1.3+

Default value: `'TLS_AES_256_GCM_SHA384:TLS_CHACHA20_POLY1305_SHA256:TLS_AES_128_GCM_SHA256'`

##### <a name="-varnish--hitch--workers"></a>`workers`

Data type: `Variant[Enum['auto'],Integer[1,1024]]`

number of workers

Default value: `'auto'`

##### <a name="-varnish--hitch--backlog"></a>`backlog`

Data type: `Integer[1]`

Listen backlog size

Default value: `200`

##### <a name="-varnish--hitch--keepalive"></a>`keepalive`

Data type: `Integer[1]`

Number of seconds a TCP socket is kept alive

Default value: `3600`

##### <a name="-varnish--hitch--chroot"></a>`chroot`

Data type: `Optional[Stdlib::Absolutepath]`

Chroot directory

Default value: `undef`

##### <a name="-varnish--hitch--user"></a>`user`

Data type: `String[1]`

User to run as. If Hitch is started as root, it will insist on changing to a user with lower rights after binding to sockets.

Default value: `'hitch'`

##### <a name="-varnish--hitch--group"></a>`group`

Data type: `String[1]`

If given, Hitch will change to this group after binding to listen sockets.

Default value: `'hitch'`

##### <a name="-varnish--hitch--log_level"></a>`log_level`

Data type: `Integer[0,2]`

Log chattiness. 0=silence, 1=errors, 2=info/debug.
This setting can also be changed at run-time by editing the configuration file followed by a reload (SIGHUP).

Default value: `1`

##### <a name="-varnish--hitch--syslog"></a>`syslog`

Data type: `Boolean`

Send messages to syslog.

Default value: `true`

##### <a name="-varnish--hitch--syslog_facility"></a>`syslog_facility`

Data type: `Stdlib::Syslogfacility`

Set the syslog facility.

Default value: `'daemon'`

##### <a name="-varnish--hitch--daemon"></a>`daemon`

Data type: `Boolean`

Run as daemon

Default value: `true`

##### <a name="-varnish--hitch--write_proxy"></a>`write_proxy`

Data type: `Enum['ip','v1','v2','proxy']`

Which Proxy mode is used

Default value: `'v2'`

##### <a name="-varnish--hitch--sni_nomatch_abort"></a>`sni_nomatch_abort`

Data type: `Boolean`

Abort handshake when the client submits an unrecognized SNI server name.

Default value: `false`

##### <a name="-varnish--hitch--tcp_fastopen"></a>`tcp_fastopen`

Data type: `Boolean`

Enable TCP Fast Open.

Default value: `false`

##### <a name="-varnish--hitch--alpn_protos"></a>`alpn_protos`

Data type: `String[1]`

Comma separated list of protocols supported by the backend

Default value: `'h2,http/1.1'`

##### <a name="-varnish--hitch--additional_parameters"></a>`additional_parameters`

Data type: `Hash[String[1],Variant[String[1],Integer[1]]]`

Add parameters additional as needed

Default value: `{}`

### <a name="varnish--install"></a>`varnish::install`

Installs Varnish

#### Examples

##### Install Varnish

```puppet
include 'varnish::install'
```

##### Make sure latest version is always installed

```puppet
class { 'varnish::install':
 version => latest,
}
```

#### Parameters

The following parameters are available in the `varnish::install` class:

* [`add_repo`](#-varnish--install--add_repo)
* [`manage_firewall`](#-varnish--install--manage_firewall)
* [`varnish_listen_port`](#-varnish--install--varnish_listen_port)
* [`package_name`](#-varnish--install--package_name)
* [`varnish_enterprise`](#-varnish--install--varnish_enterprise)
* [`varnish_enterprise_vmods_extra`](#-varnish--install--varnish_enterprise_vmods_extra)
* [`version`](#-varnish--install--version)

##### <a name="-varnish--install--add_repo"></a>`add_repo`

Data type: `Boolean`

if repo should be added

Default value: `true`

##### <a name="-varnish--install--manage_firewall"></a>`manage_firewall`

Data type: `Boolean`

if firewall should be managed

Default value: `false`

##### <a name="-varnish--install--varnish_listen_port"></a>`varnish_listen_port`

Data type: `Stdlib::Port`

port that varnish should listen to

Default value: `6081`

##### <a name="-varnish--install--package_name"></a>`package_name`

Data type: `Optional[String]`

manually define package name for installation

Default value: `undef`

##### <a name="-varnish--install--varnish_enterprise"></a>`varnish_enterprise`

Data type: `Boolean`

If varnish enterprise packages should be installed

Default value: `false`

##### <a name="-varnish--install--varnish_enterprise_vmods_extra"></a>`varnish_enterprise_vmods_extra`

Data type: `Boolean`

if varnish enterprise extra vmods should also be installed

Default value: `false`

##### <a name="-varnish--install--version"></a>`version`

Data type: `String`

passed to puppet type 'package', attribute 'ensure'

Default value: `'present'`

### <a name="varnish--ncsa"></a>`varnish::ncsa`

Allows setup of varnishncsa

#### Parameters

The following parameters are available in the `varnish::ncsa` class:

* [`enable`](#-varnish--ncsa--enable)
* [`service_ensure`](#-varnish--ncsa--service_ensure)
* [`varnishncsa_daemon_opts`](#-varnish--ncsa--varnishncsa_daemon_opts)

##### <a name="-varnish--ncsa--enable"></a>`enable`

Data type: `Boolean`

enable service

Default value: `true`

##### <a name="-varnish--ncsa--service_ensure"></a>`service_ensure`

Data type: `Stdlib::Ensure::Service`

ensure serice

Default value: `'running'`

##### <a name="-varnish--ncsa--varnishncsa_daemon_opts"></a>`varnishncsa_daemon_opts`

Data type: `Optional[String]`

Options handed to varnishncsa

Default value: `undef`

### <a name="varnish--repo"></a>`varnish::repo`

This class installs aditional repos for varnish

#### Parameters

The following parameters are available in the `varnish::repo` class:

* [`version`](#-varnish--repo--version)
* [`enable`](#-varnish--repo--enable)

##### <a name="-varnish--repo--version"></a>`version`

Data type: `Optional[String]`

Version of varnish for repo

Default value: `undef`

##### <a name="-varnish--repo--enable"></a>`enable`

Data type: `Boolean`

If repo will be managed

Default value: `false`

### <a name="varnish--shmlog"></a>`varnish::shmlog`

Mounts shmlog as tempfs

#### Examples

##### Disable config for mounting shmlog as tmpfs

```puppet
class { 'varnish::shmlog':
  tempfs => false,
}
```

#### Parameters

The following parameters are available in the `varnish::shmlog` class:

* [`shmlog_dir`](#-varnish--shmlog--shmlog_dir)
* [`tempfs`](#-varnish--shmlog--tempfs)
* [`size`](#-varnish--shmlog--size)

##### <a name="-varnish--shmlog--shmlog_dir"></a>`shmlog_dir`

Data type: `Stdlib::Absolutepath`

directory where Varnish logs

Default value: `'/var/lib/varnish'`

##### <a name="-varnish--shmlog--tempfs"></a>`tempfs`

Data type: `Boolean`

mount or not shmlog as tmpfs, boolean

Default value: `true`

##### <a name="-varnish--shmlog--size"></a>`size`

Data type: `String`

size definition of shmlog tmpfs

Default value: `'170M'`

### <a name="varnish--vcl"></a>`varnish::vcl`

To change name/location of vcl file, use $varnish_vcl_conf in the main varnish class

NOTE: though you can pass config for backends, directors, acls, probes and selectors
      as parameters to this class, it is recommended to use existing definitions instead:
      varnish::backend
      varnish::director
      varnish::probe
      varnish::acl
      varnish::selector
      See README for details on how to use those

* **Note** VCL applies following restictions:
- if you define an acl it must be used
- if you define a probe it must be used
- if you define a backend it must be used
- if you define a director it must be used
You cannot define 2 or more backends/directors and not to have selectors
Not following above rules will result in VCL compilation failure

#### Parameters

The following parameters are available in the `varnish::vcl` class:

* [`functions`](#-varnish--vcl--functions)
* [`probes`](#-varnish--vcl--probes)
* [`backends`](#-varnish--vcl--backends)
* [`directors`](#-varnish--vcl--directors)
* [`selectors`](#-varnish--vcl--selectors)
* [`acls`](#-varnish--vcl--acls)
* [`blockedips`](#-varnish--vcl--blockedips)
* [`blockedbots`](#-varnish--vcl--blockedbots)
* [`enable_waf`](#-varnish--vcl--enable_waf)
* [`pipe_uploads`](#-varnish--vcl--pipe_uploads)
* [`wafexceptions`](#-varnish--vcl--wafexceptions)
* [`purgeips`](#-varnish--vcl--purgeips)
* [`includedir`](#-varnish--vcl--includedir)
* [`manage_includes`](#-varnish--vcl--manage_includes)
* [`cookiekeeps`](#-varnish--vcl--cookiekeeps)
* [`defaultgrace`](#-varnish--vcl--defaultgrace)
* [`min_cache_time`](#-varnish--vcl--min_cache_time)
* [`static_cache_time`](#-varnish--vcl--static_cache_time)
* [`gziptypes`](#-varnish--vcl--gziptypes)
* [`template`](#-varnish--vcl--template)
* [`logrealip`](#-varnish--vcl--logrealip)
* [`honor_backend_ttl`](#-varnish--vcl--honor_backend_ttl)
* [`cond_requests`](#-varnish--vcl--cond_requests)
* [`x_forwarded_proto`](#-varnish--vcl--x_forwarded_proto)
* [`https_redirect`](#-varnish--vcl--https_redirect)
* [`drop_stat_cookies`](#-varnish--vcl--drop_stat_cookies)
* [`cond_unset_cookies`](#-varnish--vcl--cond_unset_cookies)
* [`unset_headers`](#-varnish--vcl--unset_headers)
* [`unset_headers_debugips`](#-varnish--vcl--unset_headers_debugips)
* [`vcl_version`](#-varnish--vcl--vcl_version)

##### <a name="-varnish--vcl--functions"></a>`functions`

Data type: `Hash`

Hash of additional function definitions

Default value: `{}`

##### <a name="-varnish--vcl--probes"></a>`probes`

Data type: `Hash`

Hash of probes, defined as varnish::vcl::probe

Default value: `{}`

##### <a name="-varnish--vcl--backends"></a>`backends`

Data type: `Hash`

Hash of backends, defined as varnish::vcl::backend

Default value: `{ 'default' => { host => '127.0.0.1', port => 8080 } }`

##### <a name="-varnish--vcl--directors"></a>`directors`

Data type: `Hash`

Hash of directors, defined as varnish::vcl::director

Default value: `{}`

##### <a name="-varnish--vcl--selectors"></a>`selectors`

Data type: `Hash`

Hash of selectors, defined as varnish::vcl::selector

Default value: `{}`

##### <a name="-varnish--vcl--acls"></a>`acls`

Data type: `Hash`

Hash of acls, defined as varnish::vcl::acl

Default value: `{}`

##### <a name="-varnish--vcl--blockedips"></a>`blockedips`

Data type: `Array`

Array of IP's that will be blocked with default VCL

Default value: `[]`

##### <a name="-varnish--vcl--blockedbots"></a>`blockedbots`

Data type: `Array`

Array of UserAgent Bots that will be blocked

Default value: `[]`

##### <a name="-varnish--vcl--enable_waf"></a>`enable_waf`

Data type: `Boolean`

controls VCL WAF component, can be true or false

Default value: `false`

##### <a name="-varnish--vcl--pipe_uploads"></a>`pipe_uploads`

Data type: `Boolean`

If the request is a post/put upload (chunked or multipart),
pipe the request to the backend.

Default value: `false`

##### <a name="-varnish--vcl--wafexceptions"></a>`wafexceptions`

Data type: `Array[String]`

Exclude those rules

Default value: `['57' , '56' , '34']`

##### <a name="-varnish--vcl--purgeips"></a>`purgeips`

Data type: `Array[Stdlib::IP::Address]`

source ips which are allowed to send purge requests

Default value: `[]`

##### <a name="-varnish--vcl--includedir"></a>`includedir`

Data type: `Stdlib::Absolutepath`

Dir for includefiles

Default value: `'/etc/varnish/includes'`

##### <a name="-varnish--vcl--manage_includes"></a>`manage_includes`

Data type: `Boolean`

If Includes (and Subtypes like directors, probes,.. ) should be created

Default value: `true`

##### <a name="-varnish--vcl--cookiekeeps"></a>`cookiekeeps`

Data type: `Array[String]`

Cookies that should be kept for backend

Default value: `['__ac', '_ZopeId', 'captchasessionid', 'statusmessages', '__cp', 'MoodleSession']`

##### <a name="-varnish--vcl--defaultgrace"></a>`defaultgrace`

Data type: `Optional[String]`

Default Grace time for Iptems

Default value: `undef`

##### <a name="-varnish--vcl--min_cache_time"></a>`min_cache_time`

Data type: `String`

Default Cache time

Default value: `'60s'`

##### <a name="-varnish--vcl--static_cache_time"></a>`static_cache_time`

Data type: `String`

Cache Time for static Elements like images,..

Default value: `'5m'`

##### <a name="-varnish--vcl--gziptypes"></a>`gziptypes`

Data type: `Array[String]`

Content Types that will be gziped

Default value: `['text/', 'application/xml', 'application/rss', 'application/xhtml', 'application/javascript', 'application/x-javascript']`

##### <a name="-varnish--vcl--template"></a>`template`

Data type: `Optional[String]`

Overwrite Template for VCL

Default value: `undef`

##### <a name="-varnish--vcl--logrealip"></a>`logrealip`

Data type: `Boolean`

Create std.log entry with Real IP of client

Default value: `false`

##### <a name="-varnish--vcl--honor_backend_ttl"></a>`honor_backend_ttl`

Data type: `Boolean`

if Backend TTL will be honored

Default value: `false`

##### <a name="-varnish--vcl--cond_requests"></a>`cond_requests`

Data type: `Boolean`

if condtional requests are allowed

Default value: `false`

##### <a name="-varnish--vcl--x_forwarded_proto"></a>`x_forwarded_proto`

Data type: `Boolean`

If Header x-forwared-proto should be added to hash

Default value: `false`

##### <a name="-varnish--vcl--https_redirect"></a>`https_redirect`

Data type: `Boolean`

deprecated

Default value: `false`

##### <a name="-varnish--vcl--drop_stat_cookies"></a>`drop_stat_cookies`

Data type: `Boolean`

depretaced

Default value: `true`

##### <a name="-varnish--vcl--cond_unset_cookies"></a>`cond_unset_cookies`

Data type: `Optional[String]`

If condtion to unset all coockies

Default value: `undef`

##### <a name="-varnish--vcl--unset_headers"></a>`unset_headers`

Data type: `Array[String]`

Unset the named http headers

Default value: `['Via','X-Powered-By','X-Varnish','Server','Age','X-Cache']`

##### <a name="-varnish--vcl--unset_headers_debugips"></a>`unset_headers_debugips`

Data type: `Array[Stdlib::IP::Address]`

Do not unset the named headers for the following IP's

Default value: `['172.0.0.1']`

##### <a name="-varnish--vcl--vcl_version"></a>`vcl_version`

Data type: `Varnish::Vclversion`

Which version von VCL should be used

Default value: `'4'`

## Defined types

### <a name="varnish--vcl--acl"></a>`varnish::vcl::acl`

Defines an ACL Type of Varnish. Defined ACL's must be used in VCL

#### Parameters

The following parameters are available in the `varnish::vcl::acl` defined type:

* [`hosts`](#-varnish--vcl--acl--hosts)

##### <a name="-varnish--vcl--acl--hosts"></a>`hosts`

Data type: `Array[Stdlib::IP::Address]`

Array of defined Hosts

### <a name="varnish--vcl--acl_member"></a>`varnish::vcl::acl_member`

The varnish::vcl::acl_member class.

#### Parameters

The following parameters are available in the `varnish::vcl::acl_member` defined type:

* [`varnish_fqdn`](#-varnish--vcl--acl_member--varnish_fqdn)
* [`acl`](#-varnish--vcl--acl_member--acl)
* [`host`](#-varnish--vcl--acl_member--host)

##### <a name="-varnish--vcl--acl_member--varnish_fqdn"></a>`varnish_fqdn`

Data type: `String`

Tag name of the varnish host that is collected

##### <a name="-varnish--vcl--acl_member--acl"></a>`acl`

Data type: `String`

Name of the ACL that should be created

##### <a name="-varnish--vcl--acl_member--host"></a>`host`

Data type: `Stdlib::IP::Address`

Host ip that will be inserted

### <a name="varnish--vcl--backend"></a>`varnish::vcl::backend`

Defines a Backend for VCL

#### Parameters

The following parameters are available in the `varnish::vcl::backend` defined type:

* [`host`](#-varnish--vcl--backend--host)
* [`port`](#-varnish--vcl--backend--port)
* [`probe`](#-varnish--vcl--backend--probe)
* [`connect_timeout`](#-varnish--vcl--backend--connect_timeout)
* [`first_byte_timeout`](#-varnish--vcl--backend--first_byte_timeout)
* [`between_bytes_timeout`](#-varnish--vcl--backend--between_bytes_timeout)

##### <a name="-varnish--vcl--backend--host"></a>`host`

Data type: `Stdlib::Host`

Host that will be defined as backend

##### <a name="-varnish--vcl--backend--port"></a>`port`

Data type: `Stdlib::Port`

Port of the backend host

##### <a name="-varnish--vcl--backend--probe"></a>`probe`

Data type: `Optional[String]`

Name of probe that will be used for healthcheck

Default value: `undef`

##### <a name="-varnish--vcl--backend--connect_timeout"></a>`connect_timeout`

Data type: `Optional[Variant[String[1],Integer]]`

define varnish connect connect_timeout

Default value: `undef`

##### <a name="-varnish--vcl--backend--first_byte_timeout"></a>`first_byte_timeout`

Data type: `Optional[Variant[String[1],Integer]]`

define varnish first_byte_timeout

Default value: `undef`

##### <a name="-varnish--vcl--backend--between_bytes_timeout"></a>`between_bytes_timeout`

Data type: `Optional[Variant[String[1],Integer]]`

define varnish between_bytes_timeout

Default value: `undef`

### <a name="varnish--vcl--director"></a>`varnish::vcl::director`

Defines a backend director in varnish vcl

#### Parameters

The following parameters are available in the `varnish::vcl::director` defined type:

* [`type`](#-varnish--vcl--director--type)
* [`backends`](#-varnish--vcl--director--backends)
* [`vcl_version`](#-varnish--vcl--director--vcl_version)

##### <a name="-varnish--vcl--director--type"></a>`type`

Data type: `String`

Type of varnish backend director

Default value: `'round-robin'`

##### <a name="-varnish--vcl--director--backends"></a>`backends`

Data type: `Array[String]`

Array of backends for the director, backends need to be defined as varnish::vcl:backend

Default value: `[]`

##### <a name="-varnish--vcl--director--vcl_version"></a>`vcl_version`

Data type: `Varnish::Vclversion`

Version of vcl Language

Default value: `$varnish::vcl::vcl_version`

### <a name="varnish--vcl--probe"></a>`varnish::vcl::probe`

Defined probes must be used

* **See also**
  * https://varnish-cache.org/docs/trunk/reference/vcl-probe.html

#### Parameters

The following parameters are available in the `varnish::vcl::probe` defined type:

* [`interval`](#-varnish--vcl--probe--interval)
* [`timeout`](#-varnish--vcl--probe--timeout)
* [`threshold`](#-varnish--vcl--probe--threshold)
* [`window`](#-varnish--vcl--probe--window)
* [`includedir`](#-varnish--vcl--probe--includedir)
* [`url`](#-varnish--vcl--probe--url)
* [`request`](#-varnish--vcl--probe--request)

##### <a name="-varnish--vcl--probe--interval"></a>`interval`

Data type: `String`

Paramter as defined from varnish

Default value: `'5s'`

##### <a name="-varnish--vcl--probe--timeout"></a>`timeout`

Data type: `String`

Paramter as defined from varnish

Default value: `'5s'`

##### <a name="-varnish--vcl--probe--threshold"></a>`threshold`

Data type: `String`

Paramter as defined from varnish

Default value: `'3'`

##### <a name="-varnish--vcl--probe--window"></a>`window`

Data type: `String`

Paramter as defined from varnish

Default value: `'8'`

##### <a name="-varnish--vcl--probe--includedir"></a>`includedir`

Data type: `String`

Directory where includefiles will be created

Default value: `$varnish::vcl::includedir`

##### <a name="-varnish--vcl--probe--url"></a>`url`

Data type: `Optional[String]`

Paramter as defined from varnish

Default value: `undef`

##### <a name="-varnish--vcl--probe--request"></a>`request`

Data type: `Optional[Variant[String,Array[String]]]`

Paramter as defined from varnish

Default value: `undef`

### <a name="varnish--vcl--selector"></a>`varnish::vcl::selector`

Depending on the condition, requests will be sent to the correct backend

#### Parameters

The following parameters are available in the `varnish::vcl::selector` defined type:

* [`condition`](#-varnish--vcl--selector--condition)
* [`director`](#-varnish--vcl--selector--director)
* [`rewrite`](#-varnish--vcl--selector--rewrite)
* [`newurl`](#-varnish--vcl--selector--newurl)
* [`movedto`](#-varnish--vcl--selector--movedto)
* [`order`](#-varnish--vcl--selector--order)
* [`includedir`](#-varnish--vcl--selector--includedir)
* [`vcl_version`](#-varnish--vcl--selector--vcl_version)

##### <a name="-varnish--vcl--selector--condition"></a>`condition`

Data type: `String`

Condtion under that varnish will redirect to the defined backend
Must be valid VCL if conditon

##### <a name="-varnish--vcl--selector--director"></a>`director`

Data type: `String`

Director that will be used for the requests

Default value: `$name`

##### <a name="-varnish--vcl--selector--rewrite"></a>`rewrite`

Data type: `Optional[String]`

Rewrite Header X-Host to this value

Default value: `undef`

##### <a name="-varnish--vcl--selector--newurl"></a>`newurl`

Data type: `Optional[String]`

rewrite URL to this URL

Default value: `undef`

##### <a name="-varnish--vcl--selector--movedto"></a>`movedto`

Data type: `Optional[String]`

Instead of backend, sent redirect to this Baseurl

Default value: `undef`

##### <a name="-varnish--vcl--selector--order"></a>`order`

Data type: `Variant[String, Integer]`

Order value for selector statements

Default value: `'03'`

##### <a name="-varnish--vcl--selector--includedir"></a>`includedir`

Data type: `Stdlib::Absolutepath`

Directory for include files

Default value: `$varnish::vcl::includedir`

##### <a name="-varnish--vcl--selector--vcl_version"></a>`vcl_version`

Data type: `Varnish::Vclversion`

Version of VCL Language

Default value: `$varnish::vcl::vcl_version`

## Data types

### <a name="Varnish--Controller--Agent_name"></a>`Varnish::Controller::Agent_name`

Type for supported Agent Name of Controller Agent

Alias of `Pattern[/\A(?i:([-a-z0-9]+))\z/]`

### <a name="Varnish--Vclversion"></a>`Varnish::Vclversion`

Type for supported VCL Versions

Alias of `Pattern[/\A(?i:(4))\z/]`
