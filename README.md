```mermaid
flowchart LR
 
%% --- Hauptlinien ---
subgraph DEV_Area[DEV-Bereich]
   
    FEAT_A[DEV Feature A]
    FEAT_B[DEV Feature B]
    FEAT_C[DEV Feature C]
   
end
 
subgraph MainBranches[Haupt-Branches 'Update BC27']
    STAGE[(STAGE)]
    MASTER[(MASTER)]
end
 
STAGE --> MASTER
 
FEAT_A --> STAGE
FEAT_B --> STAGE
FEAT_C --> STAGE
 
%% --- Releases ---
subgraph ReleaseBranches[Release-Branches 'BC26']
MASTER --> REL_20251028[Release-20251028]
MASTER --> REL_20251128[Release-20251128]
MASTER --> REL_20251228[Release-20251228]
end
%% Kunde läuft nur auf einem Release
REL_20251128 -->|Aktiv beim Kunden | KUNDE[(Produktivsystem Kunde A)]
 
%% --- Hotfix ---
REL_20251128 --> HF[Hotfix-Branch\nHF-KundeA]
HF --> REL_20251128
HF --> STAGE
...
