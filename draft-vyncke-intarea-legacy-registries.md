---
title: "Managing the Legacy IPv4-related IANA Registries"
abbrev: "Legacy IANA IPv4 Registries"
docname: draft-vyncke-intarea-legacy-registries-latest
category: std
updates: 791, 952, 1091, 2242

ipr: trust200902
area: General
workgroup: int-area
keyword: Internet-Draft

stand_alone: yes
smart_quotes: no
pi: [toc, sortrefs, symrefs]

author:
 -
    ins: É. Vyncke
    name: Éric Vyncke
    organization: Cisco
    street: De Kleetlaan, 6A
    city: Diegem
    country: Belgium
    email: evyncke@cisco.com

normative:

informative:
  IAB_IPV4:
    target: https://datatracker.ietf.org/doc/statement-iab-statement-on-ipv6/
    title: IAB Statement on IPv6
  DHC_NETWARE:
    target: https://www.iana.org/assignments/bootp-dhcp-parameters/bootp-dhcp-parameters.xhtml#type-63-sub-options
    title: NetWare/IP Option Type 63 Sub-Option Codes
  IP_OPTIONS:
    target: https://www.iana.org/assignments/ip-parameters/ip-parameters.xhtml#ip-parameters-1
    title: IP Option Numbers
  IP_TTL:
    target: https://www.iana.org/assignments/ip-parameters/ip-parameters.xhtml#ip-parameters-2
    title: IP Option Numbers
  MACHINE_NAMES:
    target: https://www.iana.org/assignments/machine-names/machine-names.xhtml#machine-names-1
    title: Machine Names
  TERMINAL_TYPES:
    target: https://www.iana.org/assignments/terminal-type-names/terminal-type-names.xhtml#terminal-type-names-1
    title: Terminal Type Names


--- abstract

Before 2000, several IANA registries were created for IPv4. As IPv4 is no more extended,
the registration of new entries in associated registries need to be closed or updated.
This document updates RFC 791, RFC 952, RFC 1091, and RFC 2242 as it updates the related IANA registries.


--- middle

# Introduction

Before 2000, several IANA registries were created for IPv4-related protocol elements ({{?RFC791}}). As
the IETF does not plan to extend IPv4 (see also [IAB_IPV4] for the focus on IPv6), this document closes
some registries and changes the registration procedures of others.

## Justification

This section contains the justifications for the changes in IANA registries ({{iana-considerations}}):

* {{DHC_NETWARE}}: registration is to be closed as Netware is not extended anymore.
* {{IP_OPTIONS}}: as IPv4 will not be extended, the registration for new IPv4 options is to be closed.
* {{IP_TTL}}: this registry should not have been created as the IPv4 time-to-live (TTL) header field can be freely selected by the source node.
* {{MACHINE_NAMES}} and {{TERMINAL_TYPES}}: there are no registration procedures for these registries and, while probably new registrations will be rare, this document specifies the registration procedure as "First Come, First Served" ({{!RFC8126, Section 4.4}}).

# Operational Considerations

As the some registries are closing, they cannot be extended but the existing values are still
valid, i.e., they are not deprecated and can still be used.

# Security Considerations

There is no specific security considerations for this document except for the registries whose registration
procedures is now {{!RFC8126}} First Come First Served, the registration is still possible
with the risk of having unusable non-sensible data in it, but the IANA policy is to apply common sense
filtering on the content and amount of registrations.

# IANA Considerations

The IANA is requested to set the registration procedure to "Registration no longer accepted" with a reference to this document:
* {{DHC_NETWARE}}
* {{IP_OPTIONS}}

The IANA is requested to set the registration procedure to "First Come First Served" ({{!RFC8126, Section 4.4}}) with a reference to this document:
* {{MACHINE_NAMES}}
* {{TERMINAL_TYPES}}

The IANA is requested to completely remove the {{IP_TTL}} registry. If not possible, then the IANA is requested to
replace the existing note by
"There is no registry for the IPv4 time-to-live (TTL) as it is set by the node operating system or the node application.
The past and current recommended default time to live (TTL) for the IPv4 is 64 [RFC791][RFC1122]."

--- back

# Acknowledgments
{:numbered="false"}

Thanks to Mohamed Boucadair for the initial idea and to Amanda Baber for the initial list of legacy registries.
