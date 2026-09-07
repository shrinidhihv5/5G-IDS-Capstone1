# 5G IDS Workflow

```mermaid
flowchart TD
  S([Start]) --> A[Open 5G IDS Dashboard]
  A --> B[Load Prepared Training Data]
  B --> C[Train Balanced TensorFlow.js Model]
  C --> D{CSV Uploaded?}
  D -->|Yes| E[Parse CSV]
  E --> F[Map Dataset Schema to 8 Features]
  F --> G[Normalize Features]
  G --> H[ML Classification]
  H --> I[Benign / Flooding / Fuzzing / Replay]
  I --> J[Calculate Security Metrics]
  J --> K[Display KPIs, Charts and Attack Patterns]
  D -->|No| L[Wait for Dataset]
  L --> D
```

## Output Interpretation

- **Legitimate traffic:** predicted as Benign
- **Malicious traffic:** predicted as Flooding, Fuzzing, or Replay
- **Dashboard output:** traffic totals, detected attack categories, security information, and visual analytics
