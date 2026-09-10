# deck-ai-packs

deck packs for the deck workspace: the rules, gates and toggles that travel with
these repositories, versioned where the people who own them can review them.

Nothing here is machine state. `.deck/` — the descriptor, the recorded choices,
the gate evidence — lives on each machine and is not versioned. What lives here
is the shape a team agrees on.

```
packs/
  deck/          working on the engine
  deck-acme/     maintaining the example repository
```

Both are skeletons: `deck pack validate` reports `0 toggle(s), 0 gate(s)` for
each, which is the honest state — the shape is decided, the content is not.

Neither replaces a pack that already exists, and the distinction is the point of
this repository:

```
packs/
├── _workspaces/all/default/     what applies to every repository here
└── _repos/
    ├── deck/                    working on the engine
    └── deck-acme/               maintaining the demo workspace
```

**A pack's directory says what it applies to, and nothing else does.**
`_repos/<repository>` is one repository, wherever it is checked out.
`_workspaces/<name>/<scope>` is a workspace and a phase of work inside it, where
`<name>` may be `all` — every workspace this collection serves — and `<scope>`
may be `default` — the whole of it rather than one initiative.

Layers merge most general first, so the most specific has the last word:

```
all/default → all/<scope> → <name>/default → <name>/<scope> → _repos/<repository>
```

A name claimed by two collections is reported by `deck packs` and `deck doctor`
and never resolved: picking one would be a guess about your intent.

Point deck at it from the workspace descriptor:

```yaml
packs_root:
- deck-ai-packs/packs
```

One collection, because the product repositories carry none. Neither `deck` nor
`deck-acme` versions anything AI-specific: a pack is knowledge about a
repository, and it is reviewed where the people who own that knowledge can see
it — here — rather than inside the repository it describes.

## Reading a pack

    config/detect.yaml     when this pack is in play
    config/gates.yaml      the commands that prove a change, by rung
    config/toggles.yaml    decisions this codebase keeps re-making
    config/mount.yaml      what deck places in a repository, and where
    rules/*.md             invariants, loaded only when a matching file is read

## License

MIT.
