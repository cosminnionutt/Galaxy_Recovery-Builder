# Use Github Action to compile Recovery
```
Support OFRP, SHRP, TWRP compilation and production
```
---

## Release Notes
```
= 2022/07/06
- Add support for 5.1 branch

= 2022/07/05
- Updated to work with trees back to 6.0
- Add conditionals to include common trees for syncing
- Update README for SSH keys

= 2022/07/04
- Updated to work with Android 12.1 AOSP minimal TWRP manifest

= 2022/05/29
- Should work correctly with Android 11 based source code

= 2022/02/03
- Due to the hardware resource limitation of GitHub action, this version cannot be compiled based on AOSP and other source codes of Android 11 and above. If necessary, please use local compilation

= 2021/10/29: 
- Refactored version 2.0
- Completely reconstruct the use logic to reduce the difficulty of use
- Optimize the parameter transfer part, now you can run multiple Workers at the same time
- TWRP compilation test passed
- OFRP compilation test passed
- SHRP compile test passed
```

-----

## Parameter Description

| Name | Description | Example |
| ------------ | -------------------- | ------------ |
| `MANIFEST_URL` | Source address | https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git |
| `MANIFEST_BRANCH` | Source branch | twrp-12.1 |
| `DEVICE_TREE_URL` | Device address | https://github.com/TeamWin/android_device_asus_I003D |
| `DEVICE_TREE_BRANCH` | Device branch | android-12.1 |
| `DEVICE_PATH` | Device location | device/asus/I003D |
| `COMMON_TREE_URL` | Common tree address | https://github.com/TeamWin/android_device_asus_sm8250-common |
| `COMMON_PATH` | Common tree location | device/asus/sm8250-common |
| `DEVICE_NAME` | Model name | I003D |
| `MAKEFILE_NAME` | Makefile name | twrp_I003D |
| `BUILD_TARGET` | Build Target Partition (boot/recovery/vendorboot) | recovery |

-----

## how to use
```
For example, your username is: Fun-114514
```
#### 1. Click'Fork' in the upper right corner of this warehouse
![](https://i.bmp.ovh/imgs/2021/10/6b6ed9f29e732372.png)
#### 2. After waiting for the automatic redirection, you will see your own username
![](https://i.bmp.ovh/imgs/2021/10/66cfe324c0ebb69b.png)
#### 3. Change the [username and email](https://github.com/CaptainThrowback/Action-Recovery-Builder/blob/main/.github/workflows/Recovery%20Build.yml#L100-L101) in the workflow to reflect your Github credentials
## Setting up SSH Keys (optional)
#### 4. Go to Settings, then select Deploy keys and select "Add deploy key" button.

#### 5. On your Android device, install [Termux](https://github.com/termux/termux-app/releases)

#### 6. Install openssh in Termux and generate ssh keys. (Do not use passphrase for keys)
NOTE: When creating the deploy key for a repository like git@github.com:owner/repo.git or https://github.com/owner/repo, put that URL into the key comment. (Hint: Try ssh-keygen ... -C "git@github.com:owner/repo.git".)
owner = your Github username
```
pkg install openssh
ssh-keygen -t ed25519 -C "git@github.com:owner/Action-Recovery-Builder.git"
```
#### 7. Add the keys to your repo. In Termux, use the following commands:
```
cd /data/data/com.termux/files/usr/etc/ssh
cat ssh_host_ed25519_key.pub
```
  Select and copy the key then paste in the box for Key.
  You can name it whatever you choose for the title.

#### 8. Now to add your private ssh key. Back in Termux:
```
cat ssh_host_ed25519_key
```
   Copy the output from Termux.

   In your browser, select *Secrets* under the Security tab.
   Select Actions
   Select New repository secret
   For the New secret name, it should be SSH_PRIVATE_KEY
   Paste the output from ssh_host_ed25519_key into the Value box.
   Then select Add secret.

## Building the Recovery
#### 9. Click'Actions-Recovery Build'
![](https://i.bmp.ovh/imgs/2021/10/23896d1b66292047.png)
#### 10. Click'Run workflow' and fill in according to the above'parameter description'
![](https://i.bmp.ovh/imgs/2021/10/9cb7871267cf2f53.png)
#### 11. After filling in, click'Run workflow' to start running

-----

## Compilation results
Can be downloaded at [Release](../../releases)

-----
## Remark

#### TeamWin Recovery Project: https://github.com/minimal-manifest-twrp
#### OrangeFox Recovery Project: https://gitlab.com/OrangeFox/Manifest.git
#### SKYHAWK Recovery Project: https://github.com/SHRP/platform_manifest_twrp_omni.git
