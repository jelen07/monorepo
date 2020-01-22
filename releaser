#!/bin/bash
#
# This script automates the creation and updating of a subtree split
# in a second repository.
#
set -eu
IFS=$'\n\t'

command -v splitsh-lite >/dev/null 2>&1 || { echo "$0 requires splitsh-lite but it's not installed.  Aborting." >&2; exit 1; }

# Adjust for your repositories.
#source_repository=git@github.com:path/to-full-project-repo.git
source_repository=git@github.com:jelen07/monorepo.git
source_branch=master
source_dir=src/Nextgen/Component/Core

destination_repository=git@github.com:jelen07/nextgen-core.git
destination_branch=master

# The rest shouldn't need changing.
temp_repo=$(mktemp -d)
temp_branch=test #$(cat /dev/urandom | head -n 1) # tr -dc 'a-zA-Z0-9' |

# Checkout the old repository, make it safe and checkout a temp branch
git clone ${source_repository} ${temp_repo}
cd ${temp_repo}
git checkout ${source_branch}
git remote remove origin
git checkout -b ${temp_branch}

# Create the split, check it out and then push the temp branch up
sha1=$(splitsh-lite --prefix=${source_dir} --quiet)
git reset --hard ${sha1}
git remote add remote ${destination_repository}
git push -u remote ${temp_branch}:${destination_branch} # -f

# Cleanup
cd /tmp
rm -rf ${temp_repo}

echo "Done."
