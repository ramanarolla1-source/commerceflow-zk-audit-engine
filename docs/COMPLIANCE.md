Compliance Logic: Regulatory Rules Engine
1. Compliance Philosophy
CommerceFlow treats compliance as a deterministic, code-based certainty. We shift the burden of proof from human-led, retrospective audits to real-time, automated verification via our off-chain AI Agent and on-chain ZK-STARK Verifier.

2. Regulatory Alignment
Our rules engine is designed to accommodate the shifting landscape of cross-border trade regulations, including:

SAT (Servicio de Administración Tributaria) Compliance: Automated verification of invoice metadata against regional tax requirements.

Global Standard Protocol: Adherence to standard AML/KYC thresholds for SME settlement.

Real-Time Data Normalization: Standardizing disparate invoice formats (JSON/PDF) into a machine-readable compliance schema.

3. The Rules Engine Pipeline
The validator.py logic within the src/agents/ directory operates as follows:

Normalization: The AI Agent ingests unstructured trade documents and extracts key invoice features (e.g., counterparty ID, tax amount, date, currency).

Logic Mapping: The extracted data is run against our internal Compliance Rules Engine.

Verification: The engine checks for consistency against regulatory requirements (e.g., verifying if the tax calculation is correct and the counterparty is not on a restricted list).

Proof Trigger: If and only if all compliance checks pass, the validator triggers the ZK-STARK Prover to generate a cryptographic proof of compliance.

4. Separation of Concerns
Off-Chain Engine: Handles high-compute logic and flexible, frequently updated regulatory rules (enabling rapid updates as tax codes shift).

On-Chain Verifier: Maintains immutability and trust, acting only as the mathematical judge to ensure the off-chain audit was performed correctly.

5. Security & Data Privacy
The engine ensures that sensitive financial data is never exposed:

Data Minimization: Only the binary outcome of the compliance check (Pass/Fail) and relevant cryptographic hashes are sent to the Starknet Verifier.

Corporate Sovereignty: SME trade data remains under the custody of the enterprise, ensuring full corporate privacy.
