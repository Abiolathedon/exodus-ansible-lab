# 02 - Inventory (EXODUS)

Summary of the Ansible inventory, mapped onto the real EXODUS fleet.
(Concept already in place - this is reference, not a drill.)

## What an inventory is

The inventory is the **list of machines Ansible can manage**, and how they
are **grouped**. Ansible reads it to answer one question: "which hosts does
this play run against?"

- A host = one managed machine.
- A group = a named set of hosts you can target together.
- A host can belong to more than one group.

## Why grouping matters

You target a group, not a machine. "Run this on the `linux` group" is better
than naming seven servers, because when the fleet grows you change the group,
not every playbook.

## The EXODUS inventory

Location (in the main project):
- inventories/production/hosts.yml

Structure (conceptual):