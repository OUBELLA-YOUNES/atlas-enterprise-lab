# Verification Commands

## Domain Controller

ipconfig /all

dcdiag

Get-Service DNS

Get-Service DHCPServer

Get-ADDomain

Get-DhcpServerv4Scope

---

## Client

ipconfig /all

whoami

hostname

gpupdate /force

gpresult /r

nltest /dsgetdc:atlas.internal

ping cas-dc-01

nslookup atlas.internal
