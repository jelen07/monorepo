# Nextgen/Nextgen

## Todos
- Test split.sh
- Is possible to split to the multiple groups and repositories?
- Add one extra namespace the `Oxyshop` before `Nextgen`.
- Should the plugins be stored within this monorepo?
    - What about packages (front-end components)?
    - Where projects should be stored?
    - What about templates (themes)?
    - And DevOps?
    - Standard will be moved to the DevOps group.
- `Nextgen/Nextgen-Standard` could be ib monorepo too. ATM it is separated.

### Workflow
- Releasing new versions
- PR/MR
- Testing

### Testing
See the blog post [How to test monorepo in 3 layers](https://www.tomasvotruba.com/blog/2018/11/22/how-to-test-monorepo-in-3-layers/).
- Testing Monorepo (like Symfony, Sylius)
- Testing Standalone Packages in Monorepo (like Symfony, Sylius)
- After Split Testing

## Docs
Will be in the separated repository, see the [docs](https://docs.nextgen.oxydev.cz).

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
