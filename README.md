# Laravel Ansible Deploy

This project demonstrates automated deployment of a Laravel application using Ansible.

## Requirements

- Ansible
- PHP 8.2
- Nginx
- SQLite

## Directory Structure

```
.
├── ansible/            # Ansible configuration files
│   ├── inventory/     # Inventory files
│   ├── group_vars/    # Variable files
│   └── roles/         # Ansible roles
├── laravel-app/       # Laravel application
```

## Deployment

To deploy the application locally:

1. Install Ansible:
   ```bash
   sudo apt update
   sudo apt install ansible
   ```

2. Run the playbook:
   ```bash
   cd ansible
   ansible-playbook -i inventory/local site.yml
   ```

3. Access the application at http://localhost

## Roles

- **common**: Installs basic requirements
- **php**: Installs PHP and Composer
- **nginx**: Configures Nginx web server
- **laravel**: Deploys the Laravel application
