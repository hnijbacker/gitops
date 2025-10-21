graph TD

  %% Git Repositories
  subgraph Git["💾 Git Repositories"]
    G1["gitops/ (root repo)"]
    G2["frontend repo"]
    G3["backend repo"]
    G4["database repo"]
  end

  %% ArgoCD Components
  subgraph ArgoCD["🚀 ArgoCD"]
    A0["Root Application (App of Apps)"]
    A1["Environment App (dev / prod)"]
    A2["Frontend Application"]
    A3["Backend Application"]
    A4["Database Application"]
  end

  %% Kubernetes Cluster
  subgraph K8s["☸️ Kubernetes Cluster"]
    K1["frontend namespace"]
    K2["backend namespace"]
    K3["database namespace"]
  end

  %% Relations
  G1 --> A0
  A0 --> A1
  A1 --> A2
  A1 --> A3
  A1 --> A4

  A2 --> G2
  A3 --> G3
  A4 --> G4

  A2 --> K1
  A3 --> K2
  A4 --> K3

  %% Styling
  classDef git fill:#e0f7fa,stroke:#006064,color:#004d40
  classDef argocd fill:#e8eaf6,stroke:#283593,color:#1a237e
  classDef k8s fill:#f1f8e9,stroke:#33691e,color:#1b5e20

  class G1,G2,G3,G4 git
  class A0,A1,A2,A3,A4 argocd
  class K1,K2,K3 k8s
