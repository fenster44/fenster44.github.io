# Proxmox Fresh Post-Install Steps

1. https://community-scripts.github.io/ProxmoxVE/scripts?id=post-pve-install
2. https://forum.proxmox.com/threads/proxmox-random-reboots-on-hp-elitedesk-800g4-fixed-with-proxmox-install-on-top-of-debian-12-now-issues-with-hardware-transcoding-in-plex.132187/page-4#post-750312

   Or try this (from node shell):
   
   ```
   cd /lib/firmware/i915
   ```
   ```
   rm kbl_dmc_ver1_04.bin
   ```
4. To fix LXC backup errors (only if using direct NFS backups):
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
8. Update LXCs
   ```
   bash -c "$(curl -fsSL https://raw.githubusercontent.com/community-scripts/ProxmoxVE/main/tools/pve/update-lxcs.sh)"
   ```
9. Override backup notification templates
https://forum.proxmox.com/threads/how-to-customize-the-proxmox-vzdump-email-notification-format-for-backup-summaries.161899/#post-770232
It's the /usr/share/pve-manager/templates/default directory. But good news, Proxmox VE 8.4 now added support for overridable templates, this eliminates the problem of changes being overridden by package updates. To override a template, create/copy a template file at /etc/pve/notification-templates/default . For example, if you want to override the subject for backup notifications, create a /etc/pve/notification-templates/default/vzdump-subject.txt.hbs template. You may want to use the default template at /usr/share/pve-manager/templates/default as a reference.
