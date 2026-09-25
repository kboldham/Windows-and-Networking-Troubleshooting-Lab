# Windows + Network Troubleshooting — Documentation Order

## Step 1 — Establish the client network baseline

![Screenshot](screenshots/01-ipconfig-network-baseline.png)

## Step 2 — Reproduce a domain/DNS failure

![Screenshot](screenshots/02-domain-join-dns-failure.png)

## Step 3 — Diagnose name resolution

![Screenshot](screenshots/03-nslookup-failure-external-dns.png)

## Step 4 — Verify internal DNS resolution

![Screenshot](screenshots/04-nslookup-success-local-dns.png)

This is a strong real troubleshooting sequence: failure -> investigation -> successful resolution.

## Step 5 — Document DHCP configuration

![Screenshot](screenshots/05-pfsense-dhcp-scope.png)

![Screenshot](screenshots/06-dhcp-static-mapping.png)

## Step 6 — Document firewall/segmentation policy

![Screenshot](screenshots/07-pfsense-firewall-rules.png)

## Step 7 — Validate segmentation

![Screenshot](screenshots/08-dmz-to-corporate-ping-blocked.png)

![Screenshot](screenshots/09-firewall-log-block-confirmed.png)

## Step 8 — Validate allowed application traffic

![Screenshot](screenshots/10-http-connectivity-verified-status-200.png)

The `setup-evidence/` folder contains the pfSense interface-assignment screenshot.