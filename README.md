# Steve Billings: some example code

## Java

My primary langage for professional use for the last 15 years has been Java. Here's an example of some code for which I was the primary developer:

1. git clone https://github.com/blackducksoftware/synopsys-detect.git
1. cd synopsys-detect
2. git checkout 8.0.0

Under detectable/src/main/java/com/synopsys/integration/detectable/detectables/bazel/ is the code for a Synopsys Detect [detector](https://community.synopsys.com/s/document-item?bundleId=integrations-detect&topicId=components/detectors.html&_LANG=enus) (the [Bazel Detector](https://community.synopsys.com/s/document-item?bundleId=integrations-detect&topicId=packagemgrs/bazel.html&_LANG=enus)) for which I was the primary developer.

## C++ / Robotics

For the last year+ I have been developing robotic software in my spare time using C++. It took a while to develop my C++ skills to the point I could develop reasonably good code, but this code is getting to the point where I'm starting to feel pretty good about it:

1. git clone https://github.com/stevebillings/wanderbot.git
1. cd wanderbot

The [README](https://github.com/stevebillings/wanderbot#readme) contains a brief description of the code design.

At some point (hopefully soon) I'll post a video here of the robot in action.

A brief history of my explorations into robotics:

* Early in my career I did some robotics using what I believe was pretty standard at the time: C or assembly code running on a simple cyclic executive (essentially bare metal).
* When my interest in robotics revived about a year ago, I assembled from cheap parts a simple wheeled robot with a ping sensor and an arduino-based C++ controller (very reminiscent my early robotics work, and laughably primitive compared to how modern robots are developed).
* After learning more about how modern robots are developed, I shifted my attention to Robotic Operating System 2 (ROS 2), and started developing wheeled robots (only simulated at this point) on ROS 2. I developed a bunch of early ROS 2 experiments in my ros2overlays repo. From that I extracted some (still primitive) navigating robot code and created the loiterbot repo. As my thinking on the robot I wanted to create changed, and my navigation algorithm became more sophisticated (using Vector Force Field), I eventually moved the code to the more appropriately named wanderbot repo.
