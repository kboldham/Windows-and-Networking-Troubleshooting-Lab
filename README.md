# Windows and Network Troubleshooting Lab

## Project Overview

This lab documents hands-on troubleshooting of Windows network connectivity, DNS, DHCP, firewall rules, network segmentation, and application connectivity in a virtualized environment.

The goal was to practice identifying network problems from observable symptoms, using command-line and firewall tools to investigate the issue, making configuration changes, and verifying the expected result.

## Scenario 1 — Troubleshoot Domain DNS Resolution

I first reviewed the Windows client's network configuration using `ipconfig /all` to establish the assigned IP address, DNS server, default gateway, and DHCP information.

![Network Baseline](screenshots/01-ipconfig-network-baseline.png)

The workstation was unable to locate the Active Directory domain during the domain-join process.

![Domain Join DNS Failure](screenshots/02-domain-join-dns-failure.png)

I used `nslookup` to investigate name resolution and found that the client was querying an external DNS server instead of the internal domain DNS server.

![DNS Resolution Failure](screenshots/03-nslookup-failure-external-dns.png)

After correcting the DNS configuration, I repeated the lookup and successfully resolved the internal domain.

![Successful Internal DNS Resolution](screenshots/04-nslookup-success-local-dns.png)

### Result

The issue was isolated to incorrect DNS configuration. After correcting the DNS server settings, the workstation successfully resolved the internal domain.

---

## Scenario 2 — Review DHCP Configuration

I reviewed the pfSense DHCP configuration to understand the address pool assigned to client devices and configured a static mapping for a test system.

![pfSense DHCP Scope](screenshots/05-pfsense-dhcp-scope.png)

![DHCP Static Mapping](screenshots/06-dhcp-static-mapping.png)

### Result

The test system was assigned network settings through the configured DHCP environment, and the static mapping provided a consistent address for the selected client.

---

## Scenario 3 — Validate Network Segmentation

I reviewed pfSense firewall rules controlling traffic between the test network segments.

![pfSense Firewall Rules](screenshots/07-pfsense-firewall-rules.png)

I then tested connectivity from the DMZ segment to the corporate segment. The ping request failed as expected.

![Blocked DMZ to Corporate Ping](screenshots/08-dmz-to-corporate-ping-blocked.png)

The pfSense firewall log confirmed that the traffic was blocked by the configured rule.

![Firewall Log Confirming Block](screenshots/09-firewall-log-block-confirmed.png)

### Result

The test confirmed that the firewall policy was preventing traffic between the selected network segments as intended.

---

## Scenario 4 — Verify Allowed Application Traffic

I tested HTTP connectivity to confirm that permitted application traffic could successfully reach the destination.

![HTTP Connectivity Verification](screenshots/10-http-connectivity-verified-status-200.png)

### Result

The request returned HTTP status 200, confirming successful application-layer connectivity.

---

## Skills Practiced

- Windows network troubleshooting
- TCP/IP configuration
- DNS troubleshooting
- DHCP
- `ipconfig`
- `nslookup`
- pfSense firewall rules
- Network segmentation
- Connectivity testing
- Firewall log review
- Troubleshooting documentation
