# Humanoid Robot Gait - Reinforcement Learing

Github link for all files

https://github.com/zahirmahammad/690_humanoid.git 


### Libraries used
1. OpenAI Gymnasium - https://gymnasium.farama.org/environments/mujoco/humanoid/
2. Stablebaselines3 - https://stable-baselines3.readthedocs.io/en/master/guide/install.html
3. Google BRAX - https://github.com/google/brax

## Installation
Gymnasium
```
pip install gymnasium
pip install stable-baselines3[extra]
```
Brax
```
pip install -U "jax[cpu]"       # for CPU
pip install -U "jax[cuda12]"    # for GPU training
pip install brax
````

## Simulations

1. Humanoid - OpenAI Gymnasium

2. Stompy Humanoid - OpenAI Gymnasium

3. Humanoid - Brax, Mujoco MJX

4. Stompy Humanoid - Brax, Mujoco MJX

### System Requirements
------------------------
Open AI Gymnasium
- CPU/GPU

Brax, Mujoco MJX : _GPU Required_

- Given: Cloud / NVIDIA RTX - 16GB
- Ours - NVIDIA RTX 4070 - 8GB

-------------------------
### Humanoid - OpenAI Gymnasium
To train Humanoid of Gymnasium

    python train_humanoid.py
To test Humanoid of Gymnasium

    python test_humanoid.py


---------------------------
### Stompy Humanoid - OpenAI Gymnsaium
$PATH1 = /home/zahir/.local/lib/python3.10/site-packages/gymnasium/envs/mujoco/assets
$PATH2 = /home/zahir/.local/lib/python3.10/site-packages/gymnasium/envs/mujoco

Copy paste stompy.xml and /meshes2 folder in this "$PATH1"

Copy paste Humanoid_Kscale.py in this "$PATH2"

Add these lines in ___init___.py file
```
# KScale
register(
    id="Humanoid-Kscale",
    entry_point="gymnasium.envs.mujoco.humanoid_kscale:HumanoidKscaleEnv",
    max_episode_steps=1000,
)
```

To train stompy Humanoid

    python train_stompy.py

To test stompy Humanoid [saved model is not accurate]

    python test_stompy.py

-----------------------------
### Humanoid - Brax, Mujoco MJX
Run each cell in _humanoid.ipynb_


-------------------------------
### Stompy Humanoid - Mujoco MJX
Copy Paste stompy.xml and meshes.py folder in the "$PATH"

Run each cell in _stompy_humanoid.ipynb_

## Run through Docker
Follow the commands to build and create a new container - required - 12.7GB
```
xhost +

docker build --no-cache -t humanoid_docker -f humanoid_docker .

docker run --rm --privileged --net=host -it -v /tmp/.X11-unix:/tmp/.X11-unix --gpus all --env="DISPLAY" --device=/dev/video0:/dev/video0 --name humanoid_container humanoid_docker
```


Open docker image from VSCode and open the folder /690_humanoid

Open and run the files
- humanoid.ipynb
- stompy_humanoid.ipynb