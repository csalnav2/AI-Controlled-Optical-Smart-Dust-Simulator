# Outdoor fast exploration prototype

Chris Salnave

Documentation refreshed on 31 October 2026. The underlying application description remains tied to the previously reviewed upload. This refresh does not claim a new application execution or hardware validation.

### What the application lets me investigate

The second notebook explores a virtual fleet of six 300-micrometre octahedral particles moving through landscapes. It provides per-agent and fleet commands for launch, hold, passive drift and requested cruise, with telemetry and a follow camera. It also includes synthetic image and video capture, optional conversation features and a simulated cloak effect. This is an implemented interactive prototype rather than a pre-rendered movie, but the uploaded notebook contains no execution outputs establishing a current run.

The particle’s diamond-like appearance describes its octahedral geometry, not a claim that it is made from diamond. Display markers are magnified so the tiny bodies remain visible. The apparent size of a marker in the landscape therefore should not be used to estimate the physical particle size. The cloak feature changes visual observability in the simulation; it does not demonstrate physical invisibility.

### The default propulsion is magnetic rather than optical

This prototype’s default actuation is distributed magnetic forcing. Software guidance can be autonomous within that externally driven simulation; this is not demonstrated autonomous onboard propulsion. Its standard preset requests 1.2 m/s with an assumed 1 T/m field gradient; the fast preset requests 5 m/s with an assumed 7 T/m gradient. A requested speed is a controller target, not a guaranteed response. The model’s available force, drag, gravity and controller saturation determine how the particle responds.

The force assumptions use a 6.75-microgram particle with an 8 percent magnetic volume fraction and an assumed saturation magnetization. The resulting nominal force values are 144 nN in the standard preset and 1,008 nN in the fast preset. These assumptions do not include a demonstrated design for generating the required magnetic field across the displayed landscape.

That propulsion choice also separates this application from the optical research video. The outdoor research work studies a scalar optical field and an ideal reflective octahedron. The magnetic prototype is not a faster, completed version of that calculation, and its requested cruise speed is not evidence that the optical model has achieved the same transport.

### What the motion and sensors actually represent

The runtime connects a particle physics model to a controller. It integrates bounded translational forces with gravity, buoyancy, finite-Reynolds-number drag, rarefaction corrections and noise. Air is represented by a 24 by 24 horizontal periodic tile with mean wind and synthetic gusts. This is not terrain-resolved or body-resolved computational fluid dynamics, and its shape-averaged scalar drag is not a detailed aerodynamic account of the octahedron.

Yaw belongs to the virtual camera framework rather than a physical rotational mechanics model. A smooth camera turn should therefore be read as a viewing behavior, not as proof of a realizable particle attitude maneuver.

The camera model begins with hypothetical noisy 32 by 32 imagery and includes fusion and optional convolutional-neural-network denoising to a 128 by 128 output. Thermal imagery assigns synthetic radiance. These features can help explore perception software, but a larger or cleaner output image does not establish an integrated microscale sensor or measured resolving power.

### What its saved test history means

An embedded historical report from 6 October records 121 regression passes and a separate 180-second, six-particle exploration scenario using one volcanic seed. It is useful software history, not evidence of a fresh execution of this upload, broad physical validation or the optical research model’s 108-metre target. I want that history preserved without asking it to support a different claim.

### Implemented mathematics in the outdoor application

The default outdoor application starts with an octahedral geometry and an assumed magnetic material fraction. It uses those assumptions to cap a controllable external force. That ceiling is separate from the optical force calculation shown in the research video.

$$
\mathcal V=a^3/6,\quad m_p=\rho_p\mathcal V,\quad \mu_m=f_m\mathcal V M_s,\quad F_{\max}=\mu_mG_B
$$

The tip span a is in metres, volume 𝒱 in m³, density ρp in kg/m³, magnetic fraction fm dimensionless, saturation magnetization Ms in A/m and gradient GB in T/m. Multiplying volume by magnetic fraction and magnetization gives moment μm [A m²]; multiplying that moment by the assumed gradient gives force [N]. The default values yield 6.75 µg and 1.44 × 10⁻⁷ A m², hence 144 nN at 1 T/m or 1,008 nN at 7 T/m. These are the preset force ceilings, not a landscape coil design.

$$
m_p\dot{\mathbf v}=\mathbf F_{\rm applied}-\beta(\mathbf v-\mathbf u)-(m_p-\rho\mathcal V)g\hat{\mathbf z},\quad\|\mathbf F_{\rm applied}\|\le F_{\max}
$$

$$
Re=\rho d_{\rm eq}\|\mathbf v-\mathbf u\|/\mu,\qquad \beta=\frac{\pi\mu d_{\rm eq}(C_D Re)}{8C_c}
$$

The deterministic motion balance combines force, air-relative drag and buoyant weight. Velocities v and u are in m/s, β in kg/s, air density ρ in kg/m³, gravity g in m/s², equivalent diameter deq in metres and dynamic viscosity μ in Pa s; ẑ is the upward unit vector. Re, CD and Cc are dimensionless. The displayed drag expression is the octahedral continuum/slip branch; the code uses a shape-averaged correlation, a slip correction and a separate high-Knudsen branch, and adds stochastic velocity fluctuations. Actual speed and saturation plots show the consequence of this balance, not the requested speed alone.

$$
\mathbf a_c=\operatorname{clip}_{a_{\max}}[k_p(\mathbf x_*-\mathbf x)+k_v(\mathbf v_*-\mathbf v)]
$$

$$
\mathbf F_{\rm request}=m_p\mathbf a_c+\beta(\mathbf v-\mathbf u)+(m_p-\rho\mathcal V)g\hat{\mathbf z}
$$

Position error [m] and velocity error [m/s] are multiplied by kp = 3 s⁻² and kv = 3.5 s⁻¹ to request acceleration [m/s²]. The controller clips acceleration, adds drag and weight compensation, then the physics layer clips force to Fmax; an unarmed or crashed agent receives zero applied force. This sequence connects Launch, Hold and Explore commands to the force-fraction readout. Guidance can be autonomous in software while the physical actuation remains external and hypothetical.

### How this fits the latest showcase

The cinematic or application sequence presents the intended operating experience under explicit software assumptions. The scientific component videos and numerical reports are separate evidence. They should be introduced separately when these clips are edited together.

A new standalone fluorescence photon-budget benchmark is described in `FLUORESCENCE_DETECTION_EXPLANATION.md`. It explores a nonspecific fluorescent-event alert under stated optical and background assumptions. It has not been integrated into this application, and it does not upgrade the application's existing camera into a characterized miniature instrument. The exact detector package, illumination hardware, optics, mass, power and communications remain unresolved engineering questions.

### Suggested caption

This outdoor prototype lets me explore fleet commands, sensing and motion under explicit magnetic-actuation assumptions. It is a software testbed for possible behavior, not a demonstration of optical transport or a field-ready smart-dust system.

### Mathematical sources

Outdoor application mathematics: smartdust_lab/particle_physics.py lines 165–190 (magnetic ceiling), 192–212 and 247–277 (drag and translation), 278–288 (virtual yaw), 23–26 and 360–374 (controller); smartdust_lab/particle_geometry.py and docs/FAST_EXPLORATION_V27.md (geometry and presets).
