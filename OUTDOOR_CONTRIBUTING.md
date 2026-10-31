# Contributing to outdoor smart-dust research

Thank you for helping make the model more transparent and reproducible. The interactive magnetic application, optical numerical research and saved-data presentation are separate layers. Please state which one your contribution concerns.

## Current scientific boundary

The showcase evidence was frozen at 2026-10-31 00:45 UTC. The nominal 108 m trajectory remains unverified under the required numerical checks; the corrected comparison ends near 53.898 m. Neither is demonstrated hardware transport. Optical research uses scalar Fresnel propagation and ideal specular facets, not a full-vector material-scattering solution. A visual improvement does not change those claims. See `docs/SCIENCE_AND_STATUS.md` and the mathematical explanations.

## Useful contributions

- Explain or improve surface-integration bounds while preserving complete domain coverage and retained parent constraints.
- Diagnose which mathematical guard blocks a patch; distinguish failure to exclude zero from proof of a physical singularity.
- Trace original local force/torque error budgets to net loads, orientation and trajectory objectives. Do not silently relax gates.
- Review baseline load-Jacobian signs and units: source output `K` stores the positive load Jacobian; conventional restoring stiffness is its negative.
- Propose explicitly justified material, scattering, absorption or thermal models, separate from the existing ideal-reflector baseline.
- Improve reproduction documentation or saved-data displays without inventing trajectories, successful transport, physical attitude control or measured sensors.

## Before a change is accepted

1. Identify exact source files, input hashes, assumptions and the intended acceptance check.
2. Preserve original data and baselines. Keep application and optical-research results separate.
3. Record units, dependency versions, resource limits, failure/null results and reproducible outputs. Compare with unchanged gates.
4. For math changes, provide a derivation and a small independently reviewable check before proposing a larger experiment.
5. For display changes, verify saved-array identity and label magnification, time compression and synthetic content.
6. Document static checks, runtime checks and unperformed checks separately. Existing browser and numerical-runtime portability limitations remain until actually resolved.

Historical capsules are evidence, not permission to revive exhausted windows. Obtain a separately reviewed bounded protocol before new simulations; no hardware, spending, public posting or deployment is implied by this guide.

## Sharing and licensing

Submit a clearly scoped proposed change with evidence and limitations. Do not include credentials, private owner links, runtime sessions or personal data. Preserve supplied third-party notices. This guide grants no new license and does not establish a blanket license for the research or media. Check ownership and license scope before public redistribution.
