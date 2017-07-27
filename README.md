# Java

Manages Java for Linux distributions.

## Requirements

None.

## Role Variables

- **java_version**: Java version to install
- **java_subversion**: Java subversion to install. Only relevant for `oracle` installs.
- **java_build**: Optional Java build version to install. Only relevant for `oracle` installs.
- **java_distro**: Java distribution to install with valid values of `openjdk` (default) and `oracle`.
- **java_platform**: Java platform, i.e. `jre` (i.e. the Java Runtime Environment, the default) or `java` (i.e. the Java Development Kit).
- **java_install_jce**: Flag to install Java Cryptography Extensions (JCE). Defaults to `false`.
- **java_set_default**: Flag used to setup the Java install as the default. Defaults to `true`.
- **java_set_home**: Flag used to setup JAVA_HOME. Defaults to `true`.

## Dependencies

None.

## Example Playbook

```
- hosts: localhost
  roles:
     - java
```

## License

[MIT](LICENSE)

## Author Information

- [Stuart Wong](https://cgswong.github.io) | [E-Mail](mailto:cgs.wong@gmail.com) | [Twitter](https://twitter.com/cgswong)
