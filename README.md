# lvm
Manage volumes and filesystems with LVM. This role performs the following actions:


 * installs lvm2 package
 * configures physical volumes, vol group and logical volumes
 * creates and mounts filesystem

### Requirements
* Ubuntu 14.04+
* Ansible 2.x
* root access

### Role Variables
The following default variables can be redefined as needed

    # a list of volumes to configure
    volumes:
      # the block device path. this can be a list of comma separated devices
    - pvs_vol: /dev/xvdb
      # name of the volume group
      vg_name: vgopt
      # name of the logical volume
      lv_name: lvopt
      # the mount path
      mount_path: /opt
      # a comma separated list of mount options
      mount_opts: defaults,noatime,nobarrier
      # the size of the lvm
      lv_size: "+100%FREE"
      # the filesystem type
      fstype: ext4

    # patch the lvol module. See: https://github.com/ansible/ansible-modules-extras/issues/428
    ansible_2_patch: false


### Usage
The following example adds the default lvm disk configuration.

    ---
    - hosts: all
      sudo: yes
      roles:
      - role: garyellis.lvm



### License
MIT

### Author
*Gary Ellis* <gary.luis.ellis@gmail.com>
