# Proxmox Fresh Post-Install Steps

1. https://community-scripts.github.io/ProxmoxVE/scripts?id=post-pve-install
2. From node shell:
   ```
   cd /lib/firmware/i915
   ```
   ```
   rm kbl_dmc_ver1_04.bin
   ```
4. To fix LXC backup errors:
   ```
   nano /etc/vzdump.conf
   ```
     - Uncomment tmpdir and set to /tmp
6. Setup email
      - https://technotim.live/posts/proxmox-alerts/
7. Find old CT volumes and delete
      - ```
        pct rescan
        ```
      - Then use GUI to delete unused volumes
