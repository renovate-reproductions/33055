# minimal-reproduction-template

First, read the [Renovate minimal reproduction instructions](https://github.com/renovatebot/renovate/blob/main/docs/development/minimal-reproductions.md).

Then replace the current `h1` with the Renovate Issue/Discussion number.

## Current behavior

Renovate will get as new version `sdk: <3.6.1` when using `sdk: >=3.4.0 <3.6.0` and the latest version is `3.6.0` in `pubspec.yaml`. But Dart cannot define a range without a lower bound, so that will fail with

```
Command failed: dart pub get --no-precompile
pubspec.yaml has no lower-bound SDK constraint.
You should edit pubspec.yaml to contain an SDK constraint:

environment:
  sdk: '^3.6.0'

See https://dart.dev/go/sdk-constraint
```

## Expected behavior

The sdk version would need to be a valid range in the context of Dart, specifying a lower bound, either explicitly with >=, or using the caret syntax. 

## Link to the Renovate issue or Discussion

https://github.com/renovatebot/renovate/discussions/33055