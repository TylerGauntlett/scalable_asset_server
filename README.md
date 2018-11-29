## Introduction:

- This project uses nginx, docker and docker-compose to create multiple containers, all serving static assets.
  - This allows for horizontal scaling as the number of nginx connections increased.
- docker-compose is used to bring up all containers in the correct order.
- All assets in the `/web` directory will be served.

## Usage:

Clone Repo
```
git clone https://github.com/TylerGauntlett/scalable_asset_server.git
```
Start and Build Containers
```
docker-compose up -d --build
```
Stop Containers
```
docker-compose down
```

Verify everything is working by navigating to `http://localhost` where the `index.html` will load.

## Architecture:

```
--- worker_proxy (port 80)
    ├── worker_1 (port 3000)
    ├── worker_2 (port 3000)
    └── worker_3 (port 3000)
```

## Directory structure:

```
├── README.md
├── docker
│   └── nginx
│       ├── load_balancer
│       │   ├── Dockerfile
│       │   └── nginx.conf
│       └── worker
│           ├── Dockerfile
│           └── nginx.conf
├── docker-compose.yml
└── web
    └── index.html
```
