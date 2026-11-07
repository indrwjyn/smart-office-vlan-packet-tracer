# IP Addressing

| VLAN | Nama | Network | Gateway |
|------|------|---------|---------|
| 10 | Management | 192.168.10.0/24 | 192.168.10.1 |
| 20 | Staff | 192.168.20.0/24 | 192.168.20.1 |
| 30 | Finance | 192.168.30.0/24 | 192.168.30.1 |
| 40 | HRD | 192.168.40.0/24 | 192.168.40.1 |
| 50 | Guest | 192.168.50.0/24 | 192.168.50.1 |
| Link Internet | - | 203.0.113.0/30 | CORE-SW .1, Internet Server .2 |

## Perangkat

| Perangkat | VLAN | IP | Metode |
|-----------|------|----|--------|
| PC Manager | 10 | 192.168.10.11 | Static |
| Server Monitoring | 10 | 192.168.10.20 | Static |
| Printer IT | 10 | 192.168.10.30 | Static |
| PC Staff 1 sampai 3 | 20 | 192.168.20.11 sampai .13 | Static |
| Printer Staff | 20 | 192.168.20.30 | Static |
| PC Finance 1 dan 2 | 30 | 192.168.30.11 dan .12 | Static |
| Database | 30 | 192.168.30.100 | Static |
| PC HRD 1 dan 2 | 40 | 192.168.40.11 dan .12 | Static |
| Server Absensi | 40 | 192.168.40.100 | Static |
| Printer HRD | 40 | 192.168.40.30 | Static |
| Laptop Guest 1 sampai 3 | 50 | 192.168.50.11 sampai .13 | DHCP |
| Internet Server | - | 203.0.113.2/30 | Static |

DNS semua perangkat diarahkan ke 203.0.113.2.
Pool DHCP untuk VLAN 20, 30, dan 40 disiapkan untuk perangkat baru, sedangkan perangkat yang ada sekarang memakai IP static.
