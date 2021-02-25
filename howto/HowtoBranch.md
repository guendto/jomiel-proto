# HowtoBranch.md

## How the patch generation branches were created

Applicable to v1beta1 and later.

```shell
git checkout -b <branch> master
```

The last three commits are `reserved` for the patches intended for use
with `jomiel-messages` package. Therefore, commit anything else that
needs to be committed, before the ones that modify the .proto files.

```shell
git cherry-pick <sha1>
```

Once that's done, either:

```shell
git cherry-pick <commit>  # from another branch if applicable
```

Or if that's not possible:

- Refactor the .proto files
- Commit the changes (commit per .proto file)

The last three commits should now refactor only the .proto files, and
they can be exported as .patch files with

```shell
git format-patch -3
```
