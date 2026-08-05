# 01 - Ansible Architecture (EXODUS)

Summary of how Ansible works, mapped onto the real EXODUS fleet.
(Concept already in place - this is reference, not a drill.)

## The core idea

Ansible is **agentless** and **push-based**. You run it from ONE machine
(the control node). It connects OUT to the other machines over **SSH** and
makes the changes. Nothing needs to be installed on the machines being
managed except Python and SSH, which RHEL already has.

- No agent/daemon to install on managed hosts.
- No central server constantly running.
- You run a command/playbook -> Ansible pushes the work out -> done.

## The two roles a machine can have

- **Control node** = where Ansible is installed and run FROM.
- **Managed node** = a machine Ansible connects TO and configures.

## Mapped onto EXODUS

Control node:
- exodus-automation-01  (192.168.0.158)  <- Ansible runs from here

Managed nodes (Ansible connects to these over SSH):
- exodus-platform-01      (192.168.0.151)
- exodus-services-01      (192.168.0.152)
- exodus-observability-01 (192.168.0.153)
- exodus-grafana-01       (192.168.0.154)
- exodus-ingress-01       (192.168.0.155)
- exodus-logging-01       (192.168.0.156)
- exodus-ad-01            (Windows Domain Controller)

## How a run flows