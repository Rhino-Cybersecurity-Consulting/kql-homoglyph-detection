# KQL Homoglyph Attack Detection & Mitigation

Production-ready Kusto Query Language (KQL) detection rules and optimization strategies for identifying Internationalized Domain Name (IDN) abuse, character spoofing, and homoglyph attacks in Microsoft Defender XDR and Azure Sentinel.

## Overview
Phishing attempts frequently leverage homoglyph attacks substituting standard characters with visually similar Unicode characters (e.g., replacement characters, non-ASCII symbols) to spoof legitimate corporate domains and trusted entities. This repository provides queries to scan for these anomalies across user creation events and email telemetry while prioritizing query performance.

## Included Queries

* **`user_creation_homoglyph.kql`**: Scans CloudAppEvents for newly created accounts featuring non-ASCII characters within their email domain.
* **`email_events_inbound.kql`**: Monitors inbound email traffic via EmailEvents to flag incoming messages originating from spoofed sender domains.
* **`optimized_watchlist_detection.kql`**: A high-performance, cost-optimized query utilizing Azure Sentinel Watchlists and risk-based scoping to minimize expensive regex operations.

## Performance Optimization
Running regex operations across massive enterprise telemetry datasets can be resource-intensive. Recommended best practices included in these scripts involve:
1. **Scoping by Risk Tier:** Prioritizing high-risk recipient groups (Executives, Finance, IT admins) before running broad queries.
2. **Watchlist Integration:** Utilizing safe-lists to filter out legitimate international domains prior to executing string matching.

## Usage
1. Clone or download the repository.
2. Navigate to the `/queries` directory.
3. Copy the desired `.kql` script into your Microsoft Defender Advanced Hunting or Microsoft Sentinel log analytics workspace.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
