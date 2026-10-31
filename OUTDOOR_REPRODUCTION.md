# Reproduction and portability

## Safe inspection

Open `../index.html` or `../presentation/Outdoor_Interactive_Replay.html` directly. The interactive replay embeds saved arrays, CSS and JavaScript. It performs display projections/unit conversion, not numerical transport. The video can be opened in a standard media player. No application server or simulation is needed to inspect these results.

## Original application

`application/original/Smart_Dust_Lab_v2_7_Fast_Exploration.ipynb` is the unchanged uploaded notebook. `application/restored/` contains 288 literal writefile assets extracted without execution, preserving relative paths and supplied licenses. The notebook additionally contains setup/config/launch/check cells; these are not executed automatically. Consult the restored README and pyproject/requirements files for the author's dependency declarations. The requested fast profile (5 m/s, 7 T/m) belongs to a hypothetical magnetic-actuation model, not the optical study. The current app defaults to octahedral geometry; older prompt wording sometimes says spherical. Treat that as a source-consistency review item.

The extraction manifest's source-local paths remain historical locators; map its `inputs/outdoor_bundle_static/` prefix to `application/restored/` here. The readable concatenation `docs/snippet_2_source.txt` preserves the explanation's line locators.

## Optical numerical source

`research/optical/detail_direct.py` and all seven modules in `research/optical/source/` preserve the selected source bytes. External imports include NumPy, SciPy and Numba. `requirements-inspection.txt` lists packages without pretending to reproduce the original pinned numerical environment. Put the source directory on PYTHONPATH only in an explicitly reviewed execution environment; imports can compile caches or create directories.

The original fleet launch path also expects generated CASE/STATIC/CHECKS/CONVERGENCE/REVIEW_ADMISSION JSON, feed and obstacle arrays, cached field tables and admission receipts. These are **not all present in this minimal source selection**. We deliberately do not borrow configurations from other historical runs, fabricate passing prerequisites, remove guards or provide a misleading turnkey long-route launcher. Saved trajectories and exact result capsules are available for evidence review instead.

## Exact qualification capsules

The three archives under `evidence/capsules/` retain original bytes and nested historical dependencies. They include mathematical implementations, exact inputs and result receipts; inspect their own manifests and reproduction notes. Their absolute workspace paths, pinned numerical runtime/tool dependencies and bounded-owner orchestration are historical and may require reconstruction on another host. Compiled runtime distributions are not included. They are not an authorization or plug-and-play recipe to rerun terminated jobs. No full capsule qualification was executed in this export.

## Video source

`presentation/render_outdoor_cube.py` reads `presentation/inputs/data.json`. It requires NumPy, Pillow, ffmpeg and the DejaVu Sans font at its explicit Linux path. Rendering prerequisites were not reinstalled here. Its script header names the historical workspace invocation; the relocated file remains otherwise unchanged. The current MP4 has already passed full decode and 720 saved-frame mapping checks. HTML data/control checks passed under a Node canvas mock; actual Chromium/browser visual QA was blocked by sandbox/runtime setup, so cross-browser playback is not claimed.

## Licensing and publication

Keep the supplied application notices. No global license is invented for all research or media. Inspect external asset licenses and dependency terms before redistributing. Do not commit .env values, private owner URLs, local runtime sessions, caches or credentials. This package is downloadable review material, not a published repository.
