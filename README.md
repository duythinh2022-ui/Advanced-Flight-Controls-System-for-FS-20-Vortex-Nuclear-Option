# FS-20 Vortex FCS (Nuclear Option)

A flight control system mod for the stock **FS-20 Vortex** in Nuclear Option, with **F-35B-style STOVL control laws**. BepInEx plugin `Vortex_FS20.FCS`, version **0.5.10**.

- **CTOL:** carefree, full-authority handling across the envelope. Trailing-edge surfaces are stall-staggered, the elevons are modelled as flaps acting on the wing ahead of them, and there's delta-wing vortex lift. It compensates for asymmetric loads and resists departure on a damaged airframe.
- **STOVL** (hold Flight Assist to convert, at 460 km/h or below):
  - **Throttle:** works as a speed lever with a zero-ground-speed detent.
  - **Hover:** the stick commands translational rate; a released stick holds the spot and the height.
  - **Limits:** authority-based, so they follow mass, fuel, stores and thrust.
  - **At speed** (lift fan still on): blends into CTOL-like control.
  - **Hardware:** lift-fan vane box (thrust vectored 10° forward to 42° aft), with a 3D model.
  - **Release guard:** blocks a drop that would leave weight on one side that the hover can't hold.
  - **Pirouette:** optional pedal pirouette on a hotkey.
  - **Stability Assist off:** freestyle flying.

Per-version changes: [CHANGELOG.md](CHANGELOG.md).

## Install (players)

Download the release zip and put `Vortex_FS20_FCS.dll` and `meta.json` in `BepInEx\plugins\Vortex_FS20.FCS\`. Settings are in `BepInEx\config\Vortex_FS20.FCS.cfg`. The advanced settings (`Vortex_FS20.FCS.Dev.cfg`) need the optional DevUnlock DLL (source in `DevUnlock/`).

## Layout

- `Vortex_FS20.FCS/`: the plugin source.
  - The STOVL laws are in `Stovl.cs`.
  - The game side is in `SwivelLink.cs` and `StovlHooks.cs`.
  - Settings are in `Plugin.cs`.
- `native/`: the allocator's native core. The Rust source is in `fcs_core/`, and `prebuilt/Vortex_FcsCore.dll` is embedded into the plugin at build time.
- `DevUnlock/`: the optional DLL that unlocks the advanced settings.

## Build

```
bash build.sh Vortex_FS20.FCS Vortex_FS20_FCS.dll
```

- **Needs:** the .NET 8 SDK (its Roslyn `csc`), plus the game's `NuclearOption_Data/Managed` and `BepInEx/core` folders.
- **Paths:** set `M=` and `B=` at the top of `build.sh` to where those folders are on your machine.
- **Output name:** the assembly name comes from the output file name, so keep it `Vortex_FS20_FCS.dll`.
- **Reproducible:** the build is deterministic.

## License

[PolyForm Noncommercial 1.0.0](LICENSE): free to use, modify and share for noncommercial purposes. Commercial use needs the author's permission.
