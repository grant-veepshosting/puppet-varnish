# Changelog

All notable changes to this project will be documented in this file.
Each new release typically also includes the latest modulesync defaults.
These should not affect the functionality of the module.

## [v5.1.0](https://github.com/voxpupuli/puppet-varnish/tree/v5.1.0) (2023-12-04)

[Full Changelog](https://github.com/voxpupuli/puppet-varnish/compare/v5.0.0...v5.1.0)

**Implemented enhancements:**

- Add Support for Sockets in Varnish Proxy Listening [\#42](https://github.com/voxpupuli/puppet-varnish/pull/42) ([voxel01](https://github.com/voxel01))
- Added max\_connections option to a backend [\#41](https://github.com/voxpupuli/puppet-varnish/pull/41) ([wimsymons](https://github.com/wimsymons))
- add expected\_response parameter for probes [\#33](https://github.com/voxpupuli/puppet-varnish/pull/33) ([jhunt-steds](https://github.com/jhunt-steds))
- Fix varnish ncsa support [\#27](https://github.com/voxpupuli/puppet-varnish/pull/27) ([voxel01](https://github.com/voxel01))

**Merged pull requests:**

- Replace legacy stdlib::merge\(\) with native puppet code [\#45](https://github.com/voxpupuli/puppet-varnish/pull/45) ([bastelfreak](https://github.com/bastelfreak))
- Remove legacy top-scope syntax [\#40](https://github.com/voxpupuli/puppet-varnish/pull/40) ([smortex](https://github.com/smortex))

## [v5.0.0](https://github.com/voxpupuli/puppet-varnish/tree/v5.0.0) (2023-11-08)

[Full Changelog](https://github.com/voxpupuli/puppet-varnish/compare/v4.0.0...v5.0.0)

**Breaking changes:**

- 🐛 Fix firewall usage to match the new module, switch to puppetlabs/firewall 7 [\#36](https://github.com/voxpupuli/puppet-varnish/pull/36) ([JGodin-C2C](https://github.com/JGodin-C2C))
- Drop debian 9 support [\#26](https://github.com/voxpupuli/puppet-varnish/pull/26) ([voxel01](https://github.com/voxel01))

**Implemented enhancements:**

- Add Puppet 8 support [\#30](https://github.com/voxpupuli/puppet-varnish/pull/30) ([bastelfreak](https://github.com/bastelfreak))
- puppetlabs/stdlib: Allow 9.x [\#29](https://github.com/voxpupuli/puppet-varnish/pull/29) ([bastelfreak](https://github.com/bastelfreak))
- Add varnish-plus Backend parameters to use with ssl [\#28](https://github.com/voxpupuli/puppet-varnish/pull/28) ([voxel01](https://github.com/voxel01))
- Add acceptance tests [\#24](https://github.com/voxpupuli/puppet-varnish/pull/24) ([voxel01](https://github.com/voxel01))

**Fixed bugs:**

- Fix CentOS8 - jail user/ enable service [\#25](https://github.com/voxpupuli/puppet-varnish/pull/25) ([voxel01](https://github.com/voxel01))

## [v4.0.0](https://github.com/voxpupuli/puppet-varnish/tree/v4.0.0) (2023-05-13)

[Full Changelog](https://github.com/voxpupuli/puppet-varnish/compare/v3.0.0...v4.0.0)

**Breaking changes:**

- Drop Puppet 6 support [\#20](https://github.com/voxpupuli/puppet-varnish/pull/20) ([bastelfreak](https://github.com/bastelfreak))

**Implemented enhancements:**

- Define ressource type to validate instead of validate\_re [\#23](https://github.com/voxpupuli/puppet-varnish/pull/23) ([voxel01](https://github.com/voxel01))
- Add support for hitch [\#15](https://github.com/voxpupuli/puppet-varnish/pull/15) ([voxel01](https://github.com/voxel01))
- Add support of custom MSE config [\#14](https://github.com/voxpupuli/puppet-varnish/pull/14) ([voxel01](https://github.com/voxel01))
- add support for Varnish Controller Agent [\#13](https://github.com/voxpupuli/puppet-varnish/pull/13) ([voxel01](https://github.com/voxel01))

**Fixed bugs:**

- Fix VCL syntax [\#19](https://github.com/voxpupuli/puppet-varnish/pull/19) ([zipkid](https://github.com/zipkid))
- Fix datatype for vcl::backend timeouts [\#17](https://github.com/voxpupuli/puppet-varnish/pull/17) ([voxel01](https://github.com/voxel01))
- Fix Headline of README.md [\#16](https://github.com/voxpupuli/puppet-varnish/pull/16) ([voxel01](https://github.com/voxel01))

## [v3.0.0](https://github.com/voxpupuli/puppet-varnish/tree/v3.0.0) (2023-03-05)

[Full Changelog](https://github.com/voxpupuli/puppet-varnish/compare/1.0.0...v3.0.0)

   The Module is based on https://forge.puppet.com/modules/maxchk/varnish/readme. Compared to the last 1.0.0 in that namespace, we did:
  - Add support for new OS
  - Drop support for outdated OS
  - Move VCL Subclasses (acl, acl_member, backend, director, probe, selector)
  - Add support for varnish 6
  - Addsupport for varnish-plus / Varnish Enterprise

**Merged pull requests:**

- Fix up puppet-strings and generate REFERENCE.md [\#12](https://github.com/voxpupuli/puppet-varnish/pull/12) ([alexjfisher](https://github.com/alexjfisher))
- Remove old Modulefile [\#11](https://github.com/voxpupuli/puppet-varnish/pull/11) ([voxel01](https://github.com/voxel01))
- Update README.md [\#10](https://github.com/voxpupuli/puppet-varnish/pull/10) ([voxel01](https://github.com/voxel01))
- puppet-lint: Validate puppet-strings & datatypes [\#9](https://github.com/voxpupuli/puppet-varnish/pull/9) ([bastelfreak](https://github.com/bastelfreak))
- .fixtures.yml: Migrate from forge releases to git [\#8](https://github.com/voxpupuli/puppet-varnish/pull/8) ([bastelfreak](https://github.com/bastelfreak))
- fix typo in documentation, enhance README.md [\#4](https://github.com/voxpupuli/puppet-varnish/pull/4) ([voxel01](https://github.com/voxel01))
- Update module author after migration to Vox Pupuli [\#2](https://github.com/voxpupuli/puppet-varnish/pull/2) ([voxel01](https://github.com/voxel01))
- Update metadata to Vox Pupuli [\#1](https://github.com/voxpupuli/puppet-varnish/pull/1) ([voxel01](https://github.com/voxel01))

## [1.0.0](https://github.com/voxpupuli/puppet-varnish/tree/1.0.0) (2016-07-27)

[Full Changelog](https://github.com/voxpupuli/puppet-varnish/compare/d55e143663f24b4f5efd8a9628a3d0173264609b...1.0.0)



\* *This Changelog was automatically generated by [github_changelog_generator](https://github.com/github-changelog-generator/github-changelog-generator)*
