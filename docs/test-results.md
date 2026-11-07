# Hasil Pengujian

Packet Tracer 8.2.0.0162. Semua ping dijalankan dua kali dan yang dicatat adalah hasil kedua.
Nama file di kolom bukti adalah screenshot di folder `screenshots/`.

## 1. Konektivitas dan isolasi

| No | Dari | Ke | Harapan | Hasil | Bukti |
|----|------|----|---------|-------|-------|
| 1 | Guest 1 | DHCP | Dapat IP 192.168.50.x | Berhasil (192.168.50.12) | `01-guest-dhcp.png` |
| 2 | Guest 1 | Internet Server 203.0.113.2 | Berhasil | Berhasil, 0% loss, TTL 127 | `02-guest-ping-internet.png` |
| 3 | Guest 1 | VLAN 10, 20, 30, 40 | Gagal (ACL 100) | Destination host unreachable dari 192.168.50.1 | `03-guest-blocked.png` |
| 4 | Staff 1 | Finance 1 | Gagal (ACL Finance) | Unreachable dari 192.168.20.1 | `04-staff-to-finance.png` |
| 5 | HRD 1 | Database | Gagal | Unreachable dari 192.168.40.1 | `05-hrd-to-database.png` |
| 6 | Manager | Database | Berhasil | Berhasil, TTL 127 | `06-manager-to-database.png` |
| 7 | Finance 1 | Finance 2 | Berhasil | Berhasil | `07-finance-tests.png` |
| 8 | Finance 1 | Staff 1 | Berhasil | Berhasil, TTL 127 | `07-finance-tests.png` |
| 9 | Finance 1 | Internet Server | Berhasil | Berhasil, TTL 127 | `07-finance-tests.png` |
| 10 | Manager | Server Absensi | Berhasil | Berhasil, TTL 127 | `08-manager-to-absensi.png` |

## 2. Sebelum dan sesudah ACL Finance

| Kondisi | Staff 1 ke 192.168.30.11 |
|---------|--------------------------|
| Sebelum ACL | Berhasil, 4 dari 4 balasan, TTL 127 |
| Sesudah ACL | Gagal 100%, unreachable dari 192.168.20.1 |

## 3. Counter ACL

`show access-list ACL-FINANCE-OUT` setelah pengujian: permit VLAN 10 ke 30 sebanyak 4 match, echo-reply 8 match, `deny ip any any` 20 match.

`show access-list 100` setelah Guest kembali mendapat DHCP: rule DHCP 7 match, deny ke VLAN 10 sebanyak 12, VLAN 20 sebanyak 4, VLAN 30 sebanyak 8, VLAN 40 sebanyak 16, permit ke internet 16 match.

## 4. Trunk

`show interfaces trunk` di CORE-SW: Fa0/2 sampai Fa0/6 berstatus trunking dengan 802.1Q, VLAN 1, 10, 20, 30, 40, 50 aktif.

## 5. Bukti untuk bagian Yang Dipelajari

| Topik | Bukti |
|-------|-------|
| Kesalahan penulisan ACL Guest | `14-acl-guest-typo.png` |
| ACL 100 setelah rule DHCP ditambahkan | `10-acl100-dhcp-rule.png` |
| Guest 1 mendapat APIPA saat link AP mati | `13-guest-apipa-before-fix.png` |
| Port 0 Access Point kembali ke Auto | `12-ap-port0-auto.png` |
| Link Fa0/2 SW-GUEST up setelah diperbaiki | `11-sw-guest-fa0-2-up.png` |
| Counter ACL Finance, ACL 100, dan trunk | `09-acl-counters-and-trunk.png` |
