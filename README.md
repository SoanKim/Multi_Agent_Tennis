# Multi-Agent Environment: Collaboration and Competition

### The Environment
This project is based on the Tennis Environment. The project environment is similar to, but not identical to the Tennis environment on the [Unity ML-Agents GitHub page.](https://github.com/Unity-Technologies/ml-agents/blob/main/docs/Learning-Environment-Examples.md#tennis)</br>

<img src="https://user-images.githubusercontent.com/10624937/42135623-e770e354-7d12-11e8-998d-29fc74429ca2.gif">

In this environment, two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.</br>

The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation. Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.</br>

The task is episodic, and in order to solve the environment, your agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents). Specifically,</br>

* After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 2 (potentially different) scores. We then take the maximum of these 2 scores.</br>
* This yields a single score for each episode.</br>
The environment is considered solved, when the average (over 100 episodes) of those scores is at least +0.5.</br>

### Step 1: Activate the Environment</br>
If you haven't already, please follow the instructions in the [DRLND GitHub repository](https://github.com/udacity/deep-reinforcement-learning#dependencies) to set up your Python environment. These instructions can be found in ``README.md`` at the root of the repository. By following these instructions, you will install PyTorch, the ML-Agents toolkit, and a few more Python packages required to complete the project.</br>

(For Windows users) The ML-Agents toolkit supports Windows 10. While it might be possible to run the ML-Agents toolkit using other versions of Windows, it has not been tested on other versions. Furthermore, the ML-Agents toolkit has not been tested on a Windows VM such as Bootcamp or Parallels.</br>

* SPECIAL NOTE TO BETA TESTERS - please also download the ``p3_collab-compet`` folder from here and place it in the DRLND GitHub repository.</br>

### Step 2: Download the Unity Environment</br>
For this project, you will not need to install Unity - this is because we have already built the environment for you, and you can download it from one of the links below. You need only select the environment that matches your operating system:</br>

Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)</br>
Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)</br>
Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)</br>
Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)</br>
Then, place the file in the p3_collab-compet/ folder in the DRLND GitHub repository, and unzip (or decompress) the file.</br>

(For Windows users) Check out this [link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.</br>

(For AWS) If you'd like to train the agent on AWS (and have not enabled a [virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use this [link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux_NoVis.zip) to obtain the "headless" version of the environment. You will not be able to watch the agent without enabling a virtual screen, but you will be able to train the agent. (To watch the agent, you should follow the instructions to enable a virtual screen, and then download the environment for the Linux operating system above.)</br>

### Requirements
tensorflow==1.7.1<br/>
Pillow>=4.2.1<br/>
matplotlib<br/>
numpy>=1.11.0<br/>
jupyter<br/>
pytest>=3.2.2<br/>
docopt<br/>
pyyaml<br/>
protobuf==3.5.2<br/>
grpcio==1.11.0<br/>
torch==0.4.0<br/>
pandas<br/>
scipy<br/>
ipykernel<br/>

### Step 3: Explore the Environment</br>
After you have followed the instructions above, open Tennis.ipynb (located in the p3_collab-compet/ folder in the DRLND GitHub repository) and follow the instructions to learn how to use the Python API to control the agent.</br>

### The Repository Structure
* ``Tennis.ipynb`` - Includes the environment, agent, model, and main functions.<br/>
* ``Report.md`` - Includes hyperparameters, code implementation and future work.<br/>
* ``result.png`` - Shows the cumulative rewards after training.<br/>
* ``actor_checkpoint.pth`` - Contains the parameters of the local network of the actor.<br/>
* ``critic_checkpoint.pth`` - Contains the parameters of the local network of the critic.<br/>
