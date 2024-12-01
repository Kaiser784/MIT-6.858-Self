#systemsec #mitocw 

Discussion based on [Google Cloud's paper](https://cloud.google.com/security/infrastructure/design)

Defend against a class of attacks.
Resilient against Unknown attacks.
Contain Damage

 **<u>Threats google look for</u>**
 
- bugs
- password theft
- insiders
- hardware
- network
- Physical attacks

#### Security starts from Isolation

- VM's - KVM in Linux
- Separate Physical servers
- You can box up JS codes


Even though they are isolated you need them to communicate/share in some sort of way.
This often called as Reference Monitor model or Guard model.

The Sandbox/VM will have a resource in it
- You get a request to use it
- A guard will either allow/reject the request based on the policy.
- Guard needs to find who made the request to properly execute the policy.
- The guard should be logging everything to an audit log in one of the isolation domains which is not the resource sandbox.

What the guard should be doing
- [[#Authentication]]
- [[#Authorization]]
- Audit

### Authentication

##### For an end-user
Having a Password, and the guard authenticates the principal based on it.
To make sure the User is the one logging in with the password use 2FA.
#### For a service
- IP authentication (a bit error prone)
- API key
### Authorization
 Have matrix kind of table with permissions specified.
 
 This is a bit wasteful.
 - They mostly store only rows of these tables.
 - Sometimes are stored according to columns too which are called capabilities. 
### Granularity
What should be a box with the guard?
- Data Center? 
	- If you guard something big as DC then there no more guards after the first guard bcoz its a trusted inside.
	- Firewalls, IDS, Perimeter Defense are an example
- Each Service?
	- What google does with their stuff
	- Principle of Least Privilege
- Each User?
	- They don't implement coz but  performance is compromised a lot even though it maybe more secure.
### Where is the Security affecting the Performance
- Talking to RPC's (Remote Procedure Calls)
- Encryption
	- For RPC's
	- Data on disk

