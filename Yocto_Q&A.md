# ✅ Yocto Project Interview Questions & Answers (50+ Q&A)

## 🧩 Basic Yocto Questions (Q1–Q12)

1. ❓ What is the Yocto Project?  
→ It's an open-source build system to create custom Linux distributions for embedded systems.

2. ❓ What is Poky?  
→ Poky is the Yocto reference distribution that includes BitBake, metadata, and configuration files.

3. ❓ What is BitBake?  
→ It's the task executor and build engine used by the Yocto Project.

4. ❓ What is OpenEmbedded?  
→ OpenEmbedded is a build framework. Yocto uses OpenEmbedded Core (OE-Core) as its foundation.

5. ❓ What is Metadata in Yocto?  
→ Metadata includes recipes, classes, configuration files that define how packages are built and images are created.

6. ❓ What is a layer in Yocto?  
→ A layer is a collection of related recipes, classes, and configuration files.

7. ❓ What is a recipe (.bb file)?  
→ A recipe defines how a package is built, including source, dependencies, and build instructions.

8. ❓ What is a .bbappend file?  
→ It is used to append or override parts of an existing .bb file without modifying it.

9. ❓ What is a machine configuration file?  
→ It defines hardware-specific settings like CPU architecture, bootloader, kernel, etc.

10. ❓ What is the role of local.conf?  
→ It allows developers to override default settings like target machine, image type, etc.

11. ❓ What is DISTRO in Yocto?  
→ DISTRO defines the distribution policy and can customize features, init system, etc.

12. ❓ What is an image in Yocto?  
→ It is the final root filesystem created after compiling packages (e.g., core-image-minimal).

## ⚙️ Intermediate Yocto Questions (Q13–Q27)

13. ❓ How do you add a new layer to your Yocto build?  
→ Use bitbake-layers add-layer <path-to-layer>

14. ❓ How do you add a new recipe?  
→ Create a .bb file in the appropriate layer under recipes-xxx/.

15. ❓ What is the purpose of IMAGE_INSTALL?  
→ It specifies what packages are included in the root filesystem.

16. ❓ What is the difference between DEPENDS and RDEPENDS?  
→ DEPENDS is build-time dependency; RDEPENDS is runtime dependency.

17. ❓ How do you inherit classes in a recipe?  
→ Use inherit <classname> inside the recipe (.bb).

18. ❓ What are .bbclass files?  
→ They contain shared functionality used across recipes.

19. ❓ What is the sstate-cache in Yocto?  
→ It stores build artifacts to speed up future builds.

20. ❓ What is the difference between TMPDIR and DL_DIR?  
→ TMPDIR is where temporary build output goes. DL_DIR stores downloaded source code.

21. ❓ What is devshell?  
→ It opens a shell in the BitBake build environment for a package.

22. ❓ What are the main directories in a Yocto build?  
→ build/, meta/, poky/, downloads/, sstate-cache/, tmp/, etc.

23. ❓ What is do_compile in a recipe?  
→ It's the BitBake task that compiles the source code.

24. ❓ What is do_install?  
→ Task that installs compiled output to a staging directory.

25. ❓ What is do_rootfs?  
→ Creates the final root filesystem image.

26. ❓ What is LICENSE in a recipe?  
→ Declares the software license of the package.

27. ❓ What is the difference between core-image-minimal and core-image-base?  
→ core-image-minimal has the fewest components; base has more tools.

## 🚀 Advanced Yocto Questions (Q28–Q40)

28. ❓ How do you create a custom image?  
→ Create a new .bb file (e.g., core-image-mycustom.bb) inheriting core-image and define IMAGE_INSTALL.

29. ❓ What is the layer priority and how is it set?  
→ Determines which layer overrides take effect. Set using BBFILE_PRIORITY in layer.conf.

30. ❓ What is override syntax in BitBake?  
→ Allows applying different values per condition (e.g., DEBUG:pn-myapp = "1").

31. ❓ What is the use of PREFERRED_VERSION?  
→ Forces Yocto to build a specific version of a package.

32. ❓ How do you clean and rebuild a specific recipe?  
→ bitbake -c clean <recipe> && bitbake <recipe>

33. ❓ What is INSANE_SKIP used for?  
→ Skips QA checks for a recipe (used for development/debugging).

34. ❓ What are distro features in Yocto?  
→ Used to enable or disable features like X11, wayland, bluetooth, etc.

35. ❓ What is multiconfig in Yocto?  
→ Allows building for multiple machines/configs in the same build.

36. ❓ What is multilib in Yocto?  
→ Supports building libraries for multiple architectures (e.g., 32-bit + 64-bit).

37. ❓ What is externalsrc?  
→ Enables using source code from outside the Yocto build directory (e.g., for development).

38. ❓ How do you patch a kernel in Yocto?  
→ Add your patch via SRC_URI += "file://mypatch.patch".

39. ❓ What is pseudo in Yocto?  
→ A tool that simulates root privileges during the build process.

40. ❓ What is wic in Yocto?  
→ A tool to generate complete disk images with partitions.

## 🧠 Practical Questions & Packages (Q41–Q52)

41. ❓ What is Dropbear, and how is it used in Yocto?  
→ Dropbear is a lightweight SSH server suitable for embedded systems. Use IMAGE_INSTALL += "dropbear".

42. ❓ What is systemd, and how do you use it in Yocto?  
→ It's a system and service manager. Enable it using DISTRO_FEATURES += "systemd".

43. ❓ How do you include an SSH server in a Yocto image?  
→ Add dropbear or openssh to IMAGE_INSTALL.

44. ❓ What is INITRAMFS and how is it configured in Yocto?  
→ A minimal rootfs for early boot. Set INITRAMFS_IMAGE = "core-image-minimal-initramfs".

45. ❓ How do you reduce the Yocto image size?  
→ Use smaller images, remove unused packages, disable features.

46. ❓ How do you include kernel modules in the image?  
→ Use IMAGE_INSTALL and set KERNEL_MODULE_AUTOLOAD.

47. ❓ What is the difference between core-image-minimal and core-image-full-cmdline?  
→ Minimal is barebones; full-cmdline includes basic shell tools and utilities.

48. ❓ How do you add a systemd service in a recipe?  
→ Inherit systemd and set SYSTEMD_SERVICE_${PN} = "your-service.service".

49. ❓ How do you configure the root password?  
→ Set EXTRA_USERS_PARAMS = "usermod -P mypass root;" in local.conf.

50. ❓ How do you enable serial console in a Yocto image?  
→ Add console=ttyS0 to kernel bootargs and enable a getty service.

51. ❓ What is the meta-oe layer?  
→ It’s a community-contributed layer with many additional packages.

52. ❓ What’s the difference between MACHINE_FEATURES and DISTRO_FEATURES?  
→ MACHINE_FEATURES is hardware-level; DISTRO_FEATURES is software-level.
