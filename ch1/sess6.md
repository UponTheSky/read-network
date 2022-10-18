# Networks Under Attack
- today's most prevalent security-related problems?

## Malware
- deleting files, spyware for taking private information
- **botnet**
- self-replicating

## Attacking Server & Network Infrastructure
- **DoS(Denial of Service)** attacks: renders a network, host, or other piece of infrastructure unusable by legitimate users
  - web servers, email servers, DNS servers, and institutional networks

- typical DoS attacks
  - vulnerability attack: sending a few well-crafted messages to a vulnerable application or OS
  - bandwidth flooding: sending a deluge of packets so that the target's access link becomes clogged
  - connection flooding: establishing a large number of half-open or fully open TCP connections at the target host, which are bogus

- **DDoS(distributed DoS)**: the attacker controls multiple resources and has each source blast traffic at the target

## Sniffing Packets
- wireless transmitter: placing a passive receiver(**packet sniffer**) in vicinity would sniff a copy of every packet transmitted
- since "passive", difficult to be detected
- how to protect?: cryptography!

## Masquerading as Someone Trusted
- **IP spoofing**: the ability to inject packets into the Internet with a false source address
- needs: **end-point authentication** 
  - a mechanism to determine with certainty if a message originates from where we think it does