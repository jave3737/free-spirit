# Requirements
* ubuntu
* docker

# How to build
* add the following alias to the bashrc

```bash
alias runzephyr="docker run -v $(pwd):/root/application --rm -it --name=test zephyr:1.0"
alias buildzephyr="docker build --tag zephyr:1.0 ."
```

* run `buildzephyr` to build the docker image
* run `runzephyr` to enter the container
 
# Build blinky project
* run the following 

```bash
cd ~/zephyrproject/zephyr
west build -p auto -b nrf5340pdk_nrf5340_cpuapp samples/basic/blinky
```
