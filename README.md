# Ansible Role: s3fs-fuse
[![Build Status](https://travis-ci.org/bastiaanvanassche/ansible-role-s3fs-fuse.svg?branch=automated_tests)](https://travis-ci.org/bastiaanvanassche/ansible-role-s3fs-fuse)

Ansible role for mounting an AWS S3 bucket via FUSE. The role installs and configures [s3fs-fuse](https://github.com/s3fs-fuse/s3fs-fuse) on RedHat/CentOS or Debian/Ubuntu Linux.

## Requirements

An AWS account and an existing S3 bucket. Tested on Ubuntu 12.04, 14.04, 16.04 and CentOS 7.

## Role Variables

Available variables are listed below, along with the default values:

    s3fs_fuse_version: "1.80"
    s3fs_fuse_access_key_id:
    s3fs_fuse_secret_access_key:
    s3fs_fuse_bucket:
    s3fs_fuse_mount_point: "/mnt/s3"
    s3fs_fuse_mount_point_permissions: "0777"
    s3fs_fuse_url: "http://s3.amazonaws.com"
    s3fs_fuse_option_flags:
      - "allow_other"
      - "nonempty"

## Dependencies

None

## Example Playbooks

### Simple auth via keys

    - hosts: all
      roles:
        - role: s3fs_fuse
          s3fs_fuse_bucket: ansible-s3fs-fuse
          s3fs_fuse_access_key_id: <your aws access key id>
          s3fs_fuse_secret_access_key: <your aws secret access key>

### Use EC2 instance profile auth and custom options

```
- hosts: "tag_class_fuse"
  roles:
    - role: bastiaanvanassche.s3fs-fuse
      s3fs_fuse_bucket: ansible-s3fs-fuse
      s3fs_fuse_mount_point: "/media/fuseS3"
      s3fs_fuse_cache_folder: "/tmp/fuseS3cache"
      s3fs_fuse_mount_point_permissions: "0777"
      s3fs_fuse_option_flags:
        - "iam_role='iam_role_name'" # Role with sufficient access to the bucket
        - "endpoint='eu-west-1'"
        - "allow_other"
        - "nonempty"

```

## License

GPL v2
