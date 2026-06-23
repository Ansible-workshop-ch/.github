````markdown
![Ansible Training Banner](images/backred1.png)

# Ansible & AAP Training Bootcamp

A hands-on, code-first Ansible training repo for Charter teams, especially Puppet engineers moving into Ansible and Ansible Automation Platform.

This bootcamp starts with the Ansible CLI first, then moves into AAP workflows. The labs are Linux-focused and designed for beginners.

Every module follows the same learning flow:

Definition -> Diagram / Workflow -> Hands-On Walkthrough -> Quiz -> Hands-On Lab

---

## Quick start

Clone the repo:

```bash
git clone https://github.com/Ansible-workshop-ch/bootcamp.git
cd bootcamp
````

Go into the lab directory:

```bash
cd lab
```

Edit the inventory file with your real lab host IP addresses or DNS names:

```bash
vim inventories/inventory.ini
```

Test Ansible connectivity:

```bash
ansible all -m ping
```

Run the first playbook:

```bash
ansible-playbook playbooks/module1_ping.yml
```

Run the webserver playbook:

```bash
ansible-playbook playbooks/module3_webserver.yml
```

The `lab/ansible.cfg` file already points to:

```text
inventories/inventory.ini
roles/
```

Because of that, run Ansible commands from inside the `lab/` directory unless instructed otherwise.

---

## Repo layout

```text
bootcamp/
├── README.md
├── images/
│   ├── backred1.png
│   └── nexticon.webp
├── lab/
│   ├── README.md
│   ├── ansible.cfg
│   ├── group_vars/
│   │   ├── all.yml
│   │   └── web.yml
│   ├── host_vars/
│   │   └── server1.yml
│   ├── inventories/
│   │   └── inventory.ini
│   ├── playbooks/
│   │   ├── module1_ping.yml
│   │   ├── module2_service.yml
│   │   ├── module3_webserver.yml
│   │   ├── module4_variables.yml
│   │   ├── module5_template_deploy.yml
│   │   ├── module6_role_apply.yml
│   │   └── module9_final_usecase.yml
│   ├── roles/
│   │   └── web_config/
│   │       ├── defaults/
│   │       │   └── main.yml
│   │       ├── handlers/
│   │       │   └── main.yml
│   │       ├── meta/
│   │       │   └── main.yml
│   │       ├── tasks/
│   │       │   └── main.yml
│   │       ├── templates/
│   │       │   └── index.html.j2
│   │       └── vars/
│   │           └── main.yml
│   ├── templates/
│   │   ├── index.html.j2
│   │   └── motd.j2
├── module01/
│   └── introduction.md
├── module02/
│   └── inventory-and-idempotency.md
├── module03/
│   └── playbook-basics.md
├── module04/
│   └── variables-and-facts.md
├── module05/
│   └── conditions-loops-handlers-templates.md
├── module06/
│   └── roles-and-code-first.md
├── module07/
│   └── aap-workflow.md
├── module08/
│   └── aap-inventories-surveys-troubleshooting.md
├── module09/
│   └── final-use-case.md
└── orientation.md
```

---

## Where to start

Start with the orientation page:

[Pre-Training Orientation](orientation.md)

Then continue through the modules in order.

---

## Course map

### Day 1 - Foundations and confidence

| Module | Topic                                                                                |
| ------ | ------------------------------------------------------------------------------------ |
| 1      | [Introduction and Architecture](module01/introduction.md)                            |
| 2      | [Inventory, Ad Hoc Commands, and Idempotency](module02/inventory-and-idempotency.md) |
| 3      | [Playbook Basics](module03/playbook-basics.md)                                       |

Day 1 outcome:

Students can explain what Ansible is, understand inventory basics, run ad hoc commands, and write a simple playbook.

---

### Day 2 - Core Ansible skills

| Module | Topic                                                                                         |
| ------ | --------------------------------------------------------------------------------------------- |
| 4      | [Variables and Facts](module04/variables-and-facts.md)                                        |
| 5      | [Conditions, Loops, Handlers, and Templates](module05/conditions-loops-handlers-templates.md) |
| 6      | [Roles and Code-First Structure](module06/roles-and-code-first.md)                            |

Day 2 outcome:

Students can use variables, facts, templates, loops, handlers, and roles to build reusable automation.

---

### Day 3 - AAP and applied workflow

| Module | Topic                                                                                                |
| ------ | ---------------------------------------------------------------------------------------------------- |
| 7      | [AAP Workflow](module07/aap-workflow.md)                                                             |
| 8      | [AAP Inventories, Surveys, and Troubleshooting](module08/aap-inventories-surveys-troubleshooting.md) |
| 9      | [Final Charter-Style Use Case](module09/final-use-case.md)                                           |

Day 3 outcome:

Students understand how Git-based Ansible code connects to AAP projects, inventories, job templates, surveys, schedules, and troubleshooting workflows.

---

## Lab playbook reference

Run these commands from inside the `lab/` directory.

| Playbook                                | Purpose                                        |
| --------------------------------------- | ---------------------------------------------- |
| `playbooks/module1_ping.yml`            | Test connectivity                              |
| `playbooks/module2_service.yml`         | Install and manage a service                   |
| `playbooks/module3_webserver.yml`       | Build a basic web server                       |
| `playbooks/module4_variables.yml`       | Practice variables and facts                   |
| `playbooks/module5_template_deploy.yml` | Use conditions, loops, templates, and handlers |
| `playbooks/module6_role_apply.yml`      | Apply the `web_config` role                    |
| `playbooks/module9_final_usecase.yml`   | Run the final applied use case                 |

Example:

```bash
cd lab
ansible-playbook playbooks/module3_webserver.yml
```

---

## Inventory

The sample inventory is located here:

```text
lab/inventories/inventory.ini
```

Example inventory structure:

```ini
[web]
server1 ansible_host=10.0.0.11
server2 ansible_host=10.0.0.12

[db]
dbserver1 ansible_host=10.0.0.21

[linux:children]
web
db

[linux:vars]
ansible_user=ansible
ansible_python_interpreter=/usr/bin/python3
```

Replace the sample IP addresses with real reachable lab hosts.

---

## Prerequisites

Students should have basic familiarity with:

* Linux command line
* SSH
* Git clone and basic Git workflow
* YAML basics
* Basic server administration concepts

No prior Ansible experience is required.

---

## Training scope

Covered in this bootcamp:

* What Ansible is
* Inventory
* Ad hoc commands
* Modules
* Idempotency
* Playbooks
* Variables
* Facts
* `group_vars`
* `host_vars`
* Conditions
* Loops
* Templates
* Handlers
* Roles
* Code-first repo structure
* AAP projects
* AAP inventories
* AAP job templates
* AAP surveys
* AAP schedules
* AAP job output
* Basic troubleshooting

Kept light:

* Windows automation
* WinRM
* PowerShell
* AWS-specific automation
* Deep NetBox integration
* HashiCorp Vault or CyberArk integration
* AAP installation
* Execution environment build process
* Deep Puppet-to-Ansible migration mapping

---

## Success criteria

By the end of this course, students should be able to say:

I understand how Ansible works. I can read and modify a playbook. I understand inventory, `group_vars`, `host_vars`, variables, facts, templates, handlers, and roles. I can run automation from the CLI and understand how the same workflow maps into AAP. I can read job output and troubleshoot common failures.

---

## Main GitHub module links

* [Orientation](orientation.md)
* [Module 1 - Introduction and Architecture](module01/introduction.md)
* [Module 2 - Inventory, Ad Hoc Commands, and Idempotency](module02/inventory-and-idempotency.md)
* [Module 3 - Playbook Basics](module03/playbook-basics.md)
* [Module 4 - Variables and Facts](module04/variables-and-facts.md)
* [Module 5 - Conditions, Loops, Handlers, and Templates](module05/conditions-loops-handlers-templates.md)
* [Module 6 - Roles and Code-First Structure](module06/roles-and-code-first.md)
* [Module 7 - AAP Workflow](module07/aap-workflow.md)
* [Module 8 - AAP Inventories, Surveys, and Troubleshooting](module08/aap-inventories-surveys-troubleshooting.md)
* [Module 9 - Final Charter-Style Use Case](module09/final-use-case.md)

```
```
