# Projeto de IaC: Provisionamento de Infraestrutura no Linux

![Badge de Linguagem](https://img.shields.io/badge/Language-Bash-blue.svg)
![Badge de Licença](https://img.shields.io/badge/License-MIT-green.svg)

## 📖 Sobre o Projeto

Este projeto, desenvolvido como parte da formação **Linux Essential da DIO**, demonstra os princípios de **Infraestrutura como Código (IaC)** através de um script de provisionamento em **Bash**.

O objetivo é automatizar a criação de toda a infraestrutura de usuários, grupos, diretórios e permissões em um novo servidor Linux. Ao executar um único arquivo, o ambiente é configurado de forma rápida, consistente e livre de erros manuais, garantindo que novas máquinas virtuais estejam prontas para uso em segundos.

## 🚀 Funcionalidades Principais

O script `iac.sh` realiza as seguintes ações:

- **Criação de Diretórios:** Cria os diretórios departamentais (`/adm`, `/ven`, `/sec`) e um diretório público (`/publico`).
- **Criação de Grupos:** Cria os grupos de usuários necessários: `GRP_ADM`, `GRP_VEN` e `GRP_SEC`.
- **Atribuição de Permissões:**
    - O usuário `root` é o dono de todos os diretórios criados.
    - O diretório `/publico` tem permissão total (`777`) para todos os usuários.
    - Os diretórios de grupo (`/adm`, `/ven`, `/sec`) possuem permissões restritas (`770`), permitindo acesso total apenas ao dono (root) e aos membros do respectivo grupo.
- **Criação de Usuários:** Cria usuários específicos para cada departamento e os adiciona aos seus respectivos grupos, definindo o `bash` como shell padrão.

## 🛠️ Estrutura de Diretórios e Permissões

A estrutura final de permissões foi desenhada para garantir a segurança e o isolamento entre os departamentos:

| Diretório | Dono | Grupo Proprietário | Permissões | Acesso                                |
| :-------- | :--- | :----------------- | :--------- | :------------------------------------ |
| `/publico`| `root` | `root`             | `777`      | Leitura/escrita para **todos** os usuários. |
| `/adm`    | `root` | `GRP_ADM`          | `770`      | Acesso total apenas para `root` e `GRP_ADM`. |
| `/ven`    | `root` | `GRP_VEN`          | `770`      | Acesso total apenas para `root` e `GRP_VEN`. |
| `/sec`    | `root` | `GRP_SEC`          | `770`      | Acesso total apenas para `root` e `GRP_SEC`. |

## ⚙️ Como Utilizar

Para executar o provisionamento, siga os passos abaixo:

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/WanderleiSI/Linux-Projeto1-IaC.git
    ```

2.  **Navegue até o diretório do projeto:**
    ```bash
    cd ./Linux-Projeto1-IaC

    ```

3.  **Dê permissão de execução ao script:**
    ```bash
    chmod +x iac.sh
    ```

4.  **Execute o script como superusuário:**
    ```bash
    sudo ./iac.sh
    ```

Após a execução, toda a estrutura de usuários, grupos e diretórios estará configurada.

## 💡 Conceitos Aplicados

Este projeto reforça conhecimentos fundamentais em administração de sistemas Linux e cultura DevOps:

- **Infraestrutura como Código (IaC):** Gerenciar e provisionar infraestrutura através de código, em vez de processos manuais.
- **Shell Scripting (Bash):** Automação de tarefas no terminal Linux.
- **Gerenciamento de Usuários e Grupos:** Comandos como `useradd`, `groupadd`, `usermod`, `userdel`, `groupdel`.
- **Sistema de Permissões do Linux:** Uso de `chmod` e `chown` para definir permissões de acesso granulares para dono, grupo e outros.
- **Automação:** A capacidade de executar o mesmo script várias vezes e obter sempre o mesmo resultado final.

---
