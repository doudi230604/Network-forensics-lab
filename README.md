# Enterprise Network Forensics Lab

An offline-first framework that reconstructs suspicious network activity by combining packet analysis, protocol metadata and intrusion detection, then correlating the results into a single investigation timeline.

> **Status:** Design and early implementation. Features listed under *Planned* are not yet implemented.

---

## Overview

A single network tool shows only part of an incident. This project analyzes **the same PCAP** with three independent tools and merges their output, so each finding can be traced back to its source.

| Tool | Role |
|---|---|
| **TShark** | Packet-level inspection |
| **Zeek** | Connection and protocol metadata |
| **Suricata** | Signature-based detection |
| **Python** | Normalization, correlation, reporting |

## Workflow

```
PCAP/PCAPNG -> SHA-256 check -> TShark / Zeek / Suricata -> Python correlation -> SQLite -> Report
```

1. **Acquire:** capture traffic and record its SHA-256 hash.
2. **Verify:** confirm the hash before every analysis.
3. **Analyze:** process the same file with all three tools.
4. **Correlate:** join events using Community ID, the 5-tuple and a time window.
5. **Report:** produce a timeline with references to the source evidence.

## Planned Lab Scenario

A simulated workstation compromise in an isolated lab, in four phases:

1. **Reconnaissance:** port scan of a lab server
2. **Command and control:** periodic HTTP and DNS beaconing
3. **Exfiltration:** large file upload
4. **Encrypted repeat:** the same activity over TLS, to measure evidence loss

Each action is recorded in a ground-truth file so detection coverage can be measured.

## Objectives

- Analyze traffic from PCAP/PCAPNG files
- Extract packet details with TShark
- Generate network metadata with Zeek
- Detect suspicious activity with Suricata
- Correlate findings with Python
- Preserve evidence integrity with SHA-256
- Store results in SQLite
- Generate reproducible investigation reports

## Technology

| Component | Purpose |
|---|---|
| Python | Orchestration and correlation |
| TShark | Packet analysis |
| Zeek | Network metadata |
| Suricata | Intrusion detection |
| SQLite | Evidence storage |
| Git | Version control |

## Scope

**In scope:** offline PCAP analysis in a controlled lab.

**Out of scope:** live capture, production deployment, and decryption of encrypted traffic beyond available metadata.

## Documentation

The `docs/` folder covers architecture, methodology, research scope, evidence handling and testing.

## Ethical Use

Use only traffic that you own, have permission to analyze, or that is provided for research and educational purposes. All attack traffic in this project is generated against the author's own lab.

## License

See [LICENSE](https://github.com/doudi230604/Network-forensics-lab/blob/main/LICENSE).
