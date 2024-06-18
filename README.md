# README #

Hello world! Welcome to LMG "Lagrangian Meshes Generator", a python-based image processing tool able to generate dynamic geometric meshes from time-lapse images of continuous processes. 

![Alt text](https://github.com/guijoe/MGSharpCore/blob/master/images/Invagination.GIF "Invagination")

### Brief Description ###

* By "Lagrangian", we mean that the generated mesh vertices behave as Lagrangian points that can be tracked between consecutive time points.  
* Hence, the positions of these vertices, connected by a fixed network, can be used to compute all sorts of quantitative indicators, including continuum fields such as velocity, strain, strain-rate, etc. suitable for an in-depth study of the processes at play in the movies.
* The process of interest could cover a wide range of scenarii, basically, anything that can be store as a time-lapse movie of voxel. Our motivation for this project came from datasets of developing asicidian embryos, as can be seem on the picture above. Thanks to the morphonet dependency (https://morphonet.org/help_api), most image formats are supported (inr, tif, etc.).

### Running a simulation with MG# ###

* MG#Core can be used with any leading PC Operation Systems (Windows, Linux, Mac OS) thanks to the cross-platform abilities of .NET.
* Building simulations with MG# requires installing .NET Core SDK (https://dotnet.microsoft.com/download). Windows users may also make use of the native .NET framework.
* A simulation can only be runned from a "Main" code file (file with the "Main" function). The "Main" file must be compiled, and the resulting executable file runned. This goes without saying that the path to the file must be referenced, either by being in its parent directory or by explicitly specifying it in the file path.
    
#### Windows
	dotnet build
	dotnet run
	
#### Linux 
	dotnet build
	dotnet run
	
#### Mac OS 
	dotnet build
	dotnet run

### Designing and programming a simulation ###

* Programming a new simulation is as simple as creating a new class inheriting from the Simulator class. The tutorial presented throughout this text describes the code that produces the Invagination simulation showcased above.

![Alt text](https://github.com/guijoe/MGSharpCore/blob/master/images/Invagination.PNG "Set Model")
	
* Any class inheriting from Simulator must override its Abstract methods, which are mandatory. The following code adds these methods to our new class, including the Main method, to make this class runnable.

![Alt text](https://github.com/guijoe/MGSharpCore/blob/master/images/Methods.PNG "Methods")