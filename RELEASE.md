## Release

Development and release management is done through [https://github.com/safedep/vet-gitlab-ci-component](https://github.com/safedep/vet-gitlab-ci-component) auto-sync.

To create a new release, you need to: 

1. Create new tag on the repository, for example:

```bash
git tag v1.0.0
```

2. Push the tag to the repository

```bash
git push --tag
```

The new version will be released automatically to the [GitLab Component Library](https://gitlab.com/explore/catalog/safedep/ci-components/vet).
