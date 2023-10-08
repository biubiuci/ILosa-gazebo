# ILosa-gazebo

## What is ILoSA? 

教机器人如何根据我们的偏好施加力仍然是一个悬而未决的挑战，必须从多个工程角度来解决。
ILoSA是一个使机器人能够学习可变阻抗策略的框架，其中笛卡尔刚度和吸引子都可以通过用户友好的界面从人类演示和校正中学习。这些策略是在高斯过程的帮助下学习的，利用高斯过程的特性来识别不确定性区域，并允许交互式校正、刚度调制和主动扰动抑制。
学习过程包括两个步骤：
1.动觉演示-人类引导机器人完成所需的动作，以及
2.纠正阶段-在该阶段，人员可以对最初演示的策略进行局部调整，以提高任务执行期间的性能。
ILoSA已被证明在不同的挑战性任务中是有效的，例如推箱子、擦木板，以及从插座上插拔插头。只需一次演示，然后进行短时间的纠正，就可以实现良好的任务执行。低时间需求加上直观的校正界面，进一步使ILoSA可供可能不是机器人专家的人使用。以下[视频](https://www.youtube.com/watch?v=MAG-kFGztws）提供了ILoSA功能的概述。
有了这一点，我们邀请大家自己尝试ILoSA，将其扩展到其他任务中，不仅对机器人，甚至对人类都有挑战，并继续推动机器人学习的能力。
### Interested also in learning and controlling the end-effector orientation? Then read: 
# How to run the code on a Franka Emika Panda gazebo
To install:
- Create a workspace containing a src directory.
- Inside the src directory, clone the franka_ros repository by frankaemika.
```git clone https://github.com/frankaemika/franka_ros ```
- Inside the repository, clone the human friendly controllers of TU Delft https:```//github.com/franzesegiovanni/franka_human_friendly_controllers```
- Return to the workspace main directory (cd ../..).
- Source your version of ROS (e.g. ```source /opt/ros/melodic/setup.bash```).
- Build the project, calling: ```catkin_make -DMAKE_BUILD_TYPE=Release -DFranka_DIR:PATH=/path/to/libfranka/build``` (be sure that libfranka is installed https://frankaemika.github.io/docs/installation_linux.html)
To run ILoSA_gazebo:
- Switch on your Panda robot (make sure the gripper is initialized correctly), unlock its joints, and activate the FCI if necessary.
- Open a terminal and be sure that the ros of the new catkin workspace is sourced, i.e. ```source devel/setup.bash```
- 第一次运行它时，请使用 来设置 Gazebo 在文件夹ILosa/src/franka_human_friendly_controllers里执行python3 setup_gazebo.py。
再次编译：  catkin_make -DMAKE_BUILD_TYPE=Release -DFranka_DIR:PATH=~/libfranka/build.

在仿真中使用笛卡尔阻抗控制器：

roslaunch franka_gazebo panda.launch x:=-0.5 world:=$(rospack find franka_gazebo)/world/stone.sdf controller:=cartesian_variable_impedance_controller rviz:=true

要杀死凉亭，请运行： killall -9 gazebo & killall -9 gzserver  & killall -9 gzclient
- ```在ILosa-main运行```
- ``` python3 main.py```



```

  
