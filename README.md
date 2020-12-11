# ubuntu

---

# AMD Radeon Ubuntu 20.04 Driver Installation

### AMD Radeon Ubuntu 20.04 Driver Installation step by step instructions

&thinsp;

Let's start by gathering some information about your system and current state of the AMD Radeon driver. First check your VGA graphic card model and driver in use. To do so execute the following command:


```properties
$ sudo lshw -c video
```

---

# Proprietary AMDGPU-PRO drivers


In order to get the drivers, you need to go to the AMD Download Page, and grab the latest version of the drivers that matches your card. The release should come in the form of a tarball. Either extract the tarball automatically with your GUI archive manager through your browser or let it download and extract it using tar from the command line.


```properties
$ tar -xf amdgpu-pro_*.tar.xz
```

A directory containing all of the necessary packages will be created based on the version of the drivers. cd into that directory.

```properties
$ cd amdgpu-pro-XX.XX-XXXXXX
```

Don't worry about installing all of those packages individually. There's an installer script that will handle everything for you. Run the script as a regular user. It will ask you for your password to use sudo. If you want to be lazy, add the -y flag to answer "Yes" to every question.

```properties
$ ./amdgpu-pro-install -y
```

&thinsp;

 In case you need to uninstall the previously installed Proprietary AMDGPU-PRO drivers execute the following command:

```properties
$ amdgpu-pro-uninstall
```

You may get error like below:

```
Package amdgpu-hwe is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package amdgpu-pro-hwe is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'amdgpu-hwe' has no installation candidate
E: Package 'amdgpu-pro-hwe' has no installation candidate
```

Run the below cmd to install the driver after you have removed the previous driver

```properties
$ amdgpu-pro-install --opencl=legacy,pal --headless
```


---

# GpuTest

you can download the test tool from [here][GpuTest]



```properties
$ unzip GpuTest_Linux_x64_0.7.0.zip
$ cd GpuTest
$ ./GpuTest
```

[GpuTest]:https://www.geeks3d.com/dl/show/392
