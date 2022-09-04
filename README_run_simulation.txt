How to run a simulation?

1. Connect "init_SCENE_NAME"  node to "SimulationInputs" node, and activate "simulate_filaments" node.

2. Activate the following nodes in the "dopnet_filaments" node.

[For curve evolution]
Fields:
- sopgeo_curve
- sopgeo_boundbox
- sopvectorfield_psi
- sopvectorfield_vel

Solvers:
- update_vel
- advect_psi
- update_curve
- construct_psi
- multisolver

(for Jet) additionally 
Fields:
- sopgeo_auxcurve
Solvers:
- addNewCurvesForJet

(for Jet_Obstacle) additionally 
Fields:
- sopgeo_auxcurve
- sopgeo_obstacle 
- sopgeo_inv_obstacle 
Solvers:
- addNewCurvesForObstacle
- KelvinBoundaryHandle

(Optional)
Transportation of psi using MacCormack or BFECC near the end of simulation domain may causes artifacts. 
Blending Semi-Lagrangian by activating the following nodes can resolve this issue.
Fields: 
- sopvectorfield_psi2
Solvers:
- update_psi2
- advect_psi2
- blend_psi2_to_psi

[For transporting particles in Orthogonal_rings]
Fields: 
- sopgeo_particles
Solvers:
- advect_particles

[For transporting smoke in Jet and Jet_Obstacle]
Fields:
- sopscalarfield_smoke
- sopvectorfield_exvel

Solvers:
- update_exvel
- advect_smoke

(For Jet)
additionally
- smokeSourceForJet

(For Jet_Obstacle)
additionally 
- smokeSourceForObstacle
