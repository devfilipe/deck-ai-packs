# deck

A [deck](https://github.com/devfilipe/deck) pack for the
[`deck`](https://github.com/devfilipe/deck) repository: knowledge about working on
the engine that does not belong inside the engine.

It is empty, and what would go in it is narrow: something true of the `deck`
repository and of no other repository this collection serves.

deck's development knowledge — the design line, the writing standard, how we
commit, how we open issues, how we deliver, and the self-hosting rule — is one
layer up, in [`_workspaces/all/default`](../../_workspaces/all/default). It
applies to every repository here, not only to the engine.

It used to live inside the deck repository, in `packs/_workspace`. It moved for
the reason this collection exists: a product repository does not version
AI-specific content. The gate ladder that verifies deck comes from the same
layer, so a clone of deck alone is not verifiable on its own any more — it needs
this collection beside it, which is what
[`deck-manifest`](https://github.com/devfilipe/deck-manifest) assembles.

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
