Ansible  vaullt is a functionality within Ansible that allows the encryption of sensititve information suchh as keys andd passwords.

Using password files
e.x. ansible-playbook playbook.yaml --vault-password-file pwd.txt


Using vault IDs
you can label your vault file with an identifier, which is called vault ID.  
e.x. ansible-vault create --vault-id vault1@prompt secret.yaml

secret: thisissecret

---
-   hosts: web
    become: yes
    tasks:
    -   include_vars: secret.yaml
    -   name:   Print the secret
        debug:
            msg:    "{{ secret }}"

Run the playbook with the --vault-id flag:
ansible-playbook playbook.yaml  ---vault-id vault1@prompt

You can use multiple vault IDs when you have multiple vault files.
ansible-playbook playbook.yaml --vault-id vault1@prompt --vault-id vault2@prompt

