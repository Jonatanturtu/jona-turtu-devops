# Ansible Clase 35

## Mostrar variables de un host remoto.

Si necesito conocer que variables estan disponibles en el host remote, puedo usar el modulo `setup` de Ansible.

```bash
ansible -m setup <host>
ansible all -i inventory.ini -m setup
```

Links:

- [Todos los modulos de Ansible](https://docs.ansible.com/ansible/2.9/modules/list_of_all_modules.html)
- [Condicionales en Ansible](https://docs.ansible.com/ansible/2.9/user_guide/playbooks_conditionals.html)
- [Docu YAML](https://yaml.org/spec/1.2.2/)
- [YAML Syntax Ansible](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html)
- [Docu Jinja2](https://jinja.palletsprojects.com/en/2.11.x/templates/)
- 