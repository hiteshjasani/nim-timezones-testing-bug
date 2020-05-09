# nim-timezones-testing-bug

This started with figuring out why I coudn't run `nimble test -y` in a docker image on a project that was using the timezones package.  After more investigation, the problem is actually in `nimble install -y` and `nimble test -y` having slightly different behavior with packages that have binaries.  The problem is not with timezones, but I don't feel like renaming the repo, so the name is what it is.

There is now a workaround.  Do a nimble install before running tests.

```sh
bash -c "nimble install -y; nimble test"
```
* See full workaround in the workflow file: [testing.yml](.github/workflows/testing.yml)
* See the nimble issue: [nimlang/nimble#801](https://github.com/nim-lang/nimble/issues/801)
