%% ALPHA Protocol Architecture (versione potenziata)
flowchart TD
    %% Input
    A[Input] --> B

    %% Anchor & Aim
    B[Anchor & Aim] --> B1{Dati verificati?}
    B1 -- No --> Safe[Safe State: richiesta dati]
    B1 -- Yes --> C

    %% Logic
    C[Logic Engine: Structured CoT + PoT + ToT] --> D

    %% Litmus Test
    D[Litmus Test: Socratic Validation] --> D1{Contraddizioni?}
    D1 -- Yes --> Safe
    D1 -- No --> E

    %% Parameters & Risk
    E[Parameters & Risk Engine] --> E1{Rischio accettabile?}
    E1 -- No --> Safe
    E1 -- Yes --> F

    %% Hierarchy & Habitus
    F[Hierarchy & Habitus] --> F1{Ruolo decisionale}
    F1 -- Executive --> G[Output sintetico + rischio]
    F1 -- Analyst --> G[Output completo + modello]
    F1 -- Auditor --> G[Trace log + fonti]

    %% Actionable Analytics
    G --> H[Actionable Analytics: Decision Engine]
    H --> H1{Confidence > soglia?}
    H1 -- No --> Safe
    H1 -- Yes --> I[Execution / Esecuzione sicura]

    %% Safe State
    Safe[Safe State: Escalation / richiesta dati]

    %% Styling
    classDef critical fill:#f96,stroke:#333,stroke-width:2px;
    class Safe critical;
