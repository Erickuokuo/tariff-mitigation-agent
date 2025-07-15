## FEATURE

Tariff Mitigation Agent – An intelligent CLI + chat-integrated system to analyze a Bill of Materials (BOM) and recommend tariff-saving strategies.

### Core Capabilities:
- 📦 **BOM Analysis via CLI or chat**  
  - Accepts CSV, JSON, XML, Excel formats  
  - Supports manual text input or file upload  
  - Optionally integrates with ERP systems

- 🧠 **HS Code Mapping (AI-assisted)**  
  - Uses keyword matching or AI classifier (future)  
  - Fallback to "UNKNOWN" for unmapped components

- 💰 **Tariff Lookup**  
  - Fetch tariff rates by region (US, EU, etc.)  
  - Mocked or API-integrated (e.g. WTO, USITC)

- 🧭 **Sourcing Strategy Suggestion**  
  - Compares tariffs across regions  
  - Recommends most cost-effective sourcing option

- 📄 **Justification + Override**  
  - Explains suggested strategy  
  - User can override recommendations  
  - Saves all overrides in `results.json`

---

## ADVANCED FEATURES

- 🧩 **Dynamic Dashboard Widgets**  
  - Show/hide based on user context (e.g., status, alternatives, sourcing)

- 🗂️ **Multi-Format Input Support**  
  - Supports file upload (CSV, Excel, JSON, XML) or chat-based description

- ⚙️ **Invisible Agent Orchestration**  
  Powered by multi-agent system:
  - **Router Agent** – Determines intent & routes task  
  - **Context Agent** – Maintains conversation state  
  - **Classification Agent** – Determines HS code  
  - **Sourcing Agent** – Recommends mitigation strategies

---

## EXAMPLES

### 💬 Example 1: Conversational BOM Analysis

**User Input**:
> "Analyze BOM_Q3_2024.xlsx for tariff optimization"  
> 📁 User uploads file

**System**:
- "Processing your BOM with 1,247 components..."
- Shows dynamic processing widget → Cost analysis dashboard
- "Found $600K in potential savings. Bluetooth modules are high-tariff items."

**Follow-up**:
> "Show me alternatives for the bluetooth modules"

**System**:
- Shows sourcing table
- "Sourcing from Mexico could save $85K annually. Compliance steps: [Link]"

---

### 🎤 Example 2: Voice-Activated Component Check

**User**:  
> "What's the tariff on this component?"  
> 📸 Uploads image

**System**:  
- Uses image classification → maps to HS code  
- Shows region-specific tariff rates & recommendations

---

## DOCUMENTATION

- **Spec File**: `Tariff_Mitigation_Agent_CLI_Spec.md`
- **Input Format**:  
  - Required CSV headers: `component_name`, `quantity`  
  - Case-insensitive mapping  
  - Supports Excel, JSON, XML with field normalization

- **Tariff Table (Mocked)**:
  ```json
  {
    "9026.10.20": {"US": 3.0, "EU": 2.0},
    "8533.21.00": {"US": 2.5, "EU": 1.2},
    "UNKNOWN": {"US": 5.0, "EU": 5.0}
  }
Output Format:
results.json includes:

component_name

hs_code

tariffs

suggested_strategy

justification

override (if any)

PRIMARY REFERENCES
World Trade Organization (WTO) – https://www.wto.org

World Customs Organization (WCO) – HS Classification

US Trade Representative (USTR) – Trade Agreements

USITC – Tariff Database

DATA SOURCES
UN Comtrade API – https://comtrade.un.org/data/dev/portal

TradeMap API – https://api.trademap.org

Foreign Trade HS Code DB – https://www.foreign-trade.com/reference/hscode.htm

WITS (World Bank) – https://wits.worldbank.org/

EU TARIC – https://ec.europa.eu/taxation_customs/dds2/taric/

OTHER CONSIDERATIONS
Handle missing/invalid CSV columns gracefully

Match component names case-insensitively

Allow full CLI use with argparse or click

Timestamp results and save to output/results_YYYYMMDD.json

Add --no-prompt flag for non-interactive use

Logs should include component count and error summaries

FUTURE EXTENSIONS (Out of Scope for Initial Version)
Real-time tariff APIs

Real HS classification via AI model or API

Web-based UI or dashboard

API for embedding into ERPs or PLMs