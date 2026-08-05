# 03 - Ad-hoc Commands (EXODUS)

Summary of Ansible ad-hoc commands, mapped onto the real EXODUS fleet.
(Concept already understood - this is reference, not a drill.)

## What an ad-hoc command is

A one-off Ansible command you run straight from the terminal, without
writing a playbook. Good for quick, throwaway actions: check something,
ping hosts, look at a fact. Not for repeatable work - that is what
playbooks are for.

Rule of thumb:
- Ad-hoc  = quick, one-time, "just check / just do this once".
- Playbook = repeatable, documented, version-controlled.


## The shape of an ad-hoc command

ansible <hosts> -i <inventory> -m <module> -a "<arguments>"

- ansible      -> the ad-hoc command tool
- <hosts>      -> which hosts/group to target (e.g. all, linux, ingress)
- -i           -> which inventory file to use
- -m <module>  -> which module to run (default is 'command' if omitted)
- -a "..."     -> arguments passed to the module


## Read-only examples (safe - change nothing)

Ping every host (confirms Ansible can reach them over SSH):

ansible all -i inventories/production/hosts.yml -m ping



## Check uptime on the linux group:

ansible linux -i inventories/production/hosts.yml -m command -a "uptime"



## Show a single fact (the OS family) for one host:

ansible exodus-ingress-01 -i inventories/production/hosts.yml -m debug -a "var=ansible_facts.os_family"



## Gather ALL facts for one host (read-only, verbose):

ansible exodus-platform-01 -i inventories/production/hosts.yml -m setup



## command vs shell (important distinction)

- -m command -> runs a program directly. Safe default. Does NOT understand
  shell features like pipes, redirects, or variables.
- -m shell   -> runs through the shell, so pipes/redirects work - but is
  more powerful and slightly riskier. Use only when you need shell features.

## Example where you MUST use shell (because of the pipe):

ansible linux -i inventories/production/hosts.yml -m shell -a "ps -ef | grep sshd"




## Which are read-only vs state-changing

- Read-only (safe to run anytime): ping, setup, debug, command with things
  like uptime / df / cat.
- State-changing (would ALTER a server): command/shell that installs, edits
  files, restarts services, etc. Those get flagged before we run them.

## Interview point

Ad-hoc commands prove you can operate the fleet interactively for quick
checks and one-off fixes, while playbooks are how you do anything you want
repeatable and auditable. Knowing WHEN to use each is the real signal.