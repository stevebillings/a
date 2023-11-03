# Steve Billings: some example code

This page contains links to examples of (open source) code I've written in:

* [Current project (TypeScript on Node.js, and Python on Django)](#node)
* [Java on Spring Boot](#java)
* [C++ (robotics)](#cpp)

<a name="node"></a>
## Current project (TypeScript on Node.js, and Python on Django)

I am currently working on a web application ([trackyourweek.com](https://trackyourweek.com)) that enables users to track progress relative to their goals for virtual any fitness-related activity (running, cycling, lifting, etc.). 

### Web application (Typescript on Node.js)

The main web application is written in TypeScript, HTML, CSS, and EJS on Node.js, Express.js, and Passport.js (for OAuth 2.0 authentication). (I've temporarily made the github repo for the main web app private while I
port it to the (relatively new) data service described below; I'll make it public again once that work is complete.)

<a name="dataservice"></a>
### Data service (Python on DJango and Django REST framework)

The [data service](https://github.com/stevebillings/activitytrackerdataapi) is written in Python on Django and Django REST framework, and is accessed by the main web application
via a RESTful API. The database is MySQL.

I am currently building out the capabilities of the data service, and migrating the main web application to it (and away from its original direct database access)
as the capabilities of the data service allow.

### Cloud platform

The Node.js web application and the Django data service run in separate containers that are deployed to AWS.
Deployment is automated using the AWS CLI.
(The MySQL database is also hosted on AWS.)

### Development status

So far I have been, and continue to be, focused on back end functionality. As a result, [trackyourweek.com](https://trackyourweek.com) about the ugliest web application on the internet. 
But the functionality has reached the point where it is useful, at least to me. 
Feel free to sign in and give it a try if you're interested.

URL: [https://trackyourweek.com](https://trackyourweek.com)

Source repos:
* Web application: [https://github.com/stevebillings/workouttracker.git](https://github.com/stevebillings/workouttracker.git)
* Data service: [https://github.com/stevebillings/activitytrackerdataservice](https://github.com/stevebillings/activitytrackerdataservice)

<a name="java"></a>
## Java on Spring Boot

My primary language for professional use for most of the last 15 years has been Java, and most of that work has used Spring Boot. 

Most of the code I worked on while at Synopsys was written in Java on Spring Boot, and much of it is open source in github. Here are some examples of that work.

### New code

For a look at some code for which I was the primary developer:

1. git clone https://github.com/blackducksoftware/synopsys-detect.git
1. cd synopsys-detect
1. git checkout 8.0.0
1. cd detectable/src/main/java/com/synopsys/integration/detectable/detectables/bazel/

The bazel package contains the code for a Synopsys Detect ["detector"](https://community.synopsys.com/s/document-item?bundleId=integrations-detect&topicId=gettingstarted/terms/detectors.html) (in this case: the [Bazel Detector](https://community.synopsys.com/s/document-item?bundleId=integrations-detect&topicId=packagemgrs/bazel.html)). While everything we did was a team effort, I was responsible for the design, developed the initial version of it, and, as of Detect 8.0.0, had done most of the work on this code.

#### Background

The Bazel detector’s job is to discover dependencies for any of several software project types that use the [Bazel](https://bazel.build/) build tool. Depending on the project type, the detector would run a sequence of steps that included running Bazel commands, parsing the output, using elements of that output as arguments in subsequent Bazel commands, etc. This sequence of steps eventually results in a graph representing the project’s dependencies, that Detect would feed into the [Black Duck SCA system](https://www.synopsys.com/software-integrity/security-testing/software-composition-analysis.html) via Black Duck's REST APIs. The Bazel detector design is based on a set of “pipelines” (think unix pipes; see class Pipelines). It has one pipeline per project type. Each pipeline combines a set of general-purpose steps (see the classes in package bazel.pipeline.step) in a sequence. Examples of steps include: execute command, filter, split, de-dup, replace, parse, etc. This approach greatly reduced the amount of code required to support all of the required project types, and greatly reduced the incremental effort required to add support for a new project type.

### Enhanced code

This [pull request](https://github.com/blackducksoftware/synopsys-detect/pull/516) shows a pretty typical change to a detector (in this case: the [BitBake Detector](https://community.synopsys.com/s/document-item?bundleId=integrations-detect&topicId=packagemgrs/bitbake.html)). It includes new code (and tests) that I wrote, changes I made to existing code, and team interaction during code review.

#### Background

The BitBake Detector discovers dependencies in [BitBake](https://docs.yoctoproject.org/1.6/bitbake-user-manual/bitbake-user-manual.html) projects.
It does this by executing a BitBake command, parsing the output, executing another BitBake command using information parsed from the output of the previous command, etc. This sequence of steps eventually results in a graph representing the project’s dependencies, that Detect would feed into the [Black Duck SCA system](https://www.synopsys.com/software-integrity/security-testing/software-composition-analysis.html) via Black Duck's REST APIs. Unlike the Bazel detector, the BitBake detector only supports a single project type, so has no need for a pipeline approach.

<a name="cpp"></a>
## C++ / Robot Software

Since late 2021 I have been developing robot software in my spare time, primarily in C++. One of my objectives in this has been to learn C++. I think robots are a lot of fun so robotics provides an interesting sandbox for learning a new language. For a look at some of my recent C++ code:

1. git clone https://github.com/stevebillings/wanderbot.git
1. cd wanderbot

The [README](https://github.com/stevebillings/wanderbot#readme) contains a brief description of the software.

Videos of the code running in simulation:

1. A video that emphasizes the navigation algorithm (Virtual Force Field) being used to navigate a simple environment is [here](https://drive.google.com/file/d/109PchHxjqMuJjDrc6-UHcsy3-8Mow3KA/view?usp=sharing).
2. A video that shows the robot (FSM) changing state to recover from being stuck in a corner is [here](https://drive.google.com/file/d/1a-lXPeDvVW8w1gOMR2BIlpd47dWaV_UQ/view?usp=sharing).

### History

A brief history of my explorations into software for robots:

* Early in my career I did some robotics work following an approach that I believe was typical at the time: C or assembly code running on a simple cyclic executive (essentially bare metal).
* When I started playing around in robotics around the end of 2021, I assembled from cheap parts a simple wheeled robot with a ping sensor driven by C++ code running on an on-board arduino board (very reminiscent my early robotics work, and very primitive compared to the approach used in modern robots). The (very cheap) ping sensor produces a lot of false positives, which I never bothered to address in the software because by that time I was intrigued by the next project (a robot built using ROS 2). A video of this (very crude) robot is [here](https://drive.google.com/file/d/1mEP5RhqieAe89wksvIwAjcLRTK1Uh4p-/view?usp=sharing).
* Fall of 2022, I shifted my attention to robot software built on the Robot Operating System 2 (ROS 2), and started developing software for a wheeled robot (only simulated at this point) running ROS 2. I developed a bunch of early ROS 2 experiments in my ros2overlays repo. From that I extracted some (still primitive) navigating robot code and created the loiterbot repo. As my thinking evolved regarding the robot I wanted to create, and my navigation algorithm became more sophisticated (using Vector Force Field), I eventually moved the code to the more appropriately named [wanderbot](https://github.com/stevebillings/wanderbot) repo (video [here](https://drive.google.com/file/d/109PchHxjqMuJjDrc6-UHcsy3-8Mow3KA/view?usp=sharing)).
