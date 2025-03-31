# Steve Billings: some example projects

This page describes a few relatively recent and representative projects I have worked on, including (where possible) links to source code:

* [Python AI application](#rag)
* [Full stack web application (Typescript on React and Python on Django)](#haystack)
* [Java on Spring Boot](#java)
* [C++ (robotics)](#cpp)

<a name="rag"></a>
## Python AI application

For fun (and to learn about developing AI applications) I am currently developing a AI chatbot creation platform, written in Python, that enables a user to quickly configure new Retrieval-Augmented Generation (RAG) LLM chatbots, without writing code.

Source code and a more thorough description can be found at: ["https://github.com/stevebillings/simple-rag-apps"](https://github.com/stevebillings/simple-rag-apps)

<a name="haystack"></a>
## Full stack (Typescript on React and Python on Django) web application

For work, I am currently the sole architect / designer / developer of Haystack’s customer portal / data management platform for complex user and lab workflows. It is a web application comprised of a Python/Django backend accessed via a level 3 (HATEOAS) REST API, and Typescript/React/Next.js frontend. 

Both the frontend and the backend deploy automatically to containers on AWS using Github Actions (building toward a CI/CD approach).

It is architected following Domain Driven Design. It utilizes Hexagonal (ports and adapters) architecture with Repository and Unit of Work patterns to keep the business logic (the majority of the code) free from dependencies on the Django framework.

The REST API endpoints and request handlers are (and the API documentation will soon be) generated automatically from a single API specification (a JSON document).

A publish-subscribe messaging component enables asynchronous responses to events (such as persisting important events to a log in the database).

<a name="java"></a>
## Java on Spring Boot

My primary language for professional use for about 15 years was Java, and most of that work has used Spring Boot. 

Most of the code I worked on while at Synopsys was written in Java on Spring Boot, and much of it is open source in github. Here are some examples of that work.

### New code

For a look at some code for which I was the primary developer:

1. git clone https://github.com/blackducksoftware/synopsys-detect.git
1. cd synopsys-detect
1. git checkout 8.0.0
1. cd detectable/src/main/java/com/synopsys/integration/detectable/detectables/bazel/

The bazel package contains the Synopsys Detect code that provided support for Bazel projects (see ["Bazel support"](https://documentation.blackduck.com/bundle/detect/page/packagemgrs/bazel.html). While everything we did was a team effort, I was responsible for the design, developed the initial version of it, and, as of Detect 8.0.0, had done the majority of the work on this code.

#### Background

The Bazel detector’s job is to discover dependencies for any of several software project types that use the [Bazel](https://bazel.build/) build tool. Depending on the project type, the detector would run a sequence of steps that included running Bazel commands, parsing the output, using elements of that output as arguments in subsequent Bazel commands, etc. This sequence of steps eventually results in a graph representing the project’s dependencies, that Detect would feed into the [Black Duck SCA system](https://www.synopsys.com/software-integrity/security-testing/software-composition-analysis.html) via Black Duck's REST APIs. The Bazel detector design is based on a set of “pipelines” (think unix pipes; see class Pipelines). It has one pipeline per project type. Each pipeline combines a set of general-purpose steps (see the classes in package bazel.pipeline.step) in a sequence. Examples of steps include: execute command, filter, split, de-dup, replace, parse, etc. This approach greatly reduced the amount of code required to support all of the required project types, and greatly reduced the incremental effort required to add support for a new project type.

### Enhanced code

This [pull request](https://github.com/blackducksoftware/synopsys-detect/pull/516) shows a pretty typical change to a detector (in this case: the [BitBake Detector](https://documentation.blackduck.com/bundle/detect/page/packagemgrs/bitbake.html)). It includes new code (and tests) that I wrote, changes I made to existing code, and team interaction during code review.

#### Background

The BitBake Detector discovers dependencies in [BitBake](https://docs.yoctoproject.org/1.6/bitbake-user-manual/bitbake-user-manual.html) projects.
It does this by executing a BitBake command, parsing the output, executing another BitBake command using information parsed from the output of the previous command, etc. This sequence of steps eventually results in a graph representing the project’s dependencies, that Detect would feed into the [Black Duck SCA system](https://www.blackduck.com/software-composition-analysis-tools/black-duck-sca.html) via Black Duck's REST APIs. Unlike the Bazel detector, the BitBake detector only supports a single project type, so has no need for a pipeline approach.

<a name="cpp"></a>
## C++ / Robot Software

Since late 2021 I have been developing robot software in my spare time, primarily in C++. One of my objectives in this was to improve my C++ skills. I think robots are a lot of fun so robotics provided an interesting sandbox for learning a new language. For a look at some of my C++ code:

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
