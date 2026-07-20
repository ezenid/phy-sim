# Merged Physics Simulation Scenario Catalog
## Grade 9 + Grade 11 — Simulable Scenarios Only

---

## Master Scenario Index

| # | Domain | Scenario | Grades |
|---|---|---|---|
| 1 | Mechanics/Kinematics | Uniformly Accelerated Motion in 1D | 9–11 |
| 2 | Mechanics/Kinematics | Kinematics Graph Explorer | 9–11 |
| 3 | Mechanics/Kinematics | Vertical Motion / Free Fall | 11 |
| 4 | Mechanics/Kinematics | Uniform Circular Motion | 11 |
| 5 | Mechanics/Dynamics | Newton's Laws Force-Response Sandbox | 9–11 |
| 6 | Mechanics/Dynamics | Block on Surface with Friction (flat/inclined) | 9–11 |
| 7 | Mechanics/Statics | Static Equilibrium of Coplanar Forces | 11 |
| 8 | Mechanics/Statics | Simple Machine Mechanical Advantage & Design Sandbox | 9 |
| 9 | Mechanics/Energy | Work–Energy–Power Sandbox | 9–11 |
| 10 | Mechanics/Energy | Mechanical Energy Conservation Demo | 9–11 |
| 11 | Mechanics/Collisions | Collision & Momentum Lab | 11 |
| 12 | Waves/Oscillation | Simple Harmonic Oscillators: Pendulum & Spring-Mass | 9–11 |
| 13 | Waves | Wave Parameter & Propagation Visualizer | 9 |
| 14 | Waves/Acoustics | Sound Wave & Characteristics Explorer | 9 |
| 15 | Waves | Wave Superposition & Standing Waves | 9 |
| 16 | Thermodynamics | Heat Transfer Simulation (Conduction/Convection/Radiation) | 11 |
| 17 | Thermodynamics | Specific Heat / Heating Curve | 11 |
| 18 | Thermodynamics | Thermal Expansion of Materials | 9–11 |
| 19 | Thermodynamics | Phase Change / Full Heating Curve | 11 |
| 20 | Thermodynamics | Calorimetry Mixing Experiment | 11 |
| 21 | Electricity/Electrostatics | Coulomb Force Between Point Charges | 11 |
| 22 | Electricity/Electrostatics | Electric Field Visualization | 11 |
| 23 | Electricity/Electrostatics | Electric Potential / Equipotential Surfaces | 11 |
| 24 | Electricity/Circuits | DC Circuit Simulator | 11 |
| 25 | Electricity/Circuits | Parallel-Plate Capacitor (Charging/Discharging/Dielectrics) | 11 |
| 26 | Modern Physics/Nuclear | Nucleus Structure & Binding Energy Model | 11 |
| 27 | Modern Physics/Nuclear | Radioactive Decay Simulation | 11 |
| 28 | Modern Physics/Nuclear | Fission/Fusion Energy Release Model | 11 |


---

## 1. Uniformly Accelerated Motion in 1D

- **Environment:** Frictionless 1D track
- **Entities:** Particle
- **Entity Properties:** mass, position, initial velocity, acceleration, color
- **Interactions:** Constant net force (implied constant acceleration)
- **Constraints:** Motion restricted to a single axis
- **Observable Quantities:** position, velocity, acceleration, elapsed time, displacement, average/instantaneous speed
- **Visualization Requirements:** Particle on a track, trail, s–t/v–t line graph, numeric readout
- **User Controls:** initial velocity, acceleration (zero for Grade 9 uniform-motion mode), duration
- **Required Engine Features:** Fixed-timestep integrator
- **Reusable Components:** Particle, Integrator, Trajectory Renderer, Graph Renderer, Camera
- **Dependencies:** Vector primitive, Integrator, Renderer


## 2. Kinematics Graph Explorer

- **Environment:** Abstract 2D graph space
- **Entities:** Graph Curve, Cursor/Marker
- **Entity Properties:** curve data points, cursor time, slope-at-point, area-under-curve
- **Interactions:** none physical — derived-quantity visualization
- **Constraints:** Curve must stay consistent with scenario 1's underlying motion
- **Observable Quantities:** slope (velocity/acceleration), area (displacement)
- **Visualization Requirements:** Multi-panel line graphs, draggable time cursor, shaded area-under-curve, tangent overlay
- **User Controls:** feeds from scenario 1's parameters; cursor position
- **Required Engine Features:** Analytic differentiation/integration of sampled motion data
- **Reusable Components:** Graph Renderer, Cursor/Scrubber widget
- **Dependencies:** Scenario 1's Particle/Integrator output

## 3. Vertical Motion / Free Fall

- **Environment:** Earth gravity (vertical 1D), vacuum or air-drag toggle
- **Entities:** Ball/Particle
- **Entity Properties:** mass, height/position, initial velocity, g
- **Interactions:** Gravity
- **Constraints:** Ground plane, vertical-axis restriction
- **Observable Quantities:** height, velocity, time to max height, time of flight, impact velocity
- **Visualization Requirements:** Vertical track, ball with trail, velocity vector, height-vs-time graph
- **User Controls:** initial velocity/direction, g, release height
- **Required Engine Features:** Same integrator as #1, ground-plane stop condition
- **Reusable Components:** Particle, Gravity System, Integrator, Ground Plane, Trajectory Renderer
- **Dependencies:** Vector primitive, Gravity System, Integrator, Renderer

## 4. Uniform Circular Motion

- **Environment:** Frictionless plane or string-and-mass system
- **Entities:** Ball/Mass, Center pivot
- **Entity Properties:** mass, radius, angular velocity, tangential speed, period, frequency
- **Interactions:** Centripetal force (tension/normal force)
- **Constraints:** Fixed radius, constant angular speed
- **Observable Quantities:** angular position/velocity, tangential velocity, centripetal acceleration/force, period, frequency
- **Visualization Requirements:** Circular path, orbiting particle, velocity vector (tangent), centripetal force vector (inward), period/frequency readout
- **User Controls:** radius, angular velocity/period, mass
- **Required Engine Features:** Circular/polar constraint solver
- **Reusable Components:** Particle, Constraint Solver, Vector Renderer, Camera
- **Dependencies:** Vector primitive, Constraint Solver, Renderer

## 5. Newton's Laws Force-Response Sandbox

- **Environment:** Frictionless horizontal surface, optional two-body contact for 3rd-law demo
- **Entities:** Block/Body A, Block/Body B (3rd-law pair, Grade 11)
- **Entity Properties:** mass, position, velocity, acceleration, applied force(s), net force
- **Interactions:** Applied force, reaction force, normal force
- **Constraints:** Motion on a single plane
- **Observable Quantities:** net force, acceleration, velocity, position, momentum
- **Visualization Requirements:** Block on surface, force vectors, acceleration vector, F=ma readout
- **User Controls:** mass, applied force magnitude/direction
- **Required Engine Features:** Rigid-body force accumulator + integrator
- **Reusable Components:** Rigid Body, Force Accumulator, Integrator, Force Renderer
- **Dependencies:** Vector primitive, Integrator, Renderer

## 6. Block on Surface with Friction (flat/inclined)

- **Environment:** Horizontal surface (Grade 9) or inclined plane (Grade 11 addition)
- **Entities:** Block, Surface/Inclined Plane
- **Entity Properties:** mass, position, velocity, applied force; friction coefficients (static/kinetic), incline angle
- **Interactions:** Applied force, gravity component along incline (11), normal force, static/kinetic friction
- **Constraints:** Block confined to surface plane
- **Observable Quantities:** normal force, friction force, net force, acceleration, static/sliding state
- **Visualization Requirements:** Ramp/plane, block, force vectors (gravity, normal, friction, applied), angle indicator, state indicator
- **User Controls:** incline angle (11), friction coefficients/roughness, applied force, block mass
- **Required Engine Features:** Friction solver (static threshold + kinetic opposing force), incline-frame decomposition (11)
- **Reusable Components:** Rigid Body, Friction Solver, Ground/Incline Plane, Force Renderer
- **Dependencies:** Vector primitive, Force Accumulator (#5), Friction Solver, Renderer

## 7. Static Equilibrium of Coplanar Forces

- **Environment:** Fixed anchor points, gravity present
- **Entities:** Hanging mass/knot point, multiple Strings/Cables
- **Entity Properties:** mass, tension (per string), string angle
- **Interactions:** Gravity, multiple tension forces
- **Constraints:** Fixed anchor points, ΣF=0 required
- **Observable Quantities:** each tension, resultant force, angles
- **Visualization Requirements:** Knot diagram, tension vectors, resultant-force readout (balanced/unbalanced color)
- **User Controls:** number of strings/angles, external force, hanging mass
- **Required Engine Features:** Static force-balance solver (linear system for unknown tensions)
- **Reusable Components:** Force Renderer, Static Solver, Vector primitive
- **Dependencies:** Vector primitive, Force Accumulator

## 8. Simple Machine Mechanical Advantage & Design Sandbox

- **Environment:** Workbench scene, one selectable machine at a time
- **Entities:** Lever (+fulcrum), Inclined Plane/Ramp, Wedge, Screw, Wheel & Axle, Pulley, Load, Effort applicator
- **Entity Properties:** load, effort, lever arm lengths, incline angle/length, pitch, radii, pulley/rope count, friction losses
- **Interactions:** Force transmission, friction losses, torque balance
- **Constraints:** Rigid connections, fixed pivot, rope/pulley inextensibility
- **Observable Quantities:** mechanical advantage, velocity ratio, efficiency, effort required, load moved
- **Visualization Requirements:** Machine mesh, force arrows, distance-moved indicators, live MA/VR/efficiency readout
- **User Controls:** machine type, load, geometry (arm lengths/angle/pulley count/radii/pitch), friction factor
- **Required Engine Features:** Static torque/force-balance solver (per-machine-type closed-form formulas)
- **Reusable Components:** Static/Equilibrium Solver (shared with #7), Force Renderer, generic "Machine" entity with pluggable MA formula
- **Dependencies:** Force Accumulator, Static Solver

## 9. Work–Energy–Power Sandbox

- **Environment:** Horizontal/inclined surface, optional height-based scenario for PE
- **Entities:** Block/Object
- **Entity Properties:** mass, displacement, applied force (magnitude/angle in 11), height, velocity
- **Interactions:** Applied force along/at angle to displacement, gravity (PE), friction (11, negative work)
- **Constraints:** Motion along a defined path
- **Observable Quantities:** work done, kinetic/potential/mechanical energy, instantaneous/average power
- **Visualization Requirements:** Object moving/rising, force vector (with angle indicator in 11), running work/energy tally, power gauge/graph
- **User Controls:** force magnitude (and angle, 11), distance, mass, height, time taken
- **Required Engine Features:** Work integrator (∫F·ds), energy calculator (½mv², mgh), power calculator (dW/dt)
- **Reusable Components:** Force Renderer, Work/Energy Tracker, Graph Renderer
- **Dependencies:** Force Accumulator (#5), Gravity System, Friction Solver (11, optional)

## 10. Mechanical Energy Conservation Demo

- **Environment:** Frictionless track/ramp, pendulum pivot, or spring anchor; gravity present
- **Entities:** Ball/Bob/Mass, Ramp/Pendulum arm/Spring (idealized rigid or elastic)
- **Entity Properties:** mass, height, velocity, spring constant (spring variant), pendulum length
- **Interactions:** Gravity, normal force/tension/spring force
- **Constraints:** No friction/drag, fixed track/pivot/anchor geometry
- **Observable Quantities:** kinetic/potential/total mechanical energy, height, speed, period (oscillation variants)
- **Visualization Requirements:** Moving body along track/arc/spring, stacked KE/PE chart, total-energy line graph (flat = conserved), period timer
- **User Controls:** release height/angle, mass, track/oscillator type, gravity, spring constant
- **Required Engine Features:** Energy-conserving integrator (symplectic/Verlet preferred), constraint solver (pendulum arc/ramp curve), spring solver
- **Reusable Components:** Gravity System, Constraint Solver, Spring Solver, Energy Tracker, Graph Renderer
- **Dependencies:** Integrator, Constraint Solver, Gravity System

## 11. Collision & Momentum Lab

- **Environment:** Frictionless horizontal plane
- **Entities:** Body A, Body B
- **Entity Properties:** mass, velocity (vector), momentum, coefficient of restitution
- **Interactions:** Collision (impulsive contact force), momentum transfer
- **Constraints:** Momentum conservation (always), KE conservation (elastic only)
- **Observable Quantities:** momentum (each/total), impulse, velocity before/after, KE before/after, restitution
- **Visualization Requirements:** Two bodies colliding, velocity vectors before/after, momentum bar comparison, collision flash
- **User Controls:** mass, initial velocities, collision type (elastic/inelastic/perfectly inelastic), 1D/2D toggle
- **Required Engine Features:** Collision detector (1D line/2D circle-circle), impulse-based resolver with restitution
- **Reusable Components:** Rigid Body, Collision Detector, Collision Resolver, Vector Renderer
- **Dependencies:** Vector primitive, Integrator, Rigid Body (#5)

## 12. Simple Harmonic Oscillators: Pendulum & Spring-Mass

- **Environment:** Fixed pivot with gravity (pendulum), spring-anchor system
- **Entities:** Pendulum Bob + String, Mass + Spring
- **Entity Properties:** string length, bob mass, angle, period (pendulum); mass, spring constant, displacement, period (spring)
- **Interactions:** Gravity + tension (restoring force, pendulum), spring force (Hooke's law restoring force)
- **Constraints:** Fixed pivot/string length, fixed spring anchor
- **Observable Quantities:** period, frequency, amplitude, displacement, velocity, restoring force
- **Visualization Requirements:** Swinging pendulum with arc trail, oscillating spring-mass with displacement markers, period timer, displacement-vs-time graph
- **User Controls:** pendulum length, bob mass, gravity, spring constant, mass, initial displacement/angle
- **Required Engine Features:** Constraint solver (pendulum arc), Spring solver (Hooke's law integrator)
- **Reusable Components:** Constraint Solver, Spring Solver, Gravity System, Graph Renderer
- **Dependencies:** Integrator, Constraint Solver, Spring Solver

## 13. Wave Parameter & Propagation Visualizer

- **Environment:** 1D medium (string, spring, or air column)
- **Entities:** Wave (traveling waveform), Medium particles
- **Entity Properties:** amplitude, wavelength, frequency, period, wave speed, wave type, propagation direction
- **Interactions:** Propagation of disturbance through the medium
- **Constraints:** Fixed medium boundaries, wave speed determined by medium
- **Observable Quantities:** amplitude, wavelength, frequency, period, wave speed, energy transported
- **Visualization Requirements:** Animated waveform (transverse/longitudinal), medium-particle oscillation markers, wavelength/amplitude overlays, wave-speed readout
- **User Controls:** amplitude, frequency, wave speed/medium, wave type toggle, boundary condition
- **Required Engine Features:** Wave solver (parametric traveling-wave function driving particle positions)
- **Reusable Components:** Wave Solver, Waveform Renderer, Particle-oscillation Renderer
- **Dependencies:** Vector primitive, Graph/Waveform Renderer

## 14. Sound Wave & Characteristics Explorer

- **Environment:** Medium (air) with vacuum toggle, sound source and observer
- **Entities:** Sound Source, Medium, Observer/Listener
- **Entity Properties:** frequency, amplitude, waveform shape, medium presence, propagation speed
- **Interactions:** Longitudinal compression/rarefaction propagation
- **Constraints:** No propagation without a medium, fixed speed per medium
- **Observable Quantities:** frequency, pitch, amplitude, loudness, wave speed, wavelength
- **Visualization Requirements:** Longitudinal wavefront animation, waveform display, vacuum-vs-air toggle, frequency/amplitude sliders with live waveform feedback
- **User Controls:** frequency, amplitude, medium, source waveform
- **Required Engine Features:** Wave Solver (shared with #13), medium-dependent propagation-speed lookup
- **Reusable Components:** Wave Solver, Waveform Renderer
- **Dependencies:** Wave Solver (#13)

## 15. Wave Superposition & Standing Waves

- **Environment:** Shared medium carrying two overlapping waves
- **Entities:** Wave A, Wave B, Resultant Wave, Medium
- **Entity Properties:** amplitude, wavelength, frequency, phase (per component); resultant displacement
- **Interactions:** Linear superposition, constructive/destructive interference
- **Constraints:** Shared medium required; standing wave requires identical frequency/wavelength + opposite direction
- **Observable Quantities:** resultant amplitude, node/antinode position, phase difference
- **Visualization Requirements:** Component waveforms + live-summed resultant, node/antinode markers, phase-difference slider, standing-wave envelope animation
- **User Controls:** amplitude/frequency/phase per component, direction toggle
- **Required Engine Features:** Wave superposition calculator (pointwise sum each timestep)
- **Reusable Components:** Wave Solver, Waveform Renderer

## 16. Heat Transfer Simulation (Conduction/Convection/Radiation)

- **Environment:** Rod between hot/cold reservoirs; fluid container with heat source; radiating object in free space
- **Entities:** Rod/Slab, Hot/Cold Reservoir, Fluid volume, Radiating Object
- **Entity Properties:** thermal conductivity, cross-sectional area, length/thickness, temperature, emissivity, surface area
- **Interactions:** Conductive heat flow, convective circulation, radiative emission
- **Constraints:** Fixed reservoir temperatures (boundary conditions)
- **Observable Quantities:** heat flow rate, temperature gradient/profile, temperature vs. time
- **Visualization Requirements:** Color-coded temperature heat map on rod, animated convection arrows/particles, radiating glow, temperature-vs-position/time graphs
- **User Controls:** material (conductivity), rod geometry, reservoir temperatures, emissivity
- **Required Engine Features:** 1D heat conduction solver (finite-difference), convection particle-advection model, radiation flux calculator
- **Reusable Components:** Heat Solver, Heat-map Renderer, Graph Renderer
- **Dependencies:** Vector primitive, Graph Renderer

## 17. Specific Heat / Heating Curve

- **Environment:** Isolated sample heated by constant-power source
- **Entities:** Sample/Block, Heat Source
- **Entity Properties:** mass, specific heat capacity, temperature, heater power
- **Interactions:** Heat input raising temperature per Q=mcΔT
- **Constraints:** No heat loss to surroundings
- **Observable Quantities:** temperature, heat added, time
- **Visualization Requirements:** Thermometer widget, temperature-vs-time graph (multi-material comparison), color shift of sample
- **User Controls:** material/specific heat, mass, heater power
- **Required Engine Features:** Thermal integrator (dT/dt = P/(mc))
- **Reusable Components:** Heat Solver, Graph Renderer, Thermometer widget
- **Dependencies:** Heat Solver (#16)

## 18. Thermal Expansion of Materials

- **Environment:** Rod/bar/plate or liquid-in-container under temperature change
- **Entities:** Rod/Bar/Plate, Liquid volume/Container
- **Entity Properties:** original length/area/volume, expansion coefficient, temperature
- **Interactions:** Temperature-driven dimensional change
- **Constraints:** Uniform temperature across the object
- **Observable Quantities:** change in length/area/volume, final dimension
- **Visualization Requirements:** Rod/liquid-level visibly growing/shrinking (exaggerated scale), side-by-side material comparison, numeric ΔL/ΔV readout
- **User Controls:** material (expansion coefficient), initial dimension, temperature change
- **Required Engine Features:** Simple analytic expansion calculator
- **Reusable Components:** Graph/readout Renderer
- **Dependencies:** none beyond core renderer

## 19. Phase Change / Full Heating Curve

- **Environment:** Isolated sample heated at constant rate
- **Entities:** Sample (with phase state)
- **Entity Properties:** mass, specific heat (per phase), latent heat of fusion/vaporization, melting/boiling point, current phase, temperature
- **Interactions:** Heat input raising temperature within a phase; heat consumed by phase transition (plateau)
- **Constraints:** Temperature capped at melting/boiling point until latent heat fully supplied
- **Observable Quantities:** temperature, phase, cumulative heat added, time
- **Visualization Requirements:** Full heating-curve graph (staircase-with-plateaus) with live cursor, visual phase representation, plateau highlighting
- **User Controls:** substance preset, heater power, initial phase/temperature
- **Required Engine Features:** Phase-state machine layered on the #17 thermal integrator
- **Reusable Components:** Heat Solver, Phase State Machine, Graph Renderer
- **Dependencies:** Heat Solver (#17)

## 20. Calorimetry Mixing Experiment

- **Environment:** Insulated calorimeter holding two+ substances at different temperatures
- **Entities:** Substance A, Substance B, Calorimeter container
- **Entity Properties:** mass, specific heat, initial temperature, calorimeter heat capacity
- **Interactions:** Heat transfer until equilibrium (ΣQ_lost = ΣQ_gained)
- **Constraints:** No heat loss to external environment, energy conservation
- **Observable Quantities:** final equilibrium temperature, heat exchanged, time to equilibrium
- **Visualization Requirements:** Container with merging different-temperature substances, temperature-convergence graph, color gradient
- **User Controls:** mass/initial temperature per substance, specific heats/materials, calorimeter heat capacity
- **Required Engine Features:** Energy-balance solver (algebraic) and/or coupled thermal-exchange ODE
- **Reusable Components:** Heat Solver, Graph Renderer, Container entity

## 21. Coulomb Force Between Point Charges

- **Educational Objective:** Force between point charges ∝ product of charges / distance², attraction/repulsion by sign.
- **Environment:** Vacuum/air, free space with two+ point charges
- **Entities:** Point Charge A, Point Charge B (extendable to N)
- **Entity Properties:** charge magnitude/sign, position, mass (optional dynamic mode)
- **Interactions:** Coulomb force (inverse-square)
- **Constraints:** Charges fixed or free to move
- **Observable Quantities:** force magnitude/direction, distance
- **Visualization Requirements:** Color-coded charge spheres, force vector arrows, distance readout, force-vs-distance graph
- **User Controls:** charge magnitudes/signs, separation, free-motion toggle
- **Required Engine Features:** Pairwise inverse-square calculator (N-body superposition)
- **Reusable Components:** Point Charge entity, Electrostatic Force Solver, Vector Renderer
- **Dependencies:** Vector primitive, Integrator (if movable)

## 22. Electric Field Visualization

- **Educational Objective:** Field from one/more point charges; field-line direction/density; force on a test charge.
- **Environment:** Free space with source charges and a movable test charge/probe
- **Entities:** Source Charge(s), Test Charge/Probe
- **Entity Properties:** charge, position, field vector at probe
- **Interactions:** Field superposition evaluated at probe
- **Constraints:** Test charge assumed non-perturbing
- **Observable Quantities:** field strength/direction, force on test charge
- **Visualization Requirements:** Field-line streamlines, field vector grid, draggable probe with live readout
- **User Controls:** source charge configuration, probe position
- **Required Engine Features:** Field superposition evaluator (grid), field-line tracer
- **Reusable Components:** Electrostatic Force Solver (#21), Field-line Renderer, Vector Renderer
- **Dependencies:** Coulomb Force Solver (#21), Vector primitive

## 23. Electric Potential / Equipotential Surfaces

- **Environment:** Free space with source charges
- **Entities:** Source Charge(s), Sample Point/Probe
- **Entity Properties:** charge, position, potential value
- **Interactions:** Superposition of scalar potential contributions
- **Constraints:** none beyond superposition validity
- **Observable Quantities:** potential at a point, potential difference
- **Visualization Requirements:** Equipotential contours overlaid with field lines, color-mapped potential heat map, two draggable probes with ΔV readout
- **User Controls:** source charge configuration, probe positions
- **Required Engine Features:** Scalar potential field evaluator, contour extraction (marching squares)
- **Reusable Components:** Electrostatic Force Solver (#21), Heat-map/Contour Renderer
- **Dependencies:** Coulomb Force Solver (#21)

## 24. DC Circuit Simulator

- **Environment:** User-assembled or preset circuit topology
- **Entities:** Battery/Cell, Resistor, Wire, Ammeter, Voltmeter, Galvanometer, Wheatstone Bridge, Potentiometer
- **Entity Properties:** EMF, internal resistance, resistance value, meter internal resistance/range
- **Interactions:** Current flow, voltage drops, KCL/KVL
- **Constraints:** Charge conservation at nodes, energy conservation around loops, fixed topology
- **Observable Quantities:** current, voltage, power dissipated, equivalent resistance, terminal p.d.
- **Visualization Requirements:** Schematic diagram, animated current-flow indicators, per-component labels, bridge-balance indicator
- **User Controls:** EMF, internal resistance, resistor values, topology, meter placement/range
- **Required Engine Features:** Linear circuit solver (nodal analysis / matrix solve)
- **Reusable Components:** Circuit Solver, Schematic Renderer, Vector/Arrow Renderer
- **Dependencies:** none beyond core renderer

## 25. Parallel-Plate Capacitor (Charging/Discharging/Dielectrics)

- **Environment:** Parallel-plate capacitor in an RC circuit, optional dielectric insertion
- **Entities:** Capacitor, Dielectric slab, Resistor, Battery, Switch
- **Entity Properties:** plate area, separation, dielectric constant, capacitance, charge, voltage, resistance, EMF
- **Interactions:** Charging/discharging current, exponential approach to final charge, dielectric polarization
- **Constraints:** Q = CV, energy conservation
- **Observable Quantities:** capacitance, charge, voltage, current, RC time constant, stored energy
- **Visualization Requirements:** Plates with visible charge buildup, sliding dielectric with capacitance readout, charge/voltage-vs-time exponential graph
- **User Controls:** plate area/separation, dielectric material, resistance, EMF, charge/discharge switch
- **Required Engine Features:** RC exponential charge/discharge solver
- **Reusable Components:** Circuit Solver (#24, extended), Graph Renderer
- **Dependencies:** Circuit Solver (#24)

## 26. Nucleus Structure & Binding Energy Model

- **Environment:** Abstract/schematic nuclear model
- **Entities:** Proton, Neutron, Nucleus
- **Entity Properties:** atomic number, mass number, nucleon mass, nuclear mass, mass defect, binding energy
- **Interactions:** (nuclear strong force implied qualitatively)
- **Constraints:** A = Z + N
- **Observable Quantities:** mass defect, binding energy, binding energy per nucleon
- **Visualization Requirements:** Schematic nucleus (proton/neutron cluster), isotope selector, binding-energy-per-nucleon reference chart
- **User Controls:** element/isotope selection
- **Required Engine Features:** Mass-defect/binding-energy calculator (E=Δmc²)
- **Reusable Components:** Schematic Renderer, isotope/element data lookup table
- **Dependencies:** none beyond core renderer

## 27. Radioactive Decay Simulation

- **Environment:** Sample containing N₀ radioactive nuclei (population or discrete stochastic particles)
- **Entities:** Radioactive Nucleus, Daughter Nucleus (chain variant)
- **Entity Properties:** decay constant, half-life, undecayed count, decay type
- **Interactions:** Stochastic decay event or deterministic exponential decay
- **Constraints:** Monotonic decrease in parent count, probability conservation
- **Observable Quantities:** undecayed-nuclei count over time, activity, half-life
- **Visualization Requirements:** Decay curve graph, particle-population view, half-life marker, decay-chain diagram
- **User Controls:** initial nuclei count, half-life/decay constant, simulation speed, stochastic/deterministic toggle
- **Required Engine Features:** Exponential decay solver, per-particle RNG-driven decay check
- **Reusable Components:** Graph Renderer, Particle-population Renderer, RNG utility
- **Dependencies:** none beyond core renderer/graph system

## 28. Fission/Fusion Energy Release Model

- **Environment:** Abstract reaction diagram
- **Entities:** Parent Nucleus/Nuclei, Product Nucleus/Nuclei, Neutron(s)
- **Entity Properties:** mass before/after, released energy, neutrons released, reaction type
- **Interactions:** Mass-defect-to-energy conversion, chain-reaction propagation
- **Constraints:** Mass-energy conservation, critical-mass threshold (chain variant)
- **Observable Quantities:** energy released per reaction, cumulative energy, active reactions per generation, reaction rate
- **Visualization Requirements:** Before/after diagram with energy-release flash, chain-reaction branching animation, cumulative-energy graph
- **User Controls:** reaction type/isotopes, initial neutron count, branching factor (chain variant)
- **Required Engine Features:** Mass-energy release calculator, branching-process simulator
- **Reusable Components:** Schematic Renderer (#26), Graph Renderer, RNG utility (#27)
- **Dependencies:** Nucleus/binding-energy model (#26), RNG utility (#27)

---

