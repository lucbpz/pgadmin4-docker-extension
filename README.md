# Docker Extension

PGAdmin4 extension for Docker Desktop

## Installation from Makertplace

Since Docker Desktop [v4.11.0](https://docs.docker.com/desktop/release-notes/#docker-desktop-4110) PGAdmin4 Extension is available in Marketplace page, just click on **+ Add Extensions**, find PGAdmin4 Extension, click Install and that's all; PGAdmin4 icon its shown at left side menu (Extensions Beta).

## Manual Installation

If you are using Docker Desktop [v4.10.1](https://docs.docker.com/desktop/release-notes/#docker-desktop-4101) or less  you can install just by executing:

```bash
$ docker extension install mochoa/pgadmin4-docker-extension:6.15.0
Extensions can install binaries, invoke commands and access files on your machine.
Are you sure you want to continue? [y/N] y
Image not available locally, pulling mochoa/pgadmin4-docker-extension:6.15.0...
Installing new extension "mochoa/pgadmin4-docker-extension:6.15.0"
Installing service in Desktop VM...
Setting additional compose attributes
VM service started
Installing Desktop extension UI for tab "PGAdmin4"...
Extension UI tab "PGAdmin4" added.
Extension "PGAdmin" installed successfully
```

**Note**: Docker Extension CLI is required to execute above command, follow the instructions at [Extension SDK (Beta) -> Prerequisites](https://docs.docker.com/desktop/extensions-sdk/#prerequisites) page for instructions on how to add it.

## Using PGAdmin Docker Extension

Once the extension is installed a new extension is listed at the pane Extension (Beta) of Docker Desktop.

By clicking at PGAdmin4 icon the extension main window will display the PGAdmin site once it has loaded.

First login will ask you for a master password for pgAdmin, fill it with your master password and click OK.

![Setting master password](docs/images/screenshot1.png?raw=true)

By clicking on Add New Server you can add PostgreSQL server running at Docker Desktop or externals, the IP for PostgreSQL running at Docker Desktop is available at the menu, Settings -> Resources -> Network -> Docker subnet, in my case is 192.168.65.0/24 so an internal IP for reaching PostgreSQL containers running at Docker Desktop will be 192.168.65.2, also there is an internal DNS name that resolve above IP named **host.docker.internal**.

![Docker Desktop Subnet](https://miro.medium.com/max/700/0*m4e0OEQprx_GgUA7)

Let see an example of PostgreSQL started using Docker Desktop Featured Images, PostgreSQL Overview shows this sample URL:

postgres://postgres:postgrespw@localhost:55000

which means for a PGAdmin Add New Server:

- Name: Test
- Hostname/address: host.docker.internal
- Port: 55000
- Maintenance database: postgres
- Username: postgres
- Password: postgrespw

by choosing Save Password, the above password is stored at PGAdmin4 internal storage and will remain until you de-install this extension.

![Screenshot of Add New Server](docs/images/screenshot4.png?raw=true)
