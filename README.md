# Ansible Role: s3fs-fuse

Ansible role for mounting an AWS S3 bucket via FUSE. The role installs and configures [s3fs-fuse](https://github.com/s3fs-fuse/s3fs-fuse) on Ubuntu.

## Requirements

An AWS account and an existing S3 bucket. Tested on Ubuntu 12.04, 14.04 and 16.04.

## Role Variables

Available variables are listed below, along with default values:

    s3fs_fuse_version: "1.80"
    s3fs_fuse_access_key_id:
    s3fs_fuse_secret_access_key:
    s3fs_fuse_bucket:
    s3fs_fuse_mount_point: /mnt/s3
    s3fs_fuse_mount_point_permissions: "0777"

## Dependencies

None

## Example Playbook

    - hosts: all
      roles:
        - role: s3fs_fuse
          s3fs_fuse_bucket: ansible-s3fs-fuse
          s3fs_fuse_access_key_id: <your aws access key id>
          s3fs_fuse_secret_access_key: <your aws secret access key>

## License

GPL v2