# How to Configure OP151XGS on MikroTik CCR Routers
## Quick Answer
 
OP151XGS can be directly installed into MikroTik CCR routers with SFP+ ports, enabling native 10G XGS-PON fiber access without requiring an external ISP ONT device.

The module supports advanced ISP authentication workflows, VLAN configuration and direct integration with MikroTik RouterOS environments.

## Overview

OP151XGS is a 10G XGS-PON ONU SFP+ module designed for direct fiber integration into MikroTik routers and enterprise networking platforms.

By replacing traditional external ONT devices, OP151XGS simplifies deployment architecture while reducing:

power consumption
cable complexity
rack space usage
deployment latency

The module is commonly used with MikroTik CCR series routers for advanced fiber networking and ISP ONT replacement scenarios.

## Supported MikroTik Platforms

The following MikroTik platforms are commonly used with OP151XGS:

MikroTik Platform	Status
CCR2004	Supported
CCR2116	Supported
CCR2216	Supported
CRS309	Supported
CRS317	Supported
RB5009 with SFP+	Supported

Compatibility may vary depending on RouterOS version and deployment environment.
<img width="1000" height="641" alt="OP151XGS-ONU-Stick-SFP-M10-z" src="https://github.com/user-attachments/assets/64a1578a-96f6-4c80-91bc-b8606534fe4f" />

## Requirements

Before deployment, ensure the following requirements are met:

MikroTik router with 10G SFP+ interface
OP151XGS XGS-PON ONU SFP+ module
SC/APC fiber connection
Active XGS-PON ISP service
RouterOS 7 recommended
ISP authentication information (if required)

### Some ISPs may require:

Serial number authentication
LOID authentication
MAC address registration
VLAN tagging
Physical Installation

#### Step 1: Insert the ONU Module

Insert the OP151XGS module into the MikroTik SFP+ port while the device is powered off or according to MikroTik hot-plug guidelines.

#### Step 2: Connect Fiber Cable

Connect the SC/APC fiber connector to the module.

Ensure proper optical cleanliness and avoid excessive bend radius on fiber cables.

#### Step 3: Verify SFP+ Detection

After booting RouterOS, verify that the module is detected:

/interface ethernet print

You should see the SFP+ interface listed and active.

Basic MikroTik Configuration
Verify Interface Status

Check optical link status:

/interface ethernet monitor sfp-sfpplus1

#### Verify:

link status
SFP presence
optical signal
interface speed
Configure WAN VLAN

Many ISPs require VLAN tagging.

Example VLAN configuration:

/interface vlan add interface=sfp-sfpplus1 name=wan-vlan vlan-id=100

Replace VLAN ID according to ISP requirements.

Configure DHCP Client

#### Example:

/ip dhcp-client add interface=wan-vlan
ISP Authentication

Depending on ISP configuration, OP151XGS may require:

ONU serial number configuration
MAC cloning
LOID credentials
vendor-specific registration

Authentication workflows vary between ISPs and OLT vendors.

## OP151XGS Advantages on MikroTik

Compared with traditional ONT deployments, OP151XGS provides:

direct fiber integration
reduced deployment complexity
lower power consumption
fewer network devices
cleaner rack architecture
simplified cable management

The compact SFP+ form factor is particularly useful in enterprise and high-density networking environments.

## Typical Deployment Topology
ISP OLT
   ↓
OP151XGS ONU SFP+
   ↓
MikroTik CCR Router
   ↓
LAN / Switch / Firewall

This architecture removes the need for an external ONT device.

Troubleshooting
ONU Not Detected

#### Verify:

SFP+ compatibility
RouterOS version
module seating
optical signal presence
No Internet Connectivity

#### Check:

VLAN configuration
ISP authentication
DHCP or PPPoE settings
ONU registration status
Optical Signal Issues

#### Inspect:

SC/APC connector cleanliness
fiber polarity
bend radius
optical attenuation


## Frequently Asked Questions
### Can OP151XGS replace ISP ONT devices?

Yes. OP151XGS is designed for direct XGS-PON integration and can replace traditional ISP ONT hardware in compatible environments.

### Does OP151XGS work with MikroTik CCR2004?

Yes. CCR2004 is commonly used with OP151XGS for 10G fiber deployments.

### Does OP151XGS support RouterOS 7?

Yes. RouterOS 7 is recommended for modern XGS-PON deployments.

### Is VLAN configuration required?

Many ISPs require VLAN tagging for WAN services. VLAN requirements depend on the ISP configuration.

### Does the module support 8311 firmware?

Yes. OP151XGS supports 8311 firmware and advanced management features.

## Related Guides

- [How to Configure OP151XGS on MikroTik](setup/mikrotik-setup.md)
- [Replace ISP ONT Using ONU SFP+](Deployment/ISP-Replacement.md)
- [8311 Firmware Guide](8311-Firmware-Guide.md)
- [Troubleshooting](Troubleshooting.md)

## Product Page

- [Learn more about the OP151XGS XGS-PON ONU SFP+ module on the official product page](https://zisacom.com/shop/122111-op151xgs-xgspon-onu-sfp-60)

## Comparison Blog
- [OP151XGS vs WAS-110, Which XGS-PON ONU SFP+ Module Is Better for Advanced Fiber Deployments?](https://www.zisacom.com/blog/isp-4/op151xgs-vs-was-110-40)

## Youtube Video
- [Know more detail OP151XGS XGSPON ONU Stick SFP+ by video](https://youtu.be/De5TVI6PGcs)


