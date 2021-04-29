## Azure VM

1. A virtual machine with Intel silicon (M1 not possible yet)

   1. **Win10**

      Standard DS11 v2 (2 v-cpus, 14 GiB memory). Great performance but requires a Windows license, acquired separately

   1. **Win10 on a spot instance**

      Even with the same specs as above (except for a standard SSD instead of a premium one), the spot instance seemed to have much worse performance with CPU utilisation at 100% most of the time! Given it's not disks but CPU, I assume it's the spot instance and not the standard SSD causing the malperformance.

   1. **Ubuntu**

      Final option, currently used - an Ubuntu VM (same DS111 specs as above). Aside from [a quick initial setup for VSCode](../posts/2021-04-25.md), it works brilliantly!

1. Download and install nvm (or nvm-windows)
1. Install node 10 (SP Dev) and latest (General use inc. M365 CLI and Azure)
1. `npm install gulp yo @microsoft/generator-sharepoint --global`
1. Install browsers, git and vscode
