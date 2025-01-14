# External contributions
 - only accept contributions to 'dev' branch OR release immediately after

# Prepare the release

## on dev branch
 - update Cargo.lock: `cargo update` (but do not break MSRV, so do it package by package and check with MSRV toolchain)
 - check compilation success
 - cargo fmt --all / cargo check / cargo clippy
 - update the changelog
 - remove the 'beta' from the version field in Cargo.toml

## Merge process
 - create a PR dev -> master
 - merge

## Post-merge (tag creation and push MUST be done one after the other!! DON'T add a commit in the meantime)

 - git pull the changes in master
 - create a new SIGNED tag vX.Y.Z on master: `git tag -s v8.9.5` (tag message should be equal to tag number, eg: v8.9.5)
 - verify the signed tag: `git tag -v v8.9.5`
 - git push origin vX.Y.Z

 - Bump Cargo.toml to next version on dev, suffixed by 'beta'

# When the tag gets pushed, the 'release' github action will automatically add the new tag to GitHub's 'Releases'

# Check the release

 - Check CI status
 - Check Releases status
 - Edit release description if necessary
