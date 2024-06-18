# README #

Hello world! Welcome to LMG "Lagrangian Meshes Generator", a python-based image processing tool able to generate dynamic geometric meshes from time-lapse images of continuous processes. 

![Alt text](https://github.com/guijoe/lmg/blob/main/img/lmg.gif "Invagination")

### Brief Description ###

* By "Lagrangian", we mean that the generated mesh vertices behave as Lagrangian points that can be tracked between consecutive time points.  
* Hence, the positions of these vertices, connected by a fixed network, can be used to compute all sorts of quantitative indicators, including continuum fields such as velocity, strain, strain-rate, etc. suitable for an in-depth study of the processes at play in the movies.
* The process of interest could cover a wide range of scenarii, basically, anything that can be store as a time-lapse movie of voxel. Our motivation for this project came from datasets of developing asicidian embryos, as can be seem on the picture above. Thanks to the morphonet dependency (https://morphonet.org/help_api), most image formats are supported (inr, tif, etc.).

### LMG Parameters ###

In the file "run_jobs.py":

* Enter the folder or folders of your imaging data by setting the variables "root_folder" and "folders".
* Set the variable "cell_surfaces" to determine whether the meshes should be generated at the cellular (segmented objects) or embryonic (whole data) level. If cell_surfaces = True, the meshes will be generated at the cellular level. If false, the meshes will be generated at the embryonic level. 
* Set the variable "subdivisions". Initial meshes are obtained by succevise "butterfly" subdivisions of an icosahedron. The variable "subdivisions" indirectly sets the number of vertices of the mesh by determining the number of subdivisions. The following relation holds: if subdivisions = N, number of vertices = 10*4^N + 2 (e.g, N = {0,1,2,3,4,5,...}, Number of vertices = {12,42,162,642,2562,10242,...})

### Run LMG ###
On the terminal, run the following command:

	python run_jobs.py

This command runs the lagrangian mesh code, computes lagrangian mesh associated with the input image files and stores in the .obj format in the obj folder.

### Further uses ###
Having computed lagrangian meshes, further analysis can be carried on the meshes by computing for example kinematic fields. The code in "strainrate.py" computes the strain rate tensor field associate the dynamics of the computed evolving mesh. These quantities can be rendered on the mesh using available tools like paraview, or custom code. Here is a renderer of a scalar field derived from the strain rate tensor on the evolving mesh of developing ascidian embryos.

![Alt text](https://github.com/guijoe/lmg/blob/main/img/asc_dev.png "Ascidian embryos")
	
### Further reading ###

This work was carried out as part of the following publication

	Dokmegang, Joel, Emmanuel Faure, Patrick Lemaire, Ed Munro, and Madhav Mani. "Spectral decomposition unlocks ascidian morphogenesis." bioRxiv (2023): 2023-08.

The data used was first published

	Guignard, Léo, Ulla-Maj Fiúza, Bruno Leggio, Julien Laussu, Emmanuel Faure, Gaël Michelin, Kilian Biasuz et al. "Contact area–dependent cell communication and the morphological invariance of ascidian embryogenesis." Science 369, no. 6500 (2020): eaar5663.