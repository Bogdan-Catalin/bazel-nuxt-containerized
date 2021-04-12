# bazel-nuxt

This project is forked from https://github.com/albttx/bazel-nuxt and changed to use a newer version of [rules_nodejs](https://github.com/bazelbuild/rules_nodejs) - 3.3.0 and vue code has been moved in app/ and the output is also containerized with [bazel docker rules](https://github.com/bazelbuild/rules_docker). This is used to test why bazel doesn't output build directories when building from the root of the project, but does output when building from app/ with a WORKSPACE file in it.


I use [dive](https://github.com/wagoodman/dive) and [bazel docker rules](https://github.com/bazelbuild/rules_docker) because it's closer to my use case.
## Getting output directories 

```bash
cd app/
bazel run container
dive bazel:container
```

## Not getting output directories
```bash
bazel run app:container
dive bazel/app:container
```
