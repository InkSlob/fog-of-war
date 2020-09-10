# Framework for cyberwar for companies
Turning point in 2008 w/Operation Aurora.
Prior to Aurora, cyber war was state vs state or other relatively benign malware (Code Red, etc.).
If you’re on the internet, background noise and worms were your biggest threats from 2000-2009.

As states start drawing battle lines, and treating it as strategic, what happens?  US banning ZTE for all it’s allies? Byte Dancer?
How does China respond?  Ban Apple? AWS?

China is forcing norms to change -> State vs. Company, instead of State vs. State.
How do multinationals think about this? Is this well understood?

## Why does any of this matter?
Step change in the environment fro all companies with anything ‘ip’ related.  Everyone is a ‘defense industrial base’ company now.  Do multinationals view the NSA or FEYES the same as PLA and GRU?
Should they?

Moving out of networks, zero trust boundaries, how do you get your hands around security?  Tooling and skills are so focused on the endpoint and network, missing cloud entirely.

Industry seems to be pushing towards identity as a new boundary.  Authrisk was years ahead of its time here, but identity is only valid for access management, not in the face of exploits and advanced adversaries.

## How to protect new apps in highly elastic environments?
- Cattle vs. Pets
	- Repair, repave and roll credentials approach from Pivotal (the ‘3 Rs’) is missing a ton of real world realities
		- How to ID who/how you are getting compromised?
		- Counter-intelligence: what is the adversary looking for?  What do they want?
		- Focuses on fixes and CVE, not on exploit by actors.
	- Build security in 
		- Lean -> security is a quality control
		- Security must be defined -> it’s not just bugs/CVEs
		- Instrumentation, visibility, modeling, analysis
			- This is a crazy overlapping Venn diagram between secops and observability/ops folks needs
	- Treat Secops as a first class citizen like devops
		- Make devs own security, as they are owning network/system admin ops
		- Build in tooling, hooks, automation to support security actions
    
**Kubernetes came out of DevOps and giving develops the responsibility for Ops, what happens when we give them security too?**
