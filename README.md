# Dynamic OSPF Routing Project

This project demonstrates **Dynamic OSPF (Open Shortest Path First)** routing across 4 Cisco routers with different networks, showing how OSPF automatically discovers and advertises routes without static configuration.

## 📌 Project Overview
- **Routing Protocol:** OSPF (Process ID 10)
- **Routers:** 4 (Router0, Router1, Router2, Router3)
- **Networks:**
  - 10.0.0.0/24 (Backbone / Transit Network)
  - 192.168.10.0/24 (Router0 LAN)
  - 192.168.40.0/24 (Router2 LAN)
  - 192.168.50.0/24 (Router1 LAN)
  - 172.16.0.0/16 (Router3 LAN)
- **OSPF Area:** 0 (Backbone)
- **OSPF Router IDs:**
  - Router0 → 9.9.9.9
  - Router1 → 4.4.4.4
  - Router2 → 3.3.3.3
  - Router3 → 1.1.1.1

## ⚙️ Router Configurations (Example)
### Router0
```bash
router ospf 10
 router-id 9.9.9.9
 network 192.168.10.0 0.0.0.255 area 0
 network 10.0.0.0 0.0.0.255 area 0
```

### Router1
```bash
router ospf 10
 router-id 4.4.4.4
 network 192.168.50.0 0.0.0.255 area 0
 network 10.0.0.0 0.0.0.255 area 0
```

### Router2
```bash
router ospf 10
 router-id 3.3.3.3
 network 192.168.40.0 0.0.0.255 area 0
 network 10.0.0.0 0.0.0.255 area 0
```

### Router3
```bash
router ospf 10
 router-id 1.1.1.1
 network 172.16.0.0 0.0.255.255 area 0
 network 10.0.0.0 0.0.0.255 area 0
```

## 📊 Verification Commands
- `show ip route` → Check OSPF learned routes
- `show ip ospf neighbor` → Verify OSPF adjacency
- `ping` between all LAN networks → Verify connectivity

## 📌 Notes
- This is a **Dynamic OSPF project** (no static routes used).
- All routers are in **Area 0**, forming a full adjacency.
- DR/BDR election occurs automatically on the shared network (10.0.0.0/24).

## 🖥️ Topology
(Attach topology screenshot here)

---
✅ **All routes are dynamically discovered via OSPF.**
