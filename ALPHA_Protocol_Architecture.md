```mermaid
%% ALPHA Protocol — Architettura Completa con navigazione layer interattiva

flowchart TD
    %% Overview
    subgraph Overview["ALPHA Protocol - Overview"]
        Input[Input dati iniziali] --> Anchor
        Anchor[Anchor & Aim] --> Logic
        Logic[Logic Engine] --> Litmus
        Litmus[Litmus Test] --> Risk
        Risk[Parameters & Risk Engine] --> Hierarchy
        Hierarchy[Hierarchy & Habitus] --> Actionable
        Actionable[Actionable Analytics] --> Exec[Execution / Safe State]
        Exec --> Safe[Safe State fallback]
    end

    %% Anchor & Aim
    subgraph AnchorLayer["1 — Anchor & Aim"]
        A1[Input] --> B1[Retrieval-Augmented Generation + Data Validation]
        B1 --> B2{Dati verificati?}
        B2 -- No --> SafeA[Safe State: richiesta dati]
        B2 -- Yes --> Aim[Aim: Goal Formalization]
        Aim --> NextA[Passaggio a Logic Engine]
    end

    %% Logic Engine
    subgraph LogicLayer["2 — Logic Engine"]
        LogicE[Logic Engine: CoT + PoT + ToT]
        LogicE --> CoT[Structured Chain-of-Thought]
        LogicE --> PoT[Program-of-Thought]
        LogicE --> ToT[Tree-of-Thought / Scenario Expansion]
        CoT & PoT & ToT --> NextL[Output verso Litmus Test]
    end

    %% Litmus Test
    subgraph LitmusLayer["3 — Litmus Test"]
        LitmusE[Litmus Test: Socratic Validation]
        LitmusE --> Counter[Counterfactual Generation]
        Counter --> Adversarial[Adversarial Agent]
        Adversarial --> Contradiction{Contraddizioni rilevate?}
        Contradiction -- Yes --> SafeL[Safe State: escalation o revisione]
        Contradiction -- No --> NextLit[Passaggio a Parameters & Risk]
    end

    %% Parameters & Risk Engine
    subgraph RiskLayer["4 — Parameters & Risk Engine"]
        RiskE[Parameters & Risk Engine]
        RiskE --> Threshold{Rischio entro soglia?}
        Threshold -- No --> SafeR[Safe State: blocco esecuzione]
        Threshold -- Yes --> NextR[Passaggio a Hierarchy & Habitus]
    end

    %% Hierarchy & Habitus
    subgraph HierarchyLayer["5 — Hierarchy & Habitus"]
        HierarchyE[Hierarchy & Habitus: Role-conditioned Output]
        HierarchyE --> ExecRole{Ruolo decisionale}
        ExecRole -- Executive --> OutputExec[Output sintetico + esposizione rischio]
        ExecRole -- Analyst --> OutputAnalyst[Output completo + modello dettagliato]
        ExecRole -- Auditor --> OutputAudit[Logical Trace + Fonti]
        OutputExec & OutputAnalyst & OutputAudit --> NextH[Passaggio a Actionable Analytics]
    end

    %% Actionable Analytics
    subgraph ActionableLayer["6 — Actionable Analytics"]
        AA[Actionable Analytics: Decision Engine]
        AA --> Confidence{Confidence > soglia affidabilità?}
        Confidence -- No --> SafeAA[Safe State: escalation / richiesta dati]
        Confidence -- Yes --> ExecAA[Execution / Output sicuro]
    end

    %% Styling globale
    classDef critical fill:#f96,stroke:#333,stroke-width:2px;
    class Safe,SafeA,SafeL,SafeR,SafeAA critical;
