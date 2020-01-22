<p align="center"><a href="https://www.oxyshop.cz" target="_blank">
    <img src="https://symfony.com/logos/symfony_black_02.svg">
</a></p>

[Nextgen][1] eCommerce Platform on Symfony.

# Installation

# Documentation

# Contributing

# Issues

# Monorepo

All the Nextgen codebase in one place.

## Repositories

### Nextgen
- [Nextgen Standard](#todo)
- [Documentation](#todo)

### Components
- [Core](#todo)
- [Channel](#todo)
- [Product](#todo)
- ...

### Bundles
- [CommonBundle](#todo)

### DevOps
- [Standard](#todo)

### Packages (front-end)
@todo

### Plugins
@todo

### Themes
@todo

## About this monorepo

### [Split.sh](https://github.com/splitsh/lite)
Using for **splitting monorepo** to the stand-alone repositories.

:warning: At the moment we're using bash script [`releaser`](./releaser) which using `split.sh` internally.

```bash
$ ./release
```

### [symplify/monorepo-builder](https://github.com/Symplify/Symplify)
Mainly used for validation and composer.json manipulation of repositories.

:warning: Never use **monorepo-builder** to split or release.

```bash
# Validates synchronized versions in "composer.json" in all found packages
$ vendor/bin/monorepo-builder validate

# Merge "composer.json" from all found packages to root one
$ vendor/bin/monorepo-builder merge

# Propagate versions from root "composer.json" to all packages, the opposite of "merge" command
$ vendor/bin/monorepo-builder propagate

# Updates branch alias in "composer.json" all found packages
$ vendor/bin/monorepo-builder package-alias
```

## Todos
- Test split.sh
- Is possible to split to the multiple groups and repositories? => Yes
- Add one extra namespace the `Oxyshop` before `Nextgen`.
- Should the plugins be stored within this monorepo?
    - What about packages (front-end components)?
    - What about templates (themes)?
    - And DevOps?
    - Where projects should be stored?
- Standard will be moved to the DevOps group
- `Nextgen/Nextgen-Standard` could be in monorepo too. ATM it is in separated repo.
- Docs is in the separated repository, see the [docs](https://docs.nextgen.oxydev.cz).

### Workflow
- Releasing new versions
- PR/MR
- Testing

### Testing
See the blog post [How to test monorepo in 3 layers](https://www.tomasvotruba.com/blog/2018/11/22/how-to-test-monorepo-in-3-layers/).
- Testing Monorepo (like Symfony, Sylius)
- Testing Standalone Packages in Monorepo (like Symfony, Sylius)
- After Split Testing

## Releasing new versions
1. Do some checks (clean repo, ...)
1. Tag release
1. Push to the `nextgen/nextgen`
1. Split the monorepo via `split.sh`
    - Check of latest commits (SHA1) and tags if exists
    - Push changes
    - Wait for hooks
    - Check if all tags are available on packagist
    - Check again (all the commits, all the tags, ...)
    - Update dev versions and push them (`Kernel.php`)
1. Release (Create GitHub release, publish blog post, tweet release, send notifications)

[1]: https://test-test.digital24.oxydev.cz/
