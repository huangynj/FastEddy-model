==========================
Dry neutral boundary layer
==========================

Background
----------

This is a canonical neutral boundary layer scenario. The case is broadly based upon Sauer and Munoz-Esparza (2020) but is not identical. A geostrophic wind is prescribed over ground with a set aerodynamic roughness length under a neutrally stratified boundary layer. The purpose of this test case is to visualize and analyze the resultant flow and turbulence characteristics that develop when the LES reaches statistical steady-state.

Input parameters
----------------

* Number of grid points: :math:`[N_x,N_y,N_z]=[640,634,58]`
* Isotropic grid spacings in the horizontal directions: :math:`[dx,dy]=[15,15]` m, vertical grid is :math:`dz=15` m at the surface and stretched with verticalDeformFactor :math:`=0.75`
* Domain size: :math:`[9.6 \times 9.51 \times 1.08]` km
* Model time step: :math:`0.04` s
* Advection scheme: 5th-order upwind
* Time scheme: 3rd-order Runge Kutta
* Geostrophic wind: :math:`[U_g,V_g]=[10,0]` m/s
* Latitude: :math:`54.0^{\circ}` N
* Surface potential temperature: :math:`300` K
* Potential temperature profile:

.. math::
  \partial{\theta}/\partial z =
    \begin{cases}
      0 & \text{if $z$ $\le$ 500 m}\\
      0.08 & \text{if 500 m < $z$ $\le$ 650 m}\\
      0.003 & \text{if $z$ > 650 m}
    \end{cases} 

* Surface heat flux:  :math:`0.0` Km/s
* Surface roughness length: :math:`z_0=0.1` m
* Rayleigh damping layer: uppermost :math:`400` m of the domain
* Initial perturbations: :math:`\pm 0.25` K 
* Depth of perturbations: :math:`375` m
* Top boundary condition: free slip
* Lateral boundary conditions: periodic
* Time period: :math:`7` h

Execute FastEddy
----------------

1. Create a working directory to run the FastEddy tutorials and change to that directory.
2. Create a **Example01_NBL** subdirectory and change to that directory.
3. The FastEddy code will write its output to an **output** subdirectory. Create an **output** directory, if one does not already exist.   
4. Run FastEddy using the input parameters file *Example01_NBL.in* located in the **tutorials/examples/** subdirectory of the FastEddy repository. 

See :ref:`run_fasteddy` for instructions on how to build and run FastEddy on NSF NCAR's High Performance Computing machines.

Visualize the output
--------------------

1. Open the Jupyter notebook entitled *MAKE_FE_TUTORIAL_PLOTS.ipynb*.
2. Under the "Define parameters" section, modify :code:`path_base`, specifying the full path to the **Example01_NBL** subdirectory, but don't include **Example01_NBL** subdirectory. Be sure to include a trailing slash :code:`/`).
3. Under the "Define parameters" section, modify :code:`case` to set its value to :code:`neutral`.
4. Run the Jupyter notebook.
5. The resulting XY cross section png plots will be placed in a **FIGS** subdirectory of the **Example01_NBL** directory.

XY-plane views of instantaneous velocity components at :math:`t=7` h (FE_NBL.630000):

.. image:: ../images/UVWTHETA-XY-neutral.png
  :width: 1200
  :alt: Alternative text
  
XZ-plane views of instantaneous velocity components at :math:`t=7` h (FE_NBL.630000):

.. image:: ../images/UVWTHETA-XZ-neutral.png
  :width: 900
  :alt: Alternative text
  
Mean (domain horizontal average) vertical profiles of state variables at :math:`t=7` h (FE_NBL.630000):

.. image:: ../images/MEAN-PROF-neutral.png
  :width: 750
  :alt: Alternative text
 
Horizontally-averaged vertical profiles of turbulence quantities at :math:`t=6-7` h [perturbations are computed at each time instance from horizontal-slab means, then averaged horitontally and over the previous 1-hour mean]:

.. image:: ../images/TURB-PROF-neutral.png
  :width: 1200
  :alt: Alternative text 

Analyze the output
------------------

* Using the XY and XZ cross sections, discuss the characteristics (scale and magnitude) of the resolved turbulence.
* What is the boundary layer height in the neutral case?
* Using the vertical profile plots, explain why the boundary layer is neutral.

