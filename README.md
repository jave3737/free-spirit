# free-spirit

## Requirements
* ubuntu
* docker

## How to build
* add the following alias to the bashrc

```bash
alias runzephyr="docker run --rm -it --name=test zephyr:1.0"
alias buildzephyr="docker build --tag zephyr:1.0 ."
```

* run `buildzephyr` to build the docker image
* run `runzephyr` to enter the container

### build blinky project
* run the following 

```bash
cd ~/zephyrproject/zephyr
west build -p auto -b nrf5340pdk_nrf5340_cpuapp samples/basic/blinky
west build -p auto -b nrf5340pdk_nrf5340_cpunet samples/basic/blinky
```
