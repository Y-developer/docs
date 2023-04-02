# Docker Network

- [Docker Network](#docker-network)
  - [දැනට docker host එකේ පවතින network මොනවාදැයි බැලීමට](#දැනට-docker-host-එකේ-පවතින-network-මොනවාදැයි-බැලීමට)
  - [Network එකක විස්තර වැඩිදුරටත් බලාගැනීමට](#network-එකක-විස්තර-වැඩිදුරටත්-බලාගැනීමට)
  - [Network එකක් සෑදීම](#network-එකක්-සෑදීම)
  - [Network එකක් delete කිරීමට](#network-එකක්-delete-කිරීමට)
  - [භාවිතයක් නොමැති Network සියල්ල ඉවත් කිරීමට](#භාවිතයක්-නොමැති-network-සියල්ල-ඉවත්-කිරීමට)


## දැනට docker host එකේ පවතින network මොනවාදැයි බැලීමට
```bash
docker network ls
```
සාමාන්‍යයෙන docker host එක network 3ක් පවතී.
| NETWORK ID | NAME | DRIVER | SCOPE | විස්තරය |
|-|-|-|-|-|
| c507abe14a75 | bridge | bridge | local | පරිගණයේ සිට කෙලින්ම access කල හැක |
| a892ed8baedd | host | host | local | පරිගණයේ සිට access කිරීමට port publish කල යුතුය |
| 173fd36cdf87 | none | null | local | කිසිම ආකාරයකින් network එකකට සම්බන්ධ නොවේ. |

![Untitled-1](https://user-images.githubusercontent.com/117719820/229348893-20ef9da6-91b7-4cdd-ba69-e32f63a4ea4d.jpg)

## Network එකක විස්තර වැඩිදුරටත් බලාගැනීමට

```bash
docker network inspect <network_id>
```

## Network එකක් සෑදීම

```bash
docker network create --driver <bridge|host|null> --subnet <sub_net> <network_name>
```
මෙහිදී පහත options ලබා දීමේ හැකියාව ඇත.
|Name, shorthand|Description|
|-|-|
| --attachable | Enable manual container attachment |
| --aux-address | Auxiliary IPv4 or IPv6 addresses used by Network driver |
| --config-from | The network from which to copy the configuration |
| --config-only | Create a configuration only network |
| --driver , -d | Driver to manage the Network (`bridge`|`host`|`null` default value = `bridge`)  |
| --gateway | IPv4 or IPv6 Gateway for the master subnet |
| --ingress | Create swarm routing-mesh network |
| --internal | Restrict external access to the network |
| --ip-range | Allocate container ip from a sub-range |
| --ipam-driver | IP Address Management Driver |
| --ipam-opt | Set IPAM driver specific options |
| --ipv6 | Enable IPv6 networking |
| --label | Set metadata on a network |
| --opt , -o | Set driver specific options |
| --scope | Control the network’s scope |
| --subnet | Subnet in CIDR format that represents a network segment |

## Container එකක් run කි

## Network එකක් delete කිරීමට

```bash
docker network rm <network_id>
```

## භාවිතයක් නොමැති Network සියල්ල ඉවත් කිරීමට

```bash
docker network prune
```

