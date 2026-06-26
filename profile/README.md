
![Ansible Training Banner](images/ansible-banner.png)

![Ansible Training Banner](images/ansible-banner.png)

# Ansible & AAP Training Bootcamp

A hands-on, code-first Ansible training repo for Charter teams, especially Puppet engineers moving into Ansible and Ansible Automation Platform.

This bootcamp starts with the Ansible CLI first, then moves into AAP workflows. The labs are Linux-focused and designed for beginners.

Every module follows the same learning flow:

```text
Definition -> Diagram / Workflow -> Hands-On Walkthrough -> Quiz -> Hands-On Lab
```

---

## Quick Start

Clone the repo:

```bash
git clone https://github.com/Ansible-workshop-ch/bootcamp.git
cd bootcamp
```

Base repo: [Bootcamp](https://github.com/Ansible-workshop-ch/bootcamp)

---

## Start Here

* [Orientation](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/orientation.md)

---

## Course Modules

### Day 1 - Foundations

* [Module 1 - Introduction and Architecture](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module01/introduction.md)
* [Module 2 - Inventory, Ad Hoc Commands, and Idempotency](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module02/inventory-and-idempotency.md)
* [Module 3 - Playbook Basics](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module03/playbook-basics.md)

### Day 2 - Core Ansible Skills

* [Module 4 - Variables and Facts](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module04/variables-and-facts.md)
* [Module 5 - Conditions, Loops, Handlers, and Templates](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module05/conditions-loops-handlers-templates.md)
* [Module 6 - Roles and Code-First Structure](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module06/roles-and-code-first.md)

### Day 3 - AAP and Applied Workflow

* [Module 7 - AAP Workflow](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module07/aap-workflow.md)
* [Module 8 - AAP Inventories, Surveys, and Troubleshooting](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module08/aap-inventories-surveys-troubleshooting.md)
* [Module 9 - Final Charter-Style Use Case](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module09/final-use-case.md)

---

## Lab Folder

All runnable Ansible lab code lives under the `lab/` directory.

Run lab commands from there:

```bash
cd bootcamp/lab
```

Lab references:

* [Lab README](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/README.md)
* [Ansible Config](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/ansible.cfg)
* [Inventory File](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/inventories/inventory.ini)
* [Playbooks Folder](https://github.com/Ansible-workshop-ch/bootcamp/tree/main/lab/playbooks)
* [Roles Folder](https://github.com/Ansible-workshop-ch/bootcamp/tree/main/lab/roles)

---

## Lab Inventory Model

The lab includes both Ubuntu-based and Rocky/RHEL-based targets.

```text
ubuntu_web
  container1
  container2
  container3

rhel_web
  rhel1
  rhel2
  rhel3

web
  ubuntu_web
  rhel_web

linux
  web
```

This allows one playbook to work across different Linux distributions.

Ubuntu/Debian uses:

```text
Package: apache2
Service: apache2
```

Rocky/RHEL uses:

```text
Package: httpd
Service: httpd
```

The playbooks use variables instead of hardcoding package and service names:

```yaml
name: "{{ package_name }}"
```

```yaml
name: "{{ service_name }}"
```

The correct values come from group variables under:

```text
lab/inventories/group_vars/
```

---

## Playbook References

All playbooks are located under:

```text
lab/playbooks/
```

Core playbooks:

* [module1_ping.yml](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/playbooks/module1_ping.yml)
* [module2_service.yml](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/playbooks/module2_service.yml)
* [module3_webserver.yml](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/playbooks/module3_webserver.yml)
* [module4_variables.yml](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/playbooks/module4_variables.yml)
* [module5_template_deploy.yml](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/playbooks/module5_template_deploy.yml)
* [module6_role_apply.yml](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/playbooks/module6_role_apply.yml)
* [module9_final_usecase.yml](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/playbooks/module9_final_usecase.yml)

---

## Bonus Lessons

Bonus lessons are optional. They can be used for instructor demos, extra practice, or advanced discussion if time allows.

### NetBox Source of Truth

NetBox introduces the idea of using an external source of truth for infrastructure data.

* [NetBox Source of Truth Bonus](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/bonus/netbox-source-of-truth.md)

Main idea:

```text
NetBox tells Ansible what exists.
Ansible performs the automation.
AAP controls and runs the automation.
```

### EC2 Creation with Ansible

This bonus lesson teaches that Ansible can create cloud infrastructure directly, such as AWS EC2 instances.

* [Creating EC2 with Ansible](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/bonus/creating-ec2-with-ansible.md)
* [EC2 exact_count Playbook](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/playbooks/ec2_exact_count.yml)

Main idea:

```text
Ansible can configure existing hosts.
Ansible can also create cloud resources by calling cloud APIs.
```

This lesson explains the difference between:

```yaml
count: 1
```

and:

```yaml
exact_count: 1
```

`count: 1` can create another instance every time the playbook runs if used carelessly.

`exact_count: 1` is safer for repeatable automation because it tells Ansible:

```text
Make sure exactly one matching instance exists.
```

> Warning: The EC2 bonus lab can create real AWS resources. Use only in a safe AWS sandbox or instructor-controlled demo environment.

---

## Recommended Learning Flow

```text
1. Read the orientation
2. Start with Module 1
3. Run CLI labs from bootcamp/lab
4. Practice ad hoc commands
5. Move into playbooks
6. Learn variables, facts, templates, handlers, and roles
7. Move into AAP workflow
8. Finish with the final use case
9. Review bonus lessons if time allows
```

---

Course modules: 
- [Module 1 - Introduction and Architecture](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module01/introduction.md)
- [Module 2 - Inventory, Ad Hoc Commands, and Idempotency](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module02/inventory-and-idempotency.md)
- [Module 3 - Playbook Basics](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module03/playbook-basics.md)
- [Module 4 - Variables and Facts](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module04/variables-and-facts.md)
- [Module 5 - Conditions, Loops, Handlers, and Templates](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module05/conditions-loops-handlers-templates.md)
- [Module 6 - Roles and Code-First Structure](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module06/roles-and-code-first.md)
- [Module 7 - AAP Workflow](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module07/aap-workflow.md)
- [Module 8 - AAP Inventories, Surveys, and Troubleshooting](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module08/aap-inventories-surveys-troubleshooting.md)
- [Module 9 - Final Charter-Style Use Case](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/module09/final-use-case.md)

---

Lab folder:
  - [Lab README](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/README.md)
  - [Ansible Config](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/ansible.cfg)
  - [Inventory File](https://github.com/Ansible-workshop-ch/bootcamp/blob/main/lab/inventories/inventory.ini)
  - [Playbooks Folder](https://github.com/Ansible-workshop-ch/bootcamp/tree/main/lab/playbooks)
  - [Roles Folder](https://github.com/Ansible-workshop-ch/bootcamp/tree/main/lab/roles)
