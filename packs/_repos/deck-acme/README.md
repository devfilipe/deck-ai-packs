# deck-acme

A [deck](https://github.com/devfilipe/deck) pack for the
[`deck-acme`](https://github.com/devfilipe/deck-acme) repository.

It is empty, and it is not the Acme demo pack. That one is
[`deck-acme/packs/_workspaces/all/default`](https://github.com/devfilipe/deck-acme/tree/main/packs/_workspaces/all/default),
which exists to prove deck has never heard of Acme and stays inside the
repository it demonstrates — it *is* the demonstration. This pack is for
knowledge about *maintaining* deck-acme, which is a different thing.

`rules/`, `skills/` and `agents/` are walked and copied into the working
directory when this pack is mounted — measured to be where Claude Code finds
them at project level. None of the three is here yet, and none is scaffolded
empty on purpose: a placeholder would be placed for real.

```
config/detect.yaml     how deck recognises this workspace, and what it needs
config/toggles.yaml    the decisions this domain keeps re-making
config/gates.yaml      the verification ladder, and the commands behind it
config/mount.yaml      what gets placed in a repository, and how
config/profiles.yaml   named postures
rules/                 `paths:`-scoped rules, copied in on mount
skills/                procedures, copied in on mount
agents/                subagent briefs, copied in on mount
templates/workspace/   a filled-in descriptor for this shape of workspace
```

## Use it

```bash
export DECK_PACKS=$PWD          # or list it under `packs:` in the descriptor
deck doctor
deck toggle list
```

## Keep it honest

```bash
deck pack validate .            # structure, catalog, and the plugin manifest
```

Every entry should say why it exists and what each value costs. A catalog people
cannot read is a catalog people start ignoring.
