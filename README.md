# Getting Started
* Clone the project to a directory `~/projects/`

* Add the following aliases to the .profile or .bashrc

```bash
alias buildzephyr="docker build --tag zephyr:1.0 ."
alias runzephyr="docker run -it --mount src=~/projects/free-spirit,target=/root/app,type=bind --rm zephyr:1.0"
```

* Build the docker image

```bash
cd ~/projects/free-spirit/docker_files/
buildzephyr
```

* Enter the container

```bash
runzephyr
```
 
* Build the application

```bash
west build -b reel_board
```
