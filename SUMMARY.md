# Table of contents

* [Introduction](README.md)
* [Authentication](authentication.md)

## Guides

* [Projects](guides/projects.md)
* [Bugs](guides/bugs.md)
* [Error Handling](guides/error-handling.md)

## Reference

* [OpenAPI Specification](reference/openapi-specification/README.md)
  * ```yaml
    props:
      models: true
    type: builtin:openapi
    dependencies:
      spec:
        ref:
          kind: openapi
          spec: tbz-dev-web-api
    ```
