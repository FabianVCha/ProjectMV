
# ProjectMV — OpenClaw en Kubernetes

Infraestructura de OpenClaw multi-usuario sobre k3d con Kustomize y CI/CD via GitHub Actions.

## Estructura

ProjectMV/

├── base/                          # Plantilla común

│   ├── deployment.yaml

│   ├── service.yaml

│   ├── pvc.yaml

│   └── kustomization.yaml

├── overlays/

│   ├── fabian-morgan/             # Namespace usuario 1

│   │   ├── namespace.yaml

│   │   ├── configmap.yaml

│   │   ├── secret.yaml

│   │   └── kustomization.yaml

│   └── andres-vim/                # Namespace usuario 2

│       ├── namespace.yaml

│       ├── configmap.yaml

│       ├── secret.yaml

│       └── kustomization.yaml

└── .github/

└── workflows/

└── deploy.yml

## Agregar un nuevo usuario

1. Copiar overlay existente:

cp -r overlays/fabian-morgan overlays/nuevo-usuario

2. Editar namespace, configmap y secret

3. Agregar secrets en GitHub Actions

4. Agregar pasos en deploy.yml

5. Push a main

## DNS interno entre pods

http://openclaw-pod-b.fabian-morgan.svc.cluster.local:18789

## Pendientes

- [ ] Persistencia real (NFS provisioner)

- [ ] NATS broker entre namespaces

- [ ] Ingress con Traefik para Control UI

