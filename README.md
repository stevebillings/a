# Steve Billings: some example code

## Java

My primary langage for professional use for the last 15 years has been Java. Most of the code I worked on while at Synopsys is open source in github. For a look at some code for which I was the primary developer:

1. git clone https://github.com/blackducksoftware/synopsys-detect.git
1. cd synopsys-detect
1. git checkout 8.0.0
1. cd detectable/src/main/java/com/synopsys/integration/detectable/detectables/bazel/

The bazel directory contains the code for a Synopsys Detect ["detector"](https://community.synopsys.com/s/document-item?bundleId=integrations-detect&topicId=gettingstarted/terms/detectors.html) (in this case: the [Bazel Detector](https://community.synopsys.com/s/document-item?bundleId=integrations-detect&topicId=packagemgrs/bazel.html)). While everything we did was a team effort, as of Detect 8.0.0 I had done most of the work on this code.

## C++

Since late 2021 I have been developing robot software in my spare time using C++. My primary objective in this has been to learn C++; robotics provides an interesting practice field for it. For a look at some recent code that I feel best represents my current C++ abilities:

1. git clone https://github.com/stevebillings/wanderbot.git
1. cd wanderbot

The [README](https://github.com/stevebillings/wanderbot#readme) contains a brief description of the software design.

At some point I'll post a video here of the robot in action.

A brief history of my explorations into software for robots:

* Early in my career I did some robotics work following an approach that I believe was typical at the time: C or assembly code running on a simple cyclic executive (essentially bare metal).
* When I started playing around in robotics around the end of 2021, I assembled from cheap parts a simple wheeled robot with a ping sensor driven by C++ code running on an on-board arduino board (very reminiscent my early robotics work, and very primitive compared to the approach used in modern robots).
* Fall of 2022, I shifted my attention to robot software built on the Robot Operating System 2 (ROS 2), and started developing software for a wheeled robot (only simulated at this point) running ROS 2. I developed a bunch of early ROS 2 experiments in my ros2overlays repo. From that I extracted some (still primitive) navigating robot code and created the loiterbot repo. As my thinking evolved regarding the robot I wanted to create, and my navigation algorithm became more sophisticated (using Vector Force Field), I eventually moved the code to the more appropriately named [wanderbot](https://github.com/stevebillings/wanderbot) repo.
