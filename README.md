# lecole-42-___

Project master for the 42 coursework (private). `repos.json` lists the ten lecole-42* repos (a subset of _git-repos-master/repos.json); `./clone.sh --all` clones them into `~/cloud-shared-store/git` and the committed symlinks here point at them. `./check-repos-sot.sh` checks the list against the registry.

## Clone depth

`clone.sh` clones with `--depth 1 --shallow-submodules` by default: only the latest commit, so a clone is fast and takes little disk. Each repo has exactly ONE clone (in `$CLOUD_GIT_BASE`); the links point at it, so never keep a second full copy next to it.

```
./clone.sh <name>...                 # shallow, depth 1 (default)
./clone.sh --full <name>...          # full history (same as CLONE_DEPTH=0)
CLONE_DEPTH=50 ./clone.sh <name>...  # a deeper shallow clone
git -C <clone> fetch --unshallow     # later, turn an existing clone into full history
git -C <clone> submodule update --init --depth 1   # submodules stay shallow too
```

## Hub submodule

This repo's parent hub is `_git-repos-master`, mounted as a git submodule at `0_hub/_git-repos-master` (one fixed path convention for every repo; URL https://github.com/diegonmarcos/_git-repos-master.git, pinned to the hub main). Only the upward link is a submodule; this hub keeps symlinks (not submodules) to its members, so there are no cycles. Source of truth: `repos.json` in _git-repos-master (`parent_hub` / `hub`, `_hub_submodule_doc`), guarded by `node repos-sot.js check-hubs`.
