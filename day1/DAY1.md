# Day 1 — Core Identity & Network Foundation

## Objective

Deploy the core identity infrastructure for the enterprise lab.

Today's goal was to establish the Active Directory forest, configure core network services, and successfully join the first workstation to the domain.

---

# Virtual Machines

Running:

✔ CAS-DC-01

✔ CAS-IT-WS1

Powered Off:

CAS-DC-02

CAS-SRV-LIN01

CAS-DMZ-01

CAS-HR-WS1

CAS-KALI-01

---

# Infrastructure Deployed

## Active Directory

Forest

atlas.internal

Primary Domain Controller

CAS-DC-01

---

## Organizational Units

Atlas-Agency

• CAS-Endpoints

• CAS-Groups

• CAS-Staff

---

## Users

idrissi

meryem

---

## Security Groups

GS-Files-Creative-RW

GS-Files-HR-Private

GS-GMSA-Hosts

---

## DNS

Configured:

Forward Lookup Zone

Reverse Lookup Zones

Forwarders

A Records

CNAME Records

PTR Records

---

## DHCP

Configured:

VLAN10 Scope

VLAN20 Scope

VLAN30 Scope

Reservations

Lease Duration

Router Options

DNS Options

---

## Workstation

CAS-IT-WS1

Joined to:

atlas.internal

Moved into:

Atlas-Agency

CAS-Endpoints

Workstations

---

# Validation

The following tests completed successfully.

✔ Domain Join

✔ DNS Resolution

✔ DHCP Lease

✔ User Authentication

✔ Secure Channel

---

# Next

Day 2

Group Policy

DFS

FSRM

NTFS Permissions

Access-Based Enumeration
