# Azure Firewall Deployment – Etisalat-style NESA SC-07 Network Security Controls
**Project #12** from UAE Cloud Security Engineer Path (2026)

## Overview
Implemented a NESA-compliant Azure Firewall setup demonstrating boundary protection, forced tunneling, explicit allow rules, threat intelligence, and log ingestion to Log Analytics.  
Simulates critical infrastructure network controls used by Etisalat, DEWA, ADNOC.

## Architecture
- Hub VNet: 10.12.0.0/16
- AzureFirewallSubnet: 10.12.0.0/26 (mandatory)
- Workload-SN: 10.12.2.0/24 (spoke-like workload subnet)
- Azure Firewall: Standard SKU, Threat Intel = Deny mode
- Forced tunneling: UDR 0.0.0.0/0 → Firewall private IP
- Rules: Network (TCP 80/443 + UDP 53), Application (*.microsoft.com etc.)
- Logging: AzureDiagnostics → Log Analytics (NetworkRule + ApplicationRule)

## Key Steps Performed
- Created VNet + mandatory AzureFirewallSubnet (/26)
- Deployed Standard Azure Firewall + Public IP
- Created & associated Route Table for forced tunneling
- Configured Network & Application rule collections
- Deployed test VM in Workload-SN (no public IP)
- Generated & verified traffic (Allow microsoft.com, Deny others)
- Queried logs in Log Analytics showing Action, SourceIp, DestinationIp, Rule

## Evidence / Screenshots (add your own)
- [ ] VNet + subnets
- [ ] Firewall Overview (private IP, public IP, threat intel)
- [ ] Route table + association
- [ ] Rule collections (network + application)
- [ ] Test VM in Workload-SN
- [ ] curl success (microsoft.com) + fail (facebook.com)
- [ ] Log Analytics query output (Allow/Deny events)

## NESA SC-07 Mapping
- Boundary protection via explicit rules + forced tunneling
- Traffic filtering (allow-list only)
- Logging & monitoring for detection

