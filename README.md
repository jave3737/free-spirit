# Requirements
* ubuntu
* docker

# How to build
* add the following alias to the bashrc

```bash
alias runzephyr="docker run -v $(pwd):/root/app --rm -it zephyr:1.0"
alias buildzephyr="docker build --tag zephyr:1.0 ."
```

* run `buildzephyr` to build the docker image
* run `runzephyr` to enter the container
 
# Build blinky project
* run the following 

```bash
cd ~/app
west build -b reel_board
```
