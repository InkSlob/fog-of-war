# What does secops want from a system?

Depends on the threat models & architecture!

Baseline assumptions for this note:
 - Internet connected system
 - No ‘end user computing’ -> this changes the threat model tremendously
 - Some regulatory oversight to require more than hopes and dreams


## Secops Objectives
1. Baseline
	1. Software (versions, sources, etc.)
	2. Systems / hosts inventory
	3. configurations
	4. Ports, protocols, services, etc.
	5. Network flows (src/dst, size, time of day)
The baseline is used for many purposes, including anomaly detection, incident response, backup/restore, etc.  If you don’t know ‘normal’, finding abnormal is much harder.
**Baselining is a key win for cloud -> its always available, always accurate, and can be monitored for changes automatically** 

2. Monitor / Observer
	1. Network -> rely on this only when other options unavailable
	2. User traffic
	3. System to system traffic
	4. Event sequences / traces
	5. Configuration drift
  Using the baseline as a guide, what is going on in an app or environment?  This is the most heavily funded and ‘attention’ focused area (lots of SIEM/SOAR tooling).

3. “DFIR” / Respond to events and incidents
	1. Breach (active adversaries)
	2. Malware (automated threats)
	3. Loss of systems/data
	4. LEO (warrant / NSL type stuff)
	5. Hunt (suspicious activity)  
  
  Response activities are playbook based in the best orgs.  In most orgs it’s seat of pants only.  
  Response in cloud environment is hindered by primarily a lack of expertise, but also a lack of tooling.  Cloud and SDN overlays dont fit the model of incident response based on physical network taps, disk images, etc.  
  This feels like an area to attack from an intellectual property perspective -> TTPS that can intelligently leverage cloud APIs can be standardized for whole environments the way single system processes and playbooks are today.  
  Automate and scale out:
	  e.g. take a disk snapshot of all VMs and copy to forensic environment, then run automated analysis across all snapshots at once.

4. Restore
  Who’s job is it to restore service after an incident?  How is this done?

5. Report
  Everybody has to report on things.  This is valuable, even if ‘boring’.
