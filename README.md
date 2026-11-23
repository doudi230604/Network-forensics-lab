# Enterprise Network Forensics Lab

An integrated, offline-first network forensics framework for
investigating suspicious network activity through packet analysis,
network metadata extraction, intrusion detection, evidence correlation,
and incident reconstruction.

## Project Objectives

- Analyze network traffic from PCAP/PCAPNG files.
- Extract packet-level information using TShark.
- Generate network metadata using Zeek.
- Identify suspicious activity using Suricata.
- Correlate findings using Python.
- Preserve evidence integrity using SHA-256.
- Store structured investigation results in SQLite.
- Generate reproducible forensic investigation reports.

## Architecture

The proposed workflow uses three independent analysis tools:

1. TShark: packet-level inspection.
2. Zeek: network connection and protocol metadata.
3. Suricata: signature-based intrusion detection.

Python will normalize and correlate their outputs.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Orchestration and correlation |
| TShark | Packet analysis |
| Zeek | Network metadata |
| Suricata | Intrusion detection |
| SQLite | Evidence storage |
| SHA-256 | Integrity verification |
| Git | Version control |

## Project Status

Currently in the design and initial implementation phase.

Planned capabilities are not yet claimed as implemented.

## Repository Structure

See the `docs/` directory for architecture, methodology,
research scope, evidence handling, and testing documentation.

## Investigation Scope

The initial implementation focuses on offline PCAP analysis.
Live capture, encrypted traffic inspection beyond available metadata,
and production deployment are outside the initial scope.

## Ethical Use

Use only traffic that you own, have permission to analyze,
or that is explicitly provided for research and educational use.

## License

See [LICENSE](LICENSE).
