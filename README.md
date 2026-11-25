# Network Administration Interview Questions

Question set for evaluating a software developer's readiness to transition into a network administration role supporting Dell Linux infrastructure: Proxmox, Kubernetes, Docker, managed switches, uplink routing with multiple class C blocks, and VoIP.

Use alongside practical exercises where possible. Score each answer against the rubric at the end.

---

## 1. Proxmox Virtualisation

1. **Node failure.** One Proxmox node in a three-node cluster dies hard — no graceful shutdown. Walk me through exactly what happens to the VMs on that node, what the cluster does automatically, and what your first five minutes of response look like.

2. **Quorum.** Explain quorum in a Proxmox cluster. What happens if you lose quorum, and how do you recover from a split-brain scenario where two nodes think they're the primary?

3. **Storage.** You have local ZFS on each node plus a shared NFS datastore. A VM's disk image lives on local storage and the VM is migrated to another node. What breaks, and how do you prevent it?

4. **Backups.** How would you design a backup strategy for a mixed Proxmox estate — some VMs critical, some disposable? Cover scheduling, retention, offsite copies, and restore testing.

5. **Updates.** How do you patch Proxmox hosts without taking production VMs down? What's your approach to kernel updates and reboot windows?

6. **Networking in Proxmox.** Explain Linux bridges, VLANs, and OVS in the Proxmox context. When would you choose OVS over the default Linux bridge?

7. **Resource isolation.** A VM is starving other VMs of CPU. How do you diagnose and fix it using Proxmox tools?

## 2. Kubernetes

8. **Pod won't schedule.** A pod is stuck in Pending. Walk through your diagnostic process from `kubectl describe` to resolution, covering taints, tolerations, node selectors, affinity, resource requests versus limits, and storage class issues.

9. **Rolling updates.** Explain how a rolling update works under the hood. What happens if the new version crashes immediately after rollout starts? How do you configure `maxUnavailable` and `maxSurge` for a critical service?

10. **Networking.** Compare Calico, Flannel, and Cilium. What CNI would you pick for this environment and why?

11. **Ingress.** How does traffic flow from an external client to a pod behind an ingress controller? What happens at each layer — DNS, load balancer, ingress, service, endpoint?

12. **Secrets and config.** How do you manage secrets in Kubernetes securely? Discuss the difference between Secrets, sealed-secrets, external secret operators, and Vault integration.

13. **Cluster upgrades.** How do you upgrade a Kubernetes cluster with minimal downtime? Cover control plane versus worker node ordering, and what can go wrong with CRDs and API deprecations.

14. **Observability.** What does your monitoring stack look like for Kubernetes? How do you alert on pod restarts, OOM kills, and node pressure?

15. **RBAC.** A developer needs to debug a pod in the staging namespace but must not touch production. How do you express that in RBAC?

## 3. Docker

16. **Image layers.** Explain how Docker image layers work. Why does `COPY` order matter in a Dockerfile, and how does it affect build cache and image size?

17. **Networking modes.** Compare bridge, host, and overlay networking. When would host mode be appropriate, and what are the security implications?

18. **Volumes.** A container writes data to a volume. The container is removed with `docker rm` but without `-v`. Where is the data, and how do you clean it up safely?

19. **Multi-stage builds.** Show me a Dockerfile for a Go or Node application that produces a minimal production image. Explain each stage's purpose.

20. **Resource limits.** How do you set CPU and memory limits for a container, and what happens when a container exceeds them? Distinguish between soft and hard limits.

21. **Registry.** How do you run a private container registry, mirror images for air-gapped or bandwidth-constrained environments, and scan images for vulnerabilities?

## 4. Linux and Dell Hardware

22. **Dell out-of-band management.** What tools do you use for remote management of Dell servers, and how do you update firmware (BIOS, iDRAC, NIC, RAID controller) across a fleet without physical access?

23. **RAID.** A Dell PERC controller reports a degraded virtual disk. Walk through diagnosis and rebuild. What monitoring do you put in place to catch this before it becomes a failure?

24. **Disk health.** How do you monitor SSD and HDD health proactively? Cover SMART attributes, wear levelling, and end-of-life planning.

25. **Linux troubleshooting.** A Linux server is slow. Walk through your systematic approach: load average, CPU, memory, disk I/O, network. What tools do you reach for at each stage?

26. **Systemd.** A service fails to start after a reboot. How do you diagnose it? Explain unit files, dependencies, and `systemctl status` versus `journalctl`.

27. **Firewall.** Compare `iptables`, `nftables`, and `firewalld`. How would you lock down a Linux host that also runs Docker and Kubernetes?

28. **Time synchronisation.** Why does NTP matter on this infrastructure, and how do you ensure consistent time across Proxmox hosts, VMs, and containers?

## 5. Networking

29. **Subnetting.** You have three class C blocks: 203.0.113.0/24, 198.51.100.0/24, and 192.0.2.0/24. Design a subnet plan for: management, storage, VM traffic, container overlay, VoIP, and a DMZ. Show your calculations.

30. **VLAN design.** Map those subnets to VLANs on managed switches. How do you trunk VLANs between switches and to Proxmox hosts? What is 802.1Q tagging?

31. **Uplink router.** Traffic from your class C blocks exits through a single uplink router to your provider. How do you configure NAT versus public IPs for different services? How do you handle failover if the uplink drops?

32. **Asymmetric routing.** You notice some connections hang intermittently. How would you diagnose asymmetric routing across multiple subnets and the uplink?

33. **DNS.** How do you run internal DNS for this environment? Cover split-horizon DNS, forwarders, and zone transfers between Proxmox hosts or VMs.

34. **DHCP.** Where does DHCP live — the uplink router, a Linux host, or something else? How do you hand out static reservations for servers and VoIP phones?

35. **Monitoring.** What network monitoring do you deploy? Cover bandwidth utilisation, latency, packet loss, and device availability. Name specific tools.

36. **Switch management.** How do you manage a fleet of managed switches — configuration backups, firmware updates, and detecting a rogue or misconfigured switch?

## 6. VoIP

37. **QoS.** Voice traffic is sensitive to jitter and loss. How do you prioritise VoIP across your LAN and WAN? Cover DSCP markings, queueing strategies, and where you'd apply policies.

38. **SIP trunking.** Explain how a SIP trunk connects to your provider. What ports and protocols are involved, and how do you secure them?

39. **Jitter buffer.** What is a jitter buffer, where does it live, and what are the trade-offs of sizing it too small or too large?

40. **Call quality troubleshooting.** Users report choppy audio on internal calls between offices. Walk through your diagnostic path from the phone handset to the SIP server to the network path.

41. **Registration storms.** What happens if the SIP registrar or proxy goes down, and how do you design for resilience?

42. **Security.** How do you prevent toll fraud and SIP scanning on an internet-facing VoIP system?

## 7. Operational and Behavioural

43. **Incident response.** It's 2am. The entire network is down — no internet, no VoIP, VMs unreachable. You're the only one on call. What's your first action?

44. **Documentation.** How do you keep network diagrams, IP allocations, and runbooks current when the team is small?

45. **Change management.** How do you introduce a change to production networking without causing an outage? Cover testing, rollback plans, and communication.

46. **Learning.** You've never administered VoIP before. How would you get up to speed in your first month?

47. **Priorities.** You're asked to do three things: patch all servers, migrate a VM, and fix a reported network issue affecting one user. How do you sequence them?

---

## Scoring Rubric

For each question, rate 1 to 5:

- **5 — Expert.** Correct, complete, anticipates follow-up problems, cites real tooling and trade-offs.
- **4 — Strong.** Correct and practical with minor gaps.
- **3 — Adequate.** Understands the concept but misses operational detail or edge cases.
- **2 — Weak.** Partial or confused understanding; would need close supervision.
- **1 — No knowledge.** Cannot attempt or gives incorrect fundamentals.

**Passing guidance:** A candidate moving from software development into network administration should average 3 or above across sections 1 to 4 (core infrastructure they already touch), and 2.5 or above across sections 5 and 6 (new territory), with no score of 1 in any critical area (Proxmox clustering, Kubernetes scheduling, subnetting, VoIP QoS).

**Red flags:** Cannot explain what happens to VMs on node death; treats Kubernetes as just Docker; cannot subnet a class C; has never heard of DSCP or jitter buffers; no out-of-band management experience.

---

*Prepared for internal evaluation. Adapt questions to the candidate's known background and the specific hardware and software versions in use.*