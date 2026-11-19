# FS-20 Vortex FCS (Nuclear Option)

A flight control system mod for the stock **FS-20 Vortex** in Nuclear Option, with **F-35B-style STOVL control laws** "UCL or Unified Control Laws".

- **CTOL:** carefree, full-authority handling across the envelope. It compensates for asymmetric loads and resists departure on a damaged airframe.
- **STOVL** (hold Flight Assist to convert, at 460 km/h or below):
  - **Throttle:** works as a speed lever with a zero-ground-speed detent.
  - **Hover:** the stick commands translational rate; a released stick holds the spot and the height.
  - **Limits:** authority-based, so they follow mass, fuel, stores and thrust.
  - **At speed** (lift fan still on): blends into CTOL-like control.
  - **Hardware:** lift-fan vane box (thrust vectored 10° forward to 42° aft), with a 3D model.
  - **Release guard:** blocks a drop that would leave weight on one side that the hover can't hold.
  - **Pirouette:** optional pedal pirouette on a hotkey.
  - **Stability Assist off:** freestyle flying.

## License

[PolyForm Noncommercial 1.0.0](LICENSE)
