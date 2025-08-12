# Duckievillage

![Duckievillage](https://raw.githubusercontent.com/RenatoGeh/duckievillage/master/duckieusp.png)

Duckievillage is an adaptation of [Duckietown](https://duckietown.org)'s OpenAI Gym
[gym-duckietown](https://github.com/duckietown/gym-duckietown) for the undergraduate level [Intro
to Robotics](https://uspdigital.usp.br/jupiterweb/obterDisciplina?sgldis=MAC0318&nomdis=) (MAC0318)
course held at the [Institute of Mathematics and Statistics](http://www.ime.usp.br/) (IME) of the
[University of São Paulo](https://www5.usp.br/#english) (USP).

This project is not to be thought of as a fork or standalone project, but as a complement to
Duckietown's Gym. To be more precise, Duckievillage's objectives are two-fold: to be an environment
wrapper around `DuckietownEnv`, which allows a more custom-made environment for our own robotics
course; and to be used as course walkthrough.

---

## Installation

It is **highly recommended** that you use a python environment, for example:

```bash
cd
virtualenv duckievillage
```

To activate this environment, do

`source ~/.venv/duckievillage/bin/activate`


You will need to activate this environment every time you use this package. 

Clone (the patched version of) `gym-duckietown` inside `duckievillage`'s folder:

```bash
cd ~/duckievillage
git clone https://github.com/denismaua/gym-duckietown.git duckietown

``` 

Install Duckieotwns's dependencies (this might take a while):

`cd duckietown && pip3 install -e .`


Now clone the assignments:

```bash
cd ..
git clone git@github.com:denismaua/duckievillage-assignments.git assignments
```

---

## Testing

Cd to the folder where this file is locate and activate you environment (if not already acrivated):

```bash
cd ~/duckievillage
source bin/activate
```

Test your setup with:

```bash
python3 assignments/manual/manual.py
```

This should open the simulator graphical interface and run the code for the first assignment.
See [assignments/manual/README.md] for instructions on how to modify the file `manual.py` to make your own manually controlled simulated duckiebot!

If you get an error, trying restarting your computer. If the error persists see the [FAQ](#troubleshooting) section below.

## Uninstallation

To uninstall, simply run `uninstall.sh` with the same shell you used for installing Duckievillage
and follow instructions.

---

## Updating Duckievillage

Before running Duckievillage, make sure you have the latest version by running `update.sh`:

```
zsh update.sh
```

This will update Duckievillage, Duckietown and assignments.

---

## Troubleshooting

1. Something goes wrong involving gym-duckietown

> You might have a different version of gym-duckietown installed or Python is simply not finding the proper path.
> Try adding this installation to the PATH:
> `echo "export PYTHONPATH=\"\${PYTHONPATH}:$(pwd)/duckievillage/duckietown/src\"" >> ~/.bashrc`
> Resource your rcfile with `source ~/.bashrc` and reactivate the environment `source ~/duckievillage/bin/activate`

2. I get a permission denied when trying to clone from within a WSL shell!

> You should clone from a WSL partition, and not from your Windows NTFS. Do `cd ~` and retry.

4. `ModuleNotFoundError: No module named 'duckievillage'`

> You have to `cd` to the Duckievillage root directory (i.e. the directory you cloned). If the
> error persists, try either closing your shell session and opening another one (don't forget to
> `cd` to the Duckievillage root directory and activate your environment), or sourcing
> your rcfile.

5. `ModuleNotFoundError: No module named 'zuper_commons'`

> You have to activate the Duckietown environment.


6. `pyglet.gl.ContextException: Could not create GL context`

> This might either be a VM issue or a Pyglet version issue. VMs are not supported in
> Duckievillage. If it's Pyglet, you may want to either try updating the Anaconda environment with
> the latest python and packages; or alternatively ditch Anaconda and install everything with
> `pip`. For the latter, you might want to completely remove Anaconda so Python doesn't get
> confused with package versions (or at least completely isolate Anaconda from another Python
> environment. See the [pip alternative](#alternative-pip-installation) instructions. Wayland might
> also cause this problem. Consider using a Xorg backend for your Desktop Environment or Window
> Manager instead.

