## This is a little annoying to do from Julia. There's almost certainly a better way to do it.

### Add Julia packages: Conda, PyCall, PyPlot

* From the Anaconda navigator (the annoying GUI thing), find the Conda environment that Julia created (probably during IJulia installation).
It should be called somethign like "usr". 

* Activate the "usr" environment 

* Using pip (from a console or possibly from within the navigator), install holodeck:
  * pip install holodeck
  
When this is done, you can import holodeck from Julia:

* using PyCall
* @pyimport holodeck

* env = holodeck.make("UrbanCity") (or whatever environment you wanna use)

### Read holodeck's [documentation](https://github.com/BYU-PCCL/holodeck)

* The difference in Julia is that "env" etc. don't have python-style fields (eg. env.step(action)).
In Julia you'd use e.g. env[:step](action), env[:action_space], etc

* E.g. state, reward, terminal, info = env[:step](action)

The sensor data are returned in "state". In this example, I believe the camera output is the 4th field:

Image = state[4] (returns a 256x256x4 image)

etc.
