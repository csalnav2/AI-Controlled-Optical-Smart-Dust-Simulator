# Outdoor smart dust: offline scientific replay

Open **Outdoor_Interactive_Replay.html** directly in a modern browser. It contains its data, styles, and JavaScript; no server, network, account, or build step is needed. For a GitHub repository, include this HTML, this Markdown file, and the original `inputs/data.json` for provenance. No repository has been published by this work.

## What the controls do

- Select **nominal** or **corrected n12**. They are separate saved records, never spliced.
- Use **Play/Pause** or the saved-sample slider. One record plays in about 12 presentation seconds, not real time. Animation reveals saved samples without scientific interpolation or a new solver.
- Select a particle to inspect its recorded donor/receiver powers. The six-particle tilt plot and 3D views always include all six particles.

The large **left** panel magnifies the three axes independently, making small transverse and relative-height variations readable. The **right** panel uses equal physical axis scale in a 150 m cube. Paths almost overlap there because travel is predominantly along x, the group is only about 1.5 m wide, and relative height variations are micrometre-scale. There is no 3 m follow panel. Marker radii are symbolic.

## Evidence and limitations

Scientific evidence is frozen at **2026-10-31 00:45 UTC**. Presentation/layout changes after that cutoff do not add scientific results.

- **Nominal:** saved record reaches 108 m but failed spatial verification. No certified arrival.
- **Corrected n12:** saved partial run ends at 554 s, x ≈ 53.898 m. The n8/n12 tilt agreement check failed. The source file also contains a corrected n8 record; this replay deliberately exposes only nominal and corrected n12.
- Relative z is a simulation coordinate, not known absolute altitude. The 150 m cube and 108 m ring are reference geometry, not validated flight volume or physical trap boundaries.
- Model: scalar Fresnel propagation and ideal specular facet momentum transfer, **not** a full-vector Maxwell scattering calculation. Material-dependent absorption/scattering/heating, atmosphere and shared-SLM validation are unresolved.
- No measured flight, hardware demonstration, or biological benefit is claimed. Browser animation speed is not measured physical performance.

## Data schema and actual computations

The embedded JSON preserves all saved samples for the two displayed records from `inputs/data.json`. Each `frames[sample][particle]` vector has nine columns:

| Index | Column | Unit |
|---:|---|---|
| 0–2 | x_m, y_m, z_m | m |
| 3–5 | vx_m_s, vy_m_s, vz_m_s | m/s |
| 6 | donor_W | W |
| 7 | receiver_W | W |
| 8 | tilt_rad | rad |

The only unit conversions displayed are `relative_z_um = z_m × 10^6` and `tilt_deg = tilt_rad × 180 / π`. The six tilt curves can nearly overlap. The power panel displays saved allocated useful post-aperture donor/receiver channel power. It does not infer particle-intercepted power, raw source or electrical input, force, stiffness, or error bounds. In the source, `handoff_completion_reserve/moving_reserve_0.01/fleet.py` lines 1–2 state that only useful post-aperture watts enter the inherited facet force model; `core.py` in the same directory scales per-unit loads with `p[j]` at line 36 and saves `p` in trace columns 15–16 at line 85. The trace extractor maps those to donor_W/receiver_W. These paths identify upstream source and are not promised to be included in this minimal replay. Line segments join observed samples for display; future samples are not shown before their saved time.

## Explanatory mathematics (not new computed outputs)

- Surface traction integrates to force: **F = ∫S t dA**. Here **t** denotes force per area, not time.
- Torque about a chosen centre: **τ = ∫S (r − rc) × t dA**.
- Local stiffness is a negative force Jacobian near equilibrium: **Kij = −∂Fi/∂rj**.

The replay does **not** evaluate these integrals or derivatives. It does not establish torque convergence, stable trapping, capture, or transport merely by rendering a path.

## Editing

The HTML has three editable sections: CSS in `<style>`, immutable saved data in `<script id="saved-data" type="application/json">`, and canvas/controller code in the final `<script>`. `drawViews()` owns camera projections; `chart()` plots the saved channels; `render()` applies unit conversions. Keep all physical coordinate changes out of camera/layout functions. Preserve captions distinguishing independently magnified axes from the equal-scale reference view.

To verify data identity, compare each displayed record's `times` and `frames` arrays with the original JSON; do not compare entire JSON bytes because embedding omits the unused corrected n8 record. Original input SHA-256: `25dcc64a8b6cd50dbb9597666ee77dc5c8dcf4d3c4426dc62fe2ce9d15af5b00`.

This is the scientific replay, not the user's separate cinematic project. Cinematic code should be labeled separately and must not be presented as validated physics.
