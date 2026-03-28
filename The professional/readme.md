# Readme

This is a modified version of the original "The professional" Rainmeter skin. 

## Changes

- Added GPU monitor
- Modernized legacy Rainmeter syntax (removed deprecated `!Execute` bangs)
- Updated built-in measures (`SysInfo`, `WebParser`, `PowerPlugin`) to use modern native syntax
- Migrated deprecated Disk Read/Write values from `PerfMon` to modern `UsageMonitor` usage
- Added GPU vram monitor

## Notes on VRAM Monitoring

When using Rainmeter's `UsageMonitor` plugin to track VRAM, there are two important things to keep in mind:
1. **Total VRAM Must Be Hardcoded**: The plugin cannot dynamically retrieve your GPU's maximum VRAM capacity. Because of this, you must manually set the `MaxVRAM` variable in the `[Variables]` section of the `.ini` file in bytes (e.g., `17179869184` for 16GB).
2. **Preventing Double-Counted Usage and errors**: Instead of the common `Alias=VRAM` (which aggregates process-level virtual memory and can artificially inflate usage to numbers like 24GB on a 16GB card), this skin uses the `GPU Adapter Memory` category with the `Dedicated Usage` counter and `Index=0` to query the hardware adapter layer directly. The output is then passed through a `Calc` measure to cleanly strip away any string artifacts before hooking up to the graph metrics.

## Original

I can't find a listing from the original skin file, if anyone knows the original listing feel free to PR it up and I'll merge it.