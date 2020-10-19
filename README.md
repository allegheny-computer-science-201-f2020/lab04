# :crocodile: Control Structures, CMPSC 201 Fall 2020: LAB 04 Assignment

## DUE: October 27th by 3:00pm

[![Actions Status](../../workflows/build/badge.svg)](../../actions)

## Table of Contents

- [Summary](#summary)

- [Objectives](#objectives)

- [Reading Assignment](#reading-assignment)

- [Accessing the Repository](#accessing-the-repository)

- [Tasks](#tasks)

- [Running and Testing](#running-and-testing)

  - [Docker](#docker)

  - [GatorGrader](#gatorgrader)

  - [GitHub Actions CI](#github-actions-ci)

- [Evaluation](#evaluation)

- [Problems](problems)

## Summary

Designed for use with [GitHub Classroom](https://classroom.github.com/), this repository contains starter materials for lab 04 in [Computer Science 201 Fall 2020](https://cs.allegheny.edu/sites/jjumadinova/teaching/201). The lab04 assignment invites individuals to experiment with control structures.

Please watch a video introducing this lab assignment under the course's YouTube playlist: [Lab 04 Assignment Introduction](https://www.youtube.com/playlist?list=PLz9YRLfRGO9JpJfVknMPnK_jagA0mgxN0)

## Objectives

- To experiment with control structures in three different programming languages.
- To look "under the hood" at some control structures.
- To continue the practice of using the Java bytecode and explore bytecode related to control structures.

## Reading Assignment

To understand the concepts covered in this assignment, you should read Chapter 6 of the "Programming Language Pragmatics" textbook. You should also review questions and correct answers in activity5.

To learn more about Java bytecode specification and instructions consider the following resources:

- [The Java Virtual Machine Specification](http://docs.oracle.com/javase/specs/jvms/se8/html/index.html)
- [Instructions listing](https://en.wikipedia.org/wiki/Java_bytecode_instruction_listings)
- [JVM Instruction Set Documentation](https://docs.oracle.com/javase/specs/jvms/se7/html/jvms-6.html).

If you have not done so already, please read all of the relevant [GitHub Guides](https://guides.github.com/) that explain how to use many of the features that GitHub provides. In particular, please make sure that you have read guides such as "Understanding the GitHub flow", "Mastering Markdown" and "Documenting Your Projects on GitHub"; each of them will help you to understand how to use both GitHub and GitHub Classroom.

## Accessing the Repository

Please go into the #labs channel in our Slack team and find the announcement that provides a link for it. Copy this link and paste it into your web browser. Now, you should accept the laboratory assignment and see that a repository containing your GitHub username in its title was created for you. You can clone this repository and proceed with the tasks of the assignment.

## Tasks

For this laboratory assignment, you will complete a set of small experiments to gain a deeper understanding into control structures. Please navigate to the "writing/report.md" document to find outline of specific experiments and the tasks you are invited to engage in.

## Running and Testing

### Docker Commands

We use Docker for this course. This provides an environment with the languages that will be used in the class and ensures that everyone uses the same versions for help and grading purposes. Follow the instructions below, which can also be found at the `progator` Docker image link provided below, to get started. Additionally, please watch the lab introduction video for a working example of how to access the Docker image for this course and how to mount a directory as a volume.

[progator Docker Image](https://hub.docker.com/repository/docker/janyljumadinova/progator)

#### Pulling Image

If you haven't done so already recently, please download automated build from public Docker Hub Registry:

`docker pull janyljumadinova/progator`

You can check that you have the `progator` image by running the following command and verifying that you see `progator` in the list of your Docker images:

`docker image list`

#### Running

Now, run the docker container and mount your "lab04" directory as a volume by replacing `your-path/local/working/directory` in the following command with the path to your "lab04" directory:

_Mac OS_:

`docker run -d -p 80:80 -v /your-path/local/working/directory/:/root/environment janyljumadinova/progator`

_Linux OS_:

May need to use `sudo` as:

`sudo docker run -d -p 80:80 -v /your-path/local/working/directory/:/root/environment janyljumadinova/progator`

_Windows OS_ (note the quotes in path):

`docker run -d -p 80:80 -v "C:\Users\your-path/local/working/directory/":/root/environment janyljumadinova/progator`

You can check that you have correctly started the Docker container:

`docker container list`

#### Stopping the `progator` container and pruning

When you are finished working with `progator` do not forget to stop `progator` container by getting the container ID from the command you ran in your terminal:

`docker container list`

and then stopping the container by running the following command (replacing `container-ID` with the actual `progator` container ID in your terminal:

`docker container stop container-ID`

You should also remove all unused containers and images (both dangling and unreferenced) by running the following command:

`docker system prune -a`

#### Accessing the IDE

<http://localhost>

### Working in the Localhost Window

Once you have localhost open in your browser, all other instructions will be completed in that window. If you close the window, just go to localhost again - you will not lose anything.

When you open localhost, you will see:

![](InstructionImages/Image1.png?raw=true)

On the left side, click on the Explorer icon (2nd down). Click Open Folder and enter "/root/" ![](InstructionImages/Image2.png?raw=true)

In the Explorer frame, right click, and click on Open in Integrated Terminal. ![](InstructionImages/Image3.png?raw=true)

You now have a terminal in which you can run most typical Linux commands. Ubuntu 20.04 is running with VSCode. Most work will be completed in the terminal. You are encouraged to mount a directory as a volume as described in the documentation at [progator Docker Image](https://hub.docker.com/repository/docker/janyljumadinova/progator) so that you can have access to your local repository files, which can be accessed from the "environment" directory in "root".

Please remember to stop the container after you are finished working in it. You can use the command: `docker container list` to see the ID of the running container, and `docker container stop container-ID` to stop the container by replacing `container-ID` with its actual ID.

### GatorGrader

To assess the minimum completeness of the lab submission materials, you can use the GatorGrader tool. Once you have installed [Docker Desktop](https://www.docker.com/products/docker-desktop), you can use the following `docker run` command to start `gradle grade` as a containerized application, using the [DockaGator](https://github.com/GatorEducator/dockagator) Docker image available on [DockerHub](https://cloud.docker.com/u/gatoreducator/repository/docker/gatoreducator/dockagator).

```bash
docker run --rm --name dockagator \
  -v "$(pwd)":/project \
  -v "$HOME/.dockagator":/root/.local/share \
  gatoreducator/dockagator
```

This command will use `"$(pwd)"` (i.e., the current directory) as the project directory and `"$HOME/.dockagator"` as the cached GatorGrader directory. Please note that both of these directories must exist, although only the project directory must contain something. Generally, the project directory should contain the source code and technical writing of this assignment, as provided to a student through GitHub. Additionally, the cache directory should not contain anything other than directories and programs created by DockaGator, thus ensuring that they are not otherwise overwritten during the completion of the assignment. To ensure that the previous command will work correctly, you should create the cache directory by running the command `mkdir $HOME/.dockagator`. If the above `docker run` command does not work correctly on the Windows operating system, you may need to instead run the following command to work around limitations in the terminal window:

```bash
docker run --rm --name dockagator \
  -v "$(pwd):/project" \
  -v "$HOME/.dockagator:/root/.local/share" \
  gatoreducator/dockagator
```

If you are running your program on a Windows Operating System, you should run the following command instead, replacing the word "user" with the username of your machine:

```bash
docker run --rm --name dockagator -v "%cd%":/project -v "C:\Users\user/.dockagator":/root/.local/share gatoreducator/dockagator
```

Since the above `docker run` command uses a Docker images that, by default, runs `gradle grade` and then exits the Docker container, you may want to instead run the following command so that you enter an "interactive terminal" that will allow you to repeatedly run commands within the Docker container.

```bash
docker run -it --rm --name dockagator \
  -v "$(pwd)":/project \
  -v "$HOME/.dockagator":/root/.local/share \
  gatoreducator/dockagator /bin/bash
```

In Windows OS (replace `user` with your machine's username):

```bash
docker run -it --rm --name dockagator -v "%cd%":/project -v "C:\Users\user/.dockagator":/root/.local/share gatoreducator/dockagator /bin/bash
```

Once you have typed this command, you can use the [GatorGrader tool](https://github.com/GatorEducator/gatorgrader) in the Docker container by typing the command `gradle grade` in your terminal. Running this command will produce a lot of output that you should carefully inspect. If GatorGrader's output shows that there are no mistakes in the assignment, then your source code and writing are passing all of the automated baseline checks. However, if the output indicates that there are mistakes, then you will need to understand what they are and then try to fix them.

Here are some additional commands that you may need to run when using Docker:

- `docker info`: display information about how Docker runs on your workstation
- `docker images`: show the Docker images installed on your workstation
- `docker container list`: list the active images running on your workstation
- `docker system prune`: remove many types of "dangling" components from your workstation
- `docker image prune`: remove all "dangling" docker images from your workstation
- `docker container prune`: remove all stopped docker containers from your workstation
- `docker container stop ID`: stop the running container with specified ID
- `docker rmi $(docker images -q) --force`: remove all docker images from your workstation

### GitHub Actions CI

GitHub Actions CI is configured to check the program files for minimum requirements and the Markdown files in the repository with "mdl". If your program and the writing meets the minimal established requirements, then you will see a green :heavy_check_mark: in the listing of commits in GitHub. If your submission does not meet the requirements, a red :heavy_multiplication_x: will appear instead. Since this assignment contains a large creative and open-ended portion, the majority of your lab grade will be based on the satisfaction of the requirements outlined in the previous sections with the details included in the `report.md` file.

## Evaluation

The grade that a student receives on this assignment will have the following components. In addition to these three main components, student's grade may be affected by their adherence or the lack of adherence to the [Code of Conduct](https://github.com/allegheny-computer-science-201-f2020/lab01-cs201f2020/blob/main/conduct.md) developed for this course.

_Percentage of Correct GatorGrader Checks and GitHub Actions CI Build Status [up to 40%]_: Students are encouraged to repeatedly revise their submission to ensure that it passes all of GatorGrader's checks and receives a CI pass.

_Mastery of Technical Knowledge and Skills [up to 20%]_: Students will also receive a portion of their assignment grade when their program source files reveal that they have mastered all of the technical knowledge and skills developed during the completion of this lab. Since this lab assignment does not require significant implementation, this portion of the grade is not heavily weighted.

_Mastery of Technical Writing [up to 40%]_: Students will receive a portion of this lab grade when the responses to the technical writing questions presented in the "writing/report.md" reveal a mastery of both writing skills and conceptual and technical knowledge. To receive this portion of the grade, the submitted writing should provide conceptually and technically accurate answers and have correct spelling, grammar, and punctuation in addition to following the rules of Markdown.

## Problems

If you have any problems with this assignment, then please create an issue in this repository using the "Issues" link at the top of this site.
