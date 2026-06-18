![OpenShift Banner](images/ansible-banner.png)

# Ansible & AAP Training

A hands-on, **code-first** training repo for Charter teams — especially Puppet engineers — moving into **Ansible** and **Ansible Automation Platform (AAP 2.6)**.

CLI first, AAP second. Linux-focused labs. Every module follows the same shape: **Definition → Diagram/Workflow → Hands-On Walkthrough → Quiz → Hands-On Lab.**

---

## Quick start

```bash
git clone <training-repo-url> charter-ansible-training
cd charter-ansible-training

# edit inventories/inventory.ini with your lab host details, then:
ansible all -m ping
ansible-playbook playbooks/module3_webserver.yml
```

`ansible.cfg` already points at `inventories/inventory.ini` and `roles/`, so you can run commands from the repo root without `-i`.

---

## Repo layout

```text
charter-ansible-training/
├── ansible.cfg                 # inventory + roles path defaults
├── inventories/inventory.ini   # sample lab inventory (edit me)
├── group_vars/                 # all.yml, web.yml
├── host_vars/                  # server1.yml (override example)
├── playbooks/                  # one playbook per module
├── roles/web_config/           # the reusable role (Module 6+)
├── templates/                  # shared Jinja2 templates
└── docs/                       # the course modules (start here)
```

---

## Course map

**Before Day 1:** [Pre-Training Orientation](docs/00-orientation.md)

### Day 1 — Foundations and confidence
| Module | Topic |
|--------|-------|
| 1 | [Introduction and Architecture](docs/module-01-introduction-architecture.md) |
| 2 | [Inventory, Ad Hoc Commands, Idempotency](docs/module-02-inventory-adhoc-idempotency.md) |
| 3 | [Playbook Basics](docs/module-03-playbook-basics.md) |

*Outcome: run basic Ansible commands and write a simple playbook.*

### Day 2 — Core Ansible skills
| Module | Topic |
|--------|-------|
| 4 | [Variables, Facts, group_vars, host_vars](docs/module-04-variables-facts-groupvars-hostvars.md) |
| 5 | [Conditions, Loops, Handlers, Templates](docs/module-05-conditions-loops-handlers-templates.md) |
| 6 | [Roles and Code-First Structure](docs/module-06-roles-code-first.md) |

*Outcome: build reusable automation with variables, templates, handlers, and roles.*

### Day 3 — AAP and applied workflow
| Module | Topic |
|--------|-------|
| 7 | [AAP Workflow for Operators](docs/module-07-aap-workflow-operators.md) |
| 8 | [AAP Inventories, Schedules, Surveys, Troubleshooting](docs/module-08-aap-inventories-schedules-surveys.md) |
| 9 | [Final Charter-Style Use Case](docs/module-09-final-charter-usecase.md) |

*Outcome: connect Git-based code to AAP, run job templates, troubleshoot output.*

---

## Playbook ↔ module reference

| Playbook | Module |
|----------|--------|
| `playbooks/module1_ping.yml` | 1 — connectivity |
| `playbooks/module2_service.yml` | 2 — install/start service |
| `playbooks/module3_webserver.yml` | 3 — first playbook |
| `playbooks/module4_variables.yml` | 4 — variables and facts |
| `playbooks/module5_template_deploy.yml` | 5 — condition/loop/template/handler |
| `playbooks/module6_role_apply.yml` | 6 — apply the role |
| `playbooks/module9_final_usecase.yml` | 9 — final use case |

---

## Prerequisites

Basic Linux CLI · basic SSH · basic Git (cloning) · access to the lab host and the AAP 2.6 sandbox. **No prior Ansible experience required.**

## Scope notes

**Emphasized:** CLI, inventory, ad hoc commands, playbooks, variables, facts, `group_vars`/`host_vars`, conditions, loops, templates, handlers, roles, Git structure, AAP projects/inventories/job templates/output, troubleshooting, code-first workflow.

**Kept light:** Windows / WinRM / PowerShell, AWS, deep NetBox, HashiCorp Vault / CyberArk, AAP installation, execution environment creation, deep Puppet-to-Ansible comparison.

---

## Success criteria

A graduate of this course can say: *I understand how Ansible works, I can read and modify a playbook, I understand `group_vars`/`host_vars`, I understand roles, I can run automation from CLI and from AAP, I can read AAP job output, and I can troubleshoot common failures.*

