# How to build AOSP Custom ROM?

Hello friends, this time I want to discuss how to build AOSP. For you HP repairers, are you sometimes curious about how to build your own Custom ROM? So, on this occasion I want to give you the easiest tutorial on how to build your own Custom ROM.

Before continuing, make sure you have a basic understanding of the Linux CLI and also GIT version control, besides that, make sure you also have a computer/server with the specifications I recommend, namely 8 CPU cores and 32 GB RAM for a smooth build process, and don't forget to prepare 3000 storage. GB, because the Android 13 Source is quite large. Actually, for the specs of 4 CPU cores and 16 GB RAM, it is still possible, but you have to activate SWAP memory and so on, which I cannot possibly explain in this article. Don't forget to use Ubuntu 18 OS and above, in this case I use Ubuntu 22.04 with 32 CPU core specs and 64 GB RAM as the build server. OK, well, up to this step, I assume you have met these requirements. Next, let's prepare the build environment.

⚪ **Requirements** :

1. *Brain & Knowledge About Linux & Git command*
2. *Internet & Data.*
3. *Server: Like [Google Cloud](https://cloud.google.com/storage?hl=en), [Azure](https://azure.microsoft.com/en-us/resources/cloud-computing-dictionary/what-is-cloud-computing/), [Fybe](https://fybe.com/en/object-storage?gclid=Cj0KCQjw4bipBhCyARIsAFsieCynp-Mcn2A1tH6CLWWYTIlvNRcwAxiDaifoQQM7wXDnTJ1V9-MyLxIaAj_PEALw_wcB), [Amazon](https://aws.amazon.com/products/storage/).*
4. *Device Tree.*
5. *Common Device Tree(If have).*
6. *Vendor Tree.*
7. *Kernel Tree / Prebuilt kernel.*

⚪ **Setting up the build environment** :

You must install the required packages/dependencies.

``` bash
sudo apt-get install git-core gnupg flex bison build-essential zip curl zlib1g-dev libc6-dev-i386 libncurses5 x11proto-core-dev libx11-dev lib32z1-dev libgl1-mesa-dev libxml2-utils xsltproc unzip fontconfig python3 python-is-python3
```

⚪ **Setting up the launcher repo** :
``` bash
mkdir lineageos
cd lineageos
```

⚪ **Prepare local manifest** :

In this case I use the local manifest to make it faster to prepare the device tree, vendor tree and also kernel tree. Actually, you can use git clone one by one, but to make it easy and fast we will use a local manifest. Here I already have a manifest for the Xiaomi Redmi Note 9 device. For other devices, you can search for it on GitHub.

Example:
``` bash
https://github.com/Shakib-BD/local_manifest.git
```

⚪ **Sync ROM source and local manifest** :

For this tutorial I will use LineageOS 20 Android 13 because in my opinion most of the devi ce tree is definitely ready to be used for that Rom.

``` bash
repo init --depth=1 --no-repo-verify -u https://github.com/LineageOS/android.git -b lineage-20.0 --git-lfs -g default,-mips,-darwin,- notdefault 
git clone https://github.com/Shakib-BD/local_manifest.git --depth 1 -b lineage-20.0 .repo/local_manifests 
repo sync -c --no-clone-bundle --no-tags --optimized-fetch --prune --force-sync -j8
```

After that, you wait a while, because this process usually takes quite a while depending on the internet speed you have.

⚪ **NOTES** :

Make sure you change the local manifest on line 2 according to your device, the code above has been optimized so that when syncing it is not too big.

⚪ **Customizing the Device Tree (Optional)** :

This step is only optional and can be skipped if your device tree is compatible with LineageOS. However, if not, you have to edit it, for example for the Redmi Note 9 it is in the directory *device/xiaomi/merlinx*. So, I can't explain the editing process in this article because it would be quite long. So I assume your device tree is appropriate. You have to make a repository for Bringup rom branch for your device. Here I already have lineage-20 branch and already bringup for Xiaomi Redmi Note 9 device. For other devices, you can search for it on GitHub. [Bringup].

Example:
``` bash
https://github.com/Shakib-BD/dt_merlinx/tree/lineage-20
```

⚪ **Build a Custom ROM** :

After the steps above have been carried out correctly, the next step is the building process which usually takes quite a lot of time depending on the specifications of the computer you have. Next, all you have to do is copy and change it merlinxaccording to your cellphone codename, for example cactus.

``` bash
. build/envsetup.sh 
lunch lineage_merlinx-user 
make bacon
```

⚪ **NOTE** :
Make sure you wait patiently at this step.
When finished, green writing will appear and also the location where the custom ROM Zip file is located.

⚪ **Rom Upload** :

You can upload your rom to 📎 [temp.sh](https://temp.sh) / [transfer.sh](https://transfer.sh) to read their uploading guide.

So that's more or less how to build your own Custom ROM, even though in the end it looks difficult, that's how it is because when you read this article I'm sure you'll want to learn. And yes, maybe this article is still incomplete and I am aware of that, but it would be too long to explain everything in one post. And the last do with your own risk.

© Credit : [Ozi Saputra](https://github.com/mitsu00) & [Shakib](https://t.me/Info_Shakib)
