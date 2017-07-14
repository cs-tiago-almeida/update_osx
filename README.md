update_osx
================

Ansible role para configurar Xcode e Command Line Tools no OS X.

Requisitos
------------
[Homebrew](http://brew.sh/) deve ser instalado
[mas](https://github.com/mas-cli/mas) para instalar aplicativos da Mac App Store.

Role Variables
--------------
-   update

Role Variables
--------------
-   mas_email: "Your appleid appstore user"
-   mas_password: "Your appleid appstore password"
-   mas_installed_app_ids: [] # Deprecated
-   mas_installed_apps:
  - { id: 1127487414, name: "macOS Sierra (10.12.5)" }
  - { id: 497799835, name: "Xcode (8.3.3)" }

mas_upgrade_all_apps: no
mas_signin_dialog: no

As credenciais da conta Mac App Store. Os aplicativos que você instalou devem ser comprados/registrados atraves desta conta.

O arquivo com estas credenciais está localizado em `vars/main.yml` criptografado com ansible-vault.

    mas_signin_dialog: no
Se configurado para _yes_, você deve especificar a variável `mas_email` mencionada acima que será preenchida automaticamente na caixa de diálogo e solicita que você digite sua senha, seguido do código de autorização 2FA(caso esteja habilitado na conta).

-   mas_installed_app_ids: [] # Deprecated
-   mas_installed_apps:
  - { id: 1127487414, name: "macOS Sierra (10.12.5)" }
  - { id: 497799835, name: "Xcode (8.3.3)" }

Aqui temos uma lista de aplicativos para garantir o que será instalado em nossa maquina. Você pode obter IDs para todas as aplicações instaladas existentes com o utilitário `mas list` e psequisar os IDs com `mas search [App Name]`.


Exemplo de um Playbook
----------------
---
- name: Install Server

  hosts: localhost
  gather_facts: no
  become_user: root

  roles:
    - cs-tiago-almeida.update

Licença
-------
MIT

Author Information
------------------
[Tiago de Almeida Francisco] (repo)
