# Magento 2 Unit Tests
To use this action, create a YAML file `.github/workflows/example.yml` in your extension folder, based upon the following contents:
```yaml
name: ExtDN Actions
on: [push]
jobs:
  unit-tests:
    name: Magento 2 Unit Tests
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v6
      - uses: extdn/github-actions-m2/magento-unit-tests/8.3@master
        env:
          MAGENTO_VERSION: '2.4.7'
          MODULE_NAME: Foo_Bar
          COMPOSER_NAME: foo/magento2-foobar
```

You can also run multiple combinations and reuse the same variables:

```yaml
name: ExtDN Actions
on: [push]
jobs:
  unit-tests:
    name: Magento 2 Unit Tests
    runs-on: ubuntu-latest
    env:
      MODULE_NAME: Foo_Bar
      COMPOSER_NAME: foo/magento2-foobar
    steps:
      - uses: actions/checkout@v6
      - uses: extdn/github-actions-m2/magento-unit-tests/8.3@master
        env:
          MAGENTO_VERSION: '2.4.7'
      - uses: extdn/github-actions-m2/magento-unit-tests/8.3@master
        env:
          MAGENTO_VERSION: '2.4.8'
      - uses: extdn/github-actions-m2/magento-unit-tests/8.5@master
        env:
          MAGENTO_VERSION: '2.4.9'
```

Make sure to modify the following values:
- `module_name` - for instance, `Foo` if your Magento 2 module is called `Foo_Bar`
- `composer_name` - for instance, `Bar` if your Magento 2 module is called `Foo_Bar`

You could also choose to switch PHP version, by changing the tag of the Docker image:

    - uses: extdn/github-actions-m2/magento-unit-tests/8.5@master
