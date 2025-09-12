## Install MuJoCo

```console
cd ~
wget https://mujoco.org/download/mujoco210-linux-x86_64.tar.gz
mkdir $HOME/.mujoco
tar -xvf mujoco210-linux-x86_64.tar.gz -C ~/.mujoco/
echo -e 'export LD_LIBRARY_PATH=$HOME/.mujoco/mujoco210/bin' >> ~/.bashrc
echo -e 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/nvidia' >> ~/.bashrc
echo -e 'export PATH="$LD_LIBRARY_PATH:$PATH"' >> ~/.bashrc
```
For visualizing mujoco in a GUI viewer:
```console
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libGLEW.so
```

## User-customized PATH for PKUfudawei:

Before running only needs
```console
export LD_LIBRARY_PATH=$CONDA_PREFIX/lib:$HOME/.mujoco/mujoco210/bin:/usr/lib/nvidia:$LD_LIBRARY_PATH
```

For automatication, config `$CONDA_PREFIX/etc/conda/activate.d/env_vars.sh`:
```bash
# $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh
export OLD_LD_LIBRARY_PATH=$LD_LIBRARY_PATH
export LD_LIBRARY_PATH=$CONDA_PREFIX/lib:$HOME/.mujoco/mujoco210/bin:/usr/lib/nvidia:$LD_LIBRARY_PATH
```
and `$CONDA_PREFIX/etc/conda/deactivate.d/env_vars.sh`:
```bash
# $CONDA_PREFIX/etc/conda/deactivate.d/env_vars.sh
export LD_LIBRARY_PATH=$OLD_LD_LIBRARY_PATH
unset OLD_LD_LIBRARY_PATH
```
