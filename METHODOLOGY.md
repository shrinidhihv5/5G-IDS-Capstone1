# Methodology

## Goal

Classify 5G network traffic as **Benign, Flooding, Fuzzing, or Replay** and present the analysis through an interactive security dashboard.

## Method

### 1. Data Collection
Labelled CSV datasets representing benign traffic and multiple 5G attack scenarios are used for the project.

### 2. Schema Handling
The datasets do not all use the same CSV structure. The project supports canonical 5G feature CSVs as well as flow-based CSVs and maps both formats into one standardized feature representation.

### 3. Feature Extraction
Eight standardized features are used:

- `RequestMessages`
- `SuccessfulResponseMessages`
- `RequestResponseRatio`
- `RegistrationRate`
- `PDURequestRate`
- `RequestIAT`
- `ProcedureCodeNumber`
- `ProcedureCodeRate`

### 4. Normalization
Features are normalized using max scaling:

```text
x_normalized = x / x_max
```

### 5. Train/Test Split
The combined data is split approximately **80% for training and 20% for testing**.

### 6. Model Training
TensorFlow.js trains a four-class neural-network classifier in the browser. Fast mode uses a balanced subset and fewer epochs for practical demonstrations.

### 7. Evaluation
The dashboard displays model status and quick accuracy using a balanced test subset.

### 8. User Traffic Analysis
When a CSV is uploaded, the system parses it, maps its columns into the same eight features, normalizes the values, performs model inference, and displays malicious/legitimate totals, attack categories, risk information, and visualizations.
