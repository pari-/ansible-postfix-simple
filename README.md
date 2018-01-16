# postfix-simple

[![Build Status](https://travis-ci.org/pari-/ansible-postfix-simple.svg?branch=master)](https://travis-ci.org/pari-/ansible-postfix-simple)

An Ansible role which installs and configures postfix for simple eMail sending through SMTP

<!-- toc -->

- [Requirements](#requirements)
- [Example](#example)
- [Defaults](#defaults)
- [Dependencies](#dependencies)
- [License](#license)
- [Author Information](#author-information)

<!-- tocstop -->

## Requirements

Currently this role is developed for and tested on Debian GNU/Linux (release: stretch). It is assumed to work on other Debian distributions as well.

Ansible version compatibility:

- __2.4.2.0__ (current version in use for development of this role) 
- 2.3.3.0
- 2.2.3.0

## Example

```yaml
---

- hosts: "all"
  vars:
    postfix_simple_password: "yourVerySecretPassword"
    postfix_simple_user: "yourUser"
    postfix_simple_config:
      relayhost: "smtp.server.address:port"
  roles:
    - role: "ansible-postfix-simple"
      tags:
        - "postfix-simple"
```

## Defaults

Available variables are listed below, along with default values (see defaults/main.yml). They're generally prefixed with `postfix_simple` (which I deliberately leave out here for better formatting).

variable | default | notes
-------- | ------- | -----
`cache_valid_time` | `3600` | `Update the apt cache if its older than the set value (in seconds)`
`config_defaults` | `{}` | `A dictionary containing postfix configuration default values`
`config_files['maincf']` | `/etc/postfix/main.cf` | `Absolute path to postfix's main.cf`
`config_files['saslpasswd']` | `/etc/postfix/sasl/passwd` | `Absolute path to postfix's SASL password file`
`default_release` | `{{ ansible_distribution_release\|lower }}` | `The default release to install packages from`
`package_list` | `['libsasl2-modules','postfix']` | `The list of packages to be installed`
`password` | `` | `The password belonging to the user to login with`
`pre_default_release` | `{{ postfix_simple_default_release }}` | `The default release to install packages (pre_package_list) from`
`pre_package_list` | `['apt-transport-https','ca-certificates']` | `The list of prerequisite packages to be installed`
`repo_list` | `[]` | `Source string for the repositories`
`service_name` | `postfix` | `Name of the  service`
`supported_distro_list` | `['jessie', 'stretch']` | `A list of distribution releases this role supports`
`update_cache` | `yes` | `Run the equivalent of apt-get update before the operation`
`user` | `` | `The eMaul user to log in with`

## Dependencies

None

## License

MIT

## Author Information

* Patrick Ringl
