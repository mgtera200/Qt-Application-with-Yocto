# Running Your First Qt Application with Yocto

## Introduction
Welcome to the world of embedded Linux development! This README will guide you through running your first Qt application using Yocto with core-image-weston. Before we dive into the details, let's understand some key concepts:

### Weston, Wayland, and X11
In the world of graphical user interfaces (GUIs) on Linux systems, there are several important components:

1. **X11**: X11, also known as the X Window System, is the traditional display protocol used in Linux systems. While still widely used, it's considered older and less efficient compared to Wayland.

2. **Wayland**: Wayland is a modern display protocol designed to replace the older X11 protocol. It offers better performance, security, and efficiency.
  
3. **Weston**: Weston is the default compositor for Wayland. It's responsible for managing the graphical environment, handling windows, and input events.


## Getting Started with Yocto and Qt
Now, let's get started with running your first Qt application using Yocto:

## Step 1: Set Up Yocto
If you haven't already, follow the Yocto Project Quick Start guide to set up your Yocto environment:
[image|distro|Mypackage|Qemu|RPi4](https://github.com/mgtera200/YOCTO/tree/main/04-%20tera-image%20%7C%20tera%20distro%20%7C%20My%20package%20%20%7C%20Qemu%20%7C%20RPi4)

---

## Step 2: Test your QT app on Host machine:
1- Write your QT .cpp file:


![Qt c](https://github.com/mgtera200/Qt-Application-with-Yocto/assets/127119775/bc021c18-5ada-4263-b709-32c226af0141)


2- Write .pro file:


![Qt pro](https://github.com/mgtera200/Qt-Application-with-Yocto/assets/127119775/52a256cc-912f-45b5-ba27-247c12a35f64)
---

### IMPORTANT NOTE: your QT app code files should be named "myQTApp", Why?

- Notice that the Makefile is configured to build only `myQTApp` even if i named my file `myQtApp` as shown:


![qtt](https://github.com/mgtera200/Qt-Application-with-Yocto/assets/127119775/ebd931a1-d8d9-4298-98e2-be828c8ffff3)

---




3- Open terminal and write `qmake` then write `make`


4- Now start your QT application:


![QT result](https://github.com/mgtera200/Qt-Application-with-Yocto/assets/127119775/791cb650-151a-4279-9704-bff8c45644b4)


---

## Step 3: Adding The QT app to our RPI4 Image:



1- Add `meta-qt5` Layer and `meta-openembedded` Layer to poky

2- Edit bblayes.conf to include them:


![bblayes conf](https://github.com/mgtera200/Qt-Application-with-Yocto/assets/127119775/1c67ff07-eb0b-4cd0-885a-a222882d0c54)






3- Under your own meta-layer create this path `recipes-project/myqtapp/myqtapp_0.1.bb` to add your recipe for the Qt app


![qt path png](https://github.com/mgtera200/Qt-Application-with-Yocto/assets/127119775/c5ef5eb0-f2b5-4dee-a020-d87df973711f)



4- Copy your QT code files (.cpp , .pro) to `recipes-qtapp/myqtapp/files`

---

## Step 4: Add the required features and packages to your image:

1- in the `.conf` file of your distro append those Features:


![features_append](https://github.com/mgtera200/Qt-Application-with-Yocto/assets/127119775/0ef4fd8a-442e-44b7-ab49-019053a5f2d0)


2- Edit your image recipe in your own layer to include core-image-weston:


![tera-weston](https://github.com/mgtera200/Qt-Application-with-Yocto/assets/127119775/4d7e9632-bf06-4ff6-882d-96980ade0bdf)

---

## Step 4: Test your image on RPI4:

- Open the terminal and type `myQTApp` and everything will work fine:


![WhatsApp Image 2024-05-01 at 4 00 39 PM](https://github.com/mgtera200/Qt-Application-with-Yocto/assets/127119775/ad89ac73-5ad8-4af4-ac67-a6c165596e38)
