# Network Connectivity Diagnostics

## Objective
Verify network connectivity, DNS resolution, and basic network path connectivity using Windows PowerShell.

## Environment
- Operating System: Windows 11
- Virtual Machine: SOC-Windows
- Tools: PowerShell networking commands

## Tests and Results

| Test | Command | Result |
|---|---|---|
| External IP connectivity | `ping -n 20 8.8.8.8` | 20 packets received, 0% packet loss, 15 ms average response time |
| DNS resolution | `nslookup google.com` | Hostname successfully resolved |
| Hostname connectivity | `ping google.com` | 4 packets received, 0% packet loss, 38 ms average response time |
| Network path | `tracert -d 8.8.8.8` | Destination reached in the recorded test |

## Findings
The recorded tests demonstrated successful connectivity to the tested external IP address and hostname. DNS resolution succeeded, and the network path test reached the destination.

## Conclusion
No connectivity or DNS resolution failure was observed during these tests. The results represent the network conditions at the time of testing.

## Evidence
Supporting screenshots are saved locally in the project's `screenshots/` folder and can be added to the repository later.

## Skills Demonstrated
- Network troubleshooting
- DNS diagnostics
- PowerShell
- Connectivity testing
- Technical documentation
