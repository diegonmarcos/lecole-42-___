# lecole-42-___

Project master for the 42 coursework (private). `repos.json` lists the ten lecole-42* repos (a subset of _git-repos-master/repos.json); `./clone.sh --all` clones them into `~/cloud-shared-store/git` and the committed symlinks here point at them. `./check-repos-sot.sh` checks the list against the registry.

## Hub submodule

This repo's parent hub is `_git-repos-master`, mounted as a git submodule at `0_hub/_git-repos-master` (one fixed path convention for every repo; URL https://github.com/diegonmarcos/_git-repos-master.git, pinned to the hub main). Only the upward link is a submodule; this hub keeps symlinks (not submodules) to its members, so there are no cycles. Source of truth: `repos.json` in _git-repos-master (`parent_hub` / `hub`, `_hub_submodule_doc`), guarded by `node repos-sot.js check-hubs`.
