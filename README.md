# Nextcloud-Stack

This project sets up a self-hosted Nextcloud instance using Docker Compose. The stack includes:
- **MariaDB**: Database backend for Nextcloud.
- **Nextcloud**: A self-hosted file sharing service.
- **ClamAV**: Antivirus scanning for uploaded files.
- **Nginx Proxy Manager**: Reverse proxy with SSL certificate management.

## Setup Instructions

### Step 1: Clone the Repository
```bash
git clone https://github.com/jmo55/nextcloud-stack
cd nextcloud-stack
``` 

### Step 2: Create a .env File

Create a .env file in the root of the project directory to store sensitive environment variables.

Example .env file:

```bash
MYSQL_ROOT_PASSWORD=your_root_password
MYSQL_DATABASE=nextcloud
MYSQL_USER=nextcloud_user
MYSQL_PASSWORD=your_user_password
```

NOTE:

If you prefer, you can directly use the docker-compose.yml file without creating a .env file. To do this:

Replace the placeholder values (EnterYourPasswordHere) in the docker-compose.yml file with your actual credentials.
Run the next step as usual.

### Step 3: Update docker-compose.yml

The docker-compose.yml file is preconfigured to use the .env file. You can review it to ensure it meets your needs.

### Step 4: Start the Containers

Run the following command to start the services:

```bash
docker-compose up -d
```

### Step 5: Verify the Setup

    Access Nextcloud: Navigate to http://<your-server-ip> in your browser to complete the setup wizard.
    Access Nginx Proxy Manager: Navigate to http://<your-server-ip>:81 for the admin interface.
	
Persistent Storage

This project uses Docker volumes to persist data:

    db_data: Stores MariaDB data.
    nextcloud_data: Stores Nextcloud files.
    nginx_data and nginx_letsencrypt: Store Nginx Proxy Manager data and certificates.
	
Updating Services

To update the Docker images, pull the latest versions and recreate the containers:

```bash
docker-compose pull
docker-compose up -d
```
