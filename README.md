# dUpdates

> **Original project and credit:** [Prusias-kol/pUpdates](https://github.com/Prusias-kol/pUpdates) by Prusias-kol. This is a separate experimental fork maintained at [donCannoli-burns/dUpdates](https://github.com/donCannoli-burns/dUpdates).
>
> **EXPERIMENTAL — USE AT YOUR OWN RISK.** This fork is not guaranteed to be stable or safe. Review settings and scripts before running them, especially commands that spend turns, change inventory, use the mall, PvP, or ascend. The upstream author is not responsible for modifications in this fork.

KoLmafia script-update library derived from pUpdates. **The installed command and file name remain `pUpdates` / `pUpdates.ash`**, and compatibility preference names retain the historic `prusias_pUpdates_` prefix.

## Install, update, and remove

Run these commands in the **KoLmafia gCLI** (not your operating system's Git shell).

**Install**
```
git checkout https://github.com/donCannoli-burns/dUpdates main
```

**Update**
```
git update donCannoli-burns-dUpdates-main
```

**Remove this fork**
```
git delete donCannoli-burns-dUpdates-main
```

If you previously installed the original upstream project, use `git list` to confirm its installed project ID before optionally deleting it with `git delete Prusias-kol-pUpdates-main`. Avoid keeping upstream and fork versions installed simultaneously when they supply the same script filenames.

## Dependencies

None required for the `dUpdates` library itself. Its former `dependencies.txt` was removed because referencing `donCannoli-burns/dUpdates` from within `dUpdates` would create a self-dependency. Other scripts, such as `dLooper`, should declare `https://github.com/donCannoli-burns/dUpdates main` in their own dependency files.

## How to use

Run `pUpdates help` in KoLmafia to see the existing commands. Initialize tracking for a script with `pUpdates init <scriptname>`, add a note with `pUpdates add <scriptname> <update text>`, and display unseen changes with `pUpdates check <scriptname>`. Use a consistent no-spaces script name.

## Update data layout

The preferred update-data folder is now **`data/dUpdates/`**, not `data/pUpdates/`. The historic `prusias_pUpdates_` file prefix is deliberately preserved for compatibility.

For a script named `example`, the data file is:

```
kolmafia/data/dUpdates/prusias_pUpdates_example.txt
```

If another repository includes such a file, a typical KoLmafia-compatible Git layout is:

```
manifest.json
kolmafia/dependencies.txt
kolmafia/scripts/<your scripts>
kolmafia/data/dUpdates/prusias_pUpdates_<scriptname>.txt
```

Use `manifest.json` containing:

```json
{
  "root_directory": "kolmafia"
}
```

The updated `pUpdates.ash` implementation reads from `data/dUpdates/` first and falls back to `data/pUpdates/` for existing installations. New update entries are written to the new directory. Existing saved version preferences remain unchanged.

If installing this library as a dependency in another project's `dependencies.txt`, use the fork URL:

```
https://github.com/donCannoli-burns/dUpdates main
```

## Displaying updates

Use `pUpdates check <scriptname>` from a script or gCLI to print new entries. The upstream documentation sometimes referred to `ploop check`; that is a different wrapper command, not the general update-library command.
