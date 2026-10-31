# Outdoor particle trajectory research video

Chris Salnave

The scientific evidence snapshot remains 00:45 UTC on 31 October 2026. This refreshed explanation includes a separately dated later component test and does not replace or extend the frozen trajectory evidence.

### What the updated layout shows

The approved layout places an enlarged magnified three-dimensional view on the left and an enlarged true-scale 150-metre cube on the right. Lower panels show saved tilt and donor and receiver traces. The revised video is silent 1080p at 30 frames per second, with 720 frames over 24 seconds. This presentation change does not alter the frozen scientific result.

The outdoor video replays six saved particle paths using their actual coordinates. The nominal and corrected cases appear in separate chapters so that they remain distinct calculations. The trajectories are mostly straight and close together. I have not added curves or extra separation to make the fleet look more active than the saved data supports.

The right-hand 150-metre cube preserves the physical reference scale. The enlarged left-hand diagnostic view magnifies small variations with independently scaled axes. Its shape is deliberately diagnostic, not the physical aspect ratio of the trajectory. Viewers should use the true-scale cube to judge geometry and the labeled magnified view to inspect differences.

The lower tilt plot follows all six particles against saved time, converting the saved tilt_rad values from radians to degrees for display. The companion plot shows particle 1’s saved donor_W and receiver_W traces against time. These are allocated useful post-aperture donor and receiver channel powers, not the power intercepted by the particle or the source’s electrical input. Both panels expose quantities already in the saved record; they do not add a new simulation or a new measurement.

The mathematical labels identify force and torque surface integrals and a force-gradient stiffness description. The replay does not recompute them. The research source already contains a baseline local load-Jacobian and eigenvalue calculation, described below; that implementation is distinct from new optimization or certified stiffness. Displaying these labels does not turn the scalar-field and ideal-facet model into a full Maxwell scattering calculation.

The 108-metre target ring is a reference marker. It is not a physical barrier, a modeled obstacle or proof that the target was reached. A visible trajectory and a target in the same scene do not establish successful transport between them.

### Where the corrected comparison stops

The corrected comparison stops at 554 seconds, at approximately 53.898 metres, following a tilt disagreement at 553.428 seconds. The compared results matched through 515 seconds. Keeping the stop visible matters because the later portion cannot be presented as an agreed, verified continuation. The nominal 108-metre result remains uncertified.

This is a limit on what I can claim from the current calculation. It does not by itself show that the physical idea is impossible. It means that the available numerical evidence does not establish the longer transport claim, and the video should not imply otherwise.

### The optical model and its missing physics

The model combines a scalar Fresnel/Bessel field with an ideal, lossless, specularly reflecting octahedron. Its particle has a 300-micrometre tip span and a mass of 6.75 micrograms. These are the assumptions of the optical calculation, not the magnetic-actuation assumptions used by the fast-exploration application.

The calculation is not a full-vector electromagnetic scattering solution based on a Maxwell stress tensor. It does not yet include a fully characterized permittivity, absorption and heating response, surface roughness or coating physics. Ideal reflection is a simplification that keeps the research question focused, but it is not a measured material response.

Even within that simplified model, reliable face integration for force and torque remains difficult. At the frozen snapshot, surface-region uncertainty bounds were approximately 9.39 × 10⁻⁸ N for force and 4.28 × 10⁻¹¹ N m for torque. The unchanged accuracy gates were 8.75 × 10⁻¹⁹ N and 8.75 × 10⁻²⁴ N m. The bounds remain above those gates.

Those values are numerical uncertainty bounds for the tested surface region. They are not measured physical errors and are not whole-trajectory bounds. Complete coverage and tighter bounds are useful progress, but they do not turn a non-pass into a pass. Subsequent targeted tests also produced non-passes. A numerical non-pass alone does not prove an actual singularity or physical impossibility.

### What I want the video to communicate

The video makes the saved geometry and the remaining uncertainty easier to see together. I am keeping the difficult results visible because they determine what the calculation can support. Presentation refinements after the evidence cutoff do not create a new force solution or establish a new scientific result.

I do not have all the answers. I would welcome constructive collaboration on optical-force integration, numerical verification, microscale mechanics and material assumptions. The most useful next contribution is one that helps distinguish a better-looking result from a better-supported result.

### Implemented mathematics behind the optical research

The source computes a scalar propagated field, transfers its momentum to ideal reflective facets and integrates the resulting loads. The replay plots saved outputs; it does not repeat these calculations. This distinction also applies to the baseline local stiffness and eigenvalue machinery, which already exists in the research source.

$$
\Psi(r,z)=2\pi\int_0^{R_p}\frac{\rho_p^2}{W}e^{-(\rho_p/W)^2}e^{i k_0\rho_p^2(1/s-1/L)/2}J_1(k_0r\rho_p/s)\,d\rho_p
$$

$$
N=2\pi\int_0^{R_p}\frac{\rho_p^3}{W^2}e^{-2(\rho_p/W)^2}\,d\rho_p,\quad i_z=\frac{|\Psi|^2}{(\lambda s)^2N},\quad I_z=Pi_z
$$

Here ρp is the pupil-radius integration variable, r the observation radius, s = L + z, k₀ = 2π/λ, and all lengths are in metres. The pupil radius Rp = 2 m, width W = 1.4 m and wavelength λ = 1,064 nm. J₁ is the first-kind Bessel function of order one. Under this amplitude convention Ψ and N each have units m²; normalized axial flux iz is in m⁻² and Iz in W/m². Gauss–Legendre pupil quadrature and field tables implement this scalar propagation, not a complete vector electric and magnetic field solution.

$$
\mu_h=\hat{\mathbf k}_h\cdot\mathbf n,\quad dP_h=\frac P2 i_z\frac{\max(0,-\mu_h)}{\hat k_{h,z}}dA,\quad d\mathbf F_h=\frac2c dP_h\mu_h\mathbf n
$$

The two winding contributions h = ±1 each receive half the channel power. P [W] is useful post-aperture channel allocation, not intercepted particle power or electrical input. The outward facet normal is n, the incoming unit direction is k̂h, c is light speed [m/s] and dA is area [m²]. For an illuminated face μh < 0, so the source convention pushes inward relative to n; normal incidence gives force magnitude 2 dP/c. This momentum rule assumes ideal lossless specular reflection, with the original direction-validity guards still required.

$$
\mathbf F=\sum_p\int_{S_p}\mathbf t\,dA\simeq\sum_p\sum_jw_{pj}\mathbf t(\mathbf r_{pj})
$$

$$
\boldsymbol\tau=\sum_p\int_{S_p}(\mathbf r-\mathbf r_c)\times\mathbf t\,dA\simeq\sum_p\sum_jw_{pj}(\mathbf r_{pj}-\mathbf r_c)\times\mathbf t(\mathbf r_{pj})
$$

Traction t is in N/m², area weights wpj in m², force in N and torque in N m. Each patch Sp is a surface region; its quadrature nodes sample space, not different times. The weighted sums approximate the integrals. Torque adds a lever arm and possible cancellation, which is why force and torque need separate accuracy checks. The frozen non-passes remain in force despite the smoother display.

$$
A_{:,j}\simeq P\frac{G_{\rm unit}(h_je_j)-G_{\rm unit}(-h_je_j)}{2h_j},\quad J_{\rm dyn}=\begin{bmatrix}0&I\\M_6^{-1}A&-D\end{bmatrix}
$$

The generalized pose is q₆ = (position, rotation vector) and G = (force, torque). The coordinate unit vector ej selects one position or rotation coordinate. The source perturbs that coordinate each way using hj = 10⁻⁸ m for translation or 10⁻⁵ rad for rotation; P equals SUPPORT divided by the zero-pose vertical component of Gunit, scaling that unit-power load to the support requirement. M₆ contains three masses and three body inertias; D contains the corresponding translational and rotational damping rates [s⁻¹]. The 12-state matrix maps pose and velocity perturbations to their time derivatives, and the source evaluates its eigenvalues.

The output key K stores A, the positive generalized load Jacobian. Conventional restoring stiffness is −A, so signs must not be silently exchanged. Translational blocks have units N/m, rotational blocks N m/rad, and mixed blocks have different units. Negative real eigenvalue parts imply local asymptotic stability only for this linearization at an appropriate equilibrium. Matching vertical support at zero pose does not prove every force and torque balances. This implemented baseline is not new wavefront optimization, certified stiffness or proof of 108-metre transport; the video’s K label remains explanatory.

### Later component test kept separate

A later bounded test on 31 October rewrote a difficult polynomial factor without dropping its 119 coefficients. It used the exact substitution z = w² and d = −hw to regroup the polynomial into powers of w, up to degree 38. Both factor enclosures still included zero. The test therefore did not certify the required nonzero bound on that complex-domain box.

Its saved-record audit passed, and the computation stopped cleanly. Those outcomes verify preservation and accounting of the component result; they do not turn the numerical non-pass into a complete force, torque, stiffness or transport qualification. An enclosure containing zero does not establish an actual physical zero or singularity. The original accuracy gates remain unchanged, and 108-metre transport remains unverified.

### Why the six paths look nearly parallel

In the saved corrected comparison, x spans approximately 1.998 to 53.898 m. The six nominal lateral lanes are approximately −0.75, −0.45, −0.15, 0.15, 0.45 and 0.75 m. Within each lane, the saved lateral variation is only about 0.22–0.25 µm; the combined relative vertical range is about −0.140 to +1.274 µm. These relative vertical offsets are not altitude above the ground.

The left diagnostic enlarges those tiny deviations independently of the metre-scale travel. The right 150-metre cube preserves equal physical axis scale. An oblique projection can look rectangular without changing that physical scale. The paths are not six invented sweeping routes, and the magnified vertical motion should not be described as large-amplitude flight.

### Suggested caption

I’m showing six saved optical-model paths, with true-scale and explicitly magnified views kept separate. The corrected comparison stops near 53.9 metres, and the current force and torque checks do not certify 108-metre transport.

### Mathematical sources

Outdoor optical mathematics: research/optical/source/model.py lines 11–18 and 25–33 (scalar field), 38–49 (facet momentum), and 50–57 (baseline load Jacobian and eigenvalues); scaled_loads.py lines 21–28 (load integration); core.py lines 32–36 (channel-power scaling). Presentation equations explain this source and do not initiate a new solve.

Later component evidence: `OUTDOOR_COMPONENT_REVIEWED_RESULT.md`, `RESULT.json` and `INDEPENDENT_SAVED_AUDIT.json` from the composed-factor study. Saved trajectory layout is documented in `render_outdoor_cube.py` and its accompanying input data.
