# Proxmox Fresh Post-Install Steps

1. https://community-scripts.github.io/ProxmoxVE/scripts?id=post-pve-install
2. From node shell: `cd /lib/firmware/i915`
     - Delete kbl_dmc_ver1_04.bin
3. To fix LXC backup errors: `nano /etc/vzdump.conf`
     - Uncomment tmpdir and set to /tmp
4. Setup email
     - https://technotim.live/posts/proxmox-alerts/
