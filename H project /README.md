charts/kfp/
├── Chart.yaml                        # Chart metadata: name, version, description, maintainers
├── values.yaml                       # Default configuration values for prod and dev
├── .helmignore                       # Ignore unnecessary files in Helm package
├── README.md                          # Project description, deployment notes

├── crds/                             # All Custom Resource Definitions
│   ├── pipelines.yaml
│   ├── pipelineversions.yaml
│   ├── scheduledworkflow-crd.yaml
│   └── viewer-crd.yaml

├── templates/
│   ├── application/                  # Base app deployment
│   │   └── application.yaml

│   ├── cache/                        # Cache component
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   ├── role.yaml
│   │   ├── rolebinding.yaml
│   │   └── serviceaccount.yaml

│   ├── cache-deployer/               # Cache Deployer component
│   │   ├── deployment.yaml
│   │   ├── role.yaml
│   │   ├── rolebinding.yaml
│   │   ├── serviceaccount.yaml
│   │   └── cluster-scoped/           # Cluster-wide RBAC & SA
│   │       ├── clusterrole.yaml
│   │       ├── clusterrolebinding.yaml
│   │       └── serviceaccount.yaml

│   ├── apiserver/                     # ML Pipeline API server
│   │   ├── deployment.yaml
│   │   └── service.yaml

│   ├── persistence/                   # Persistence agent
│   │   └── deployment.yaml

│   ├── scheduler/                     # Scheduled workflow controller
│   │   └── deployment.yaml

│   ├── ui/                            # Pipeline UI
│   │   ├── deployment.yaml
│   │   └── service.yaml

│   ├── visualization/                 # Pipeline visualization
│   │   ├── deployment.yaml
│   │   └── service.yaml

│   ├── metadata/                      # Metadata server + envoy
│   │   ├── grpc-deployment.yaml
│   │   ├── grpc-service.yaml
│   │   ├── envoy-deployment.yaml
│   │   └── envoy-service.yaml

│   ├── metadata-writer/               # Writes metadata to DB
│   │   └── deployment.yaml

│   ├── webhook/                       # Admission webhooks
│   │   ├── mutating-webhook.yaml
│   │   └── validating-webhook.yaml

│   ├── configmaps/                    # Configs for UI, Launcher, etc.
│   │   ├── launcher-configmap.yaml
│   │   └── ui-configmap.yaml

│   ├── serviceaccounts/               # SA for all components
│   │   ├── apiserver-sa.yaml
│   │   ├── persistence-sa.yaml
│   │   ├── scheduler-sa.yaml
│   │   ├── ui-sa.yaml
│   │   ├── visualization-sa.yaml
│   │   ├── metadata-writer-sa.yaml
│   │   ├── pipeline-runner-sa.yaml
│   │   ├── container-builder-sa.yaml
│   │   ├── viewer-sa.yaml
│   │   ├── cache-sa.yaml
│   │   └── cache-deployer-sa.yaml

│   ├── rbac/                          # RBAC for all components
│   │   ├── apiserver-rbac.yaml
│   │   ├── persistence-rbac.yaml
│   │   ├── scheduler-rbac.yaml
│   │   ├── ui-rbac.yaml
│   │   ├── metadata-writer-rbac.yaml
│   │   ├── pipeline-runner-rbac.yaml
│   │   ├── public-configmap-rbac.yaml
│   │   ├── cache-role.yaml
│   │   └── cache-deployer-role.yaml

│   ├── database/
│   │   ├── postgresql/
│   │   │   ├── postgres-deployment.yaml
│   │   │   ├── postgres-service.yaml
│   │   │   ├── postgres-pvc.yaml
│   │   │   └── postgres-secret.yaml
│   │   ├── mysql/
│   │   │   ├── mysql-deployment.yaml
│   │   │   ├── mysql-service.yaml
│   │   │   ├── mysql-pvc.yaml
│   │   │   └── mysql-secret.yaml
│   │   └── metadata-db/
│   │       ├── metadata-db-deployment.yaml
│   │       ├── metadata-db-service.yaml
│   │       ├── metadata-db-pvc.yaml
│   │       └── metadata-db-secret.yaml

│   ├── istio/
│   │   ├── destination-rule.yaml
│   │   ├── istio-authorization-policy.yaml
│   │   ├── virtual-service.yaml
│   │   └── pipeline-specific/
│   │       └── istio-authorization-config.yaml

│   ├── scripts/                        # Helper scripts
│   │   ├── sync.py
│   │   ├── test_sync.py
│   │   └── run_test.sh
│   └── _helpers.tpl                     # Helm template helpers
