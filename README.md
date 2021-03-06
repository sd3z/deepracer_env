# Deep Racer Env

This repository contains a simulator for AWS Deep Racer. At this point all of the constants are just my personal guessing. It runs using shapely, pyOpenGL, pygame, and gym, and it currently must create a window to run.

### Training with PPO

0 epochs

![](gifs/0.gif)

25 epochs

![](gifs/25.gif)

```python
import gym
import gym_deepracer
import time

env = gym.make('deepracer-v0')   # starts as 1000x600
env.resize(128,128) # resize to 128x128 for learning

camera_view = env.reset()
for _ in range(1000):
    throttle = 1 # accelerate at 1 m/s^2
    turn = 15    # turn wheels 15 degrees
    action = (throttle, turn)
    sensors, reward, done, _ = env.step(action)
    time.sleep(1/25) # run at 25fps
env.quit()
```
