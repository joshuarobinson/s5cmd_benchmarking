# s5cmd_benchmarking
Benchmarking object storage with s5cmd and ansible.

Use the following Ansible playbook for simple S3 benchmarking.

Required:
 * Install Ansible and configure host group, update playbook with host group.
 * Install docker and docker-py on all hosts.
 * Create access keys and bucket to be used in testing.
 * Edit variables in the yaml file: S3 endpoint, bucket, and key prefix.
 * Create s3credentials.yaml file containing S3 access and secret keys.

An example credentials file is included in the repository, please add your keys there (and do NOT add to source control).

This benchmark is designed for storage systems that may do inline compression but NOT dedupe. To modify the compression factor, update the compressibility_ratio variable to N where the resulting data should compress N:1. The dataset generator is based on the [lzdatagen utility](https://github.com/jibsen/lzdatagen).

This playbook is designed for the [# of forks](https://docs.ansible.com/ansible/latest/reference_appendices/config.html#default-forks) to be as large as the host group so that each task is executed in parallel on all hosts.
