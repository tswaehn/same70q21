
## create zephyr environment with west for specific version in .venv

this installation is globally for the user and can be used for other projects as well

in this example we create zephyr `3.6.0`

```
mkdir -p ~/.local/zephyrproject-3.6.0
cd  ~/.local/zephyrproject-3.6.0

python3 -m venv .venv
source .venv/bin/activate

pip install west

west init --mr v3.6.0

west update

west zephyr-export

pip3 install -r zephyr/scripts/requirements.txt
```

## install sdk

this installation is globally for the user and can be used for other projects as well

depending on zephyr version we download the sdk

| zephyr | sdk      | link                                                                                                             |
|--------|----------|------------------------------------------------------------------------------------------------------------------|
| 2.7.0  | 0.15.2   |                                                                                                                  |
| 3.0.0  | 0.16.1   | https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v0.16.1/zephyr-sdk-0.16.1_linux-x86_64.tar.xz     |
| 3.5.0  | 0.16.4   | https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v0.16.4/zephyr-sdk-0.16.4_linux-x86_64.tar.xz     |
| 3.6.0  | 0.16.5-1 | https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v0.16.5-1/zephyr-sdk-0.16.5-1_linux-x86_64.tar.xz |

```
cd ~/.local

wget https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v0.16.5-1/zephyr-sdk-0.16.5-1_linux-x86_64.tar.xz

tar xvf zephyr-sdk-0.16.5-1_linux-x86_64.tar.xz

cd zephyr-sdk-0.16.5-1

./setup.sh -c -h -t all
```



## build with zephyr

go to the project folder

```
cd ~/src/my-zephyr-project
```

compare the CMakeLists.txt folder settings for
* `ZEPHYR_BASE`
* `ZEPHYR_SDK_INSTALL_DIR`


finally build

```
mkdir build
cd build
cmake ..
cmake --build .
```
