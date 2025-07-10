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

### Local Deployment

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

### Remote Deployment

To deploy to a remote server:

1. Set up SSH key authentication:
   ```bash
   ssh-keygen -t rsa -b 4096
   ssh-copy-id your_ssh_user@your_server_ip
   ```

2. Update the production inventory file:
   - Edit `ansible/inventory/production`
   - Replace `your_server_ip` with your actual server IP
   - Replace `your_ssh_user` with your SSH username

3. Update production variables:
   - Edit `ansible/group_vars/production/main.yml`
   - Set your domain name in `nginx_server_name`
   - Configure database credentials
   - Adjust other settings as needed

4. Install SSL certificate (recommended):
   ```bash
   ssh your_ssh_user@your_server_ip
   sudo apt install certbot
   sudo certbot certonly --nginx -d your-domain.com
   ```

5. Run the playbook:
   ```bash
   cd ansible
   ansible-playbook -i inventory/production site.yml
   ```

6. Access your application at https://your-domain.com

## Roles

- **common**: Installs basic requirements
- **php**: Installs PHP and Composer
- **nginx**: Configures Nginx web server
- **laravel**: Deploys the Laravel application
