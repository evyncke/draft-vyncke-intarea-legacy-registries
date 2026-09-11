---
title: "Updates to Legacy IANA Registries"
abbrev: "Legacy IANA Registries"
docname: draft-ietf-intarea-legacy-registries-latest
category: std

ipr: trust200902
area: Internet
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
  DHC_NETWARE:
    author:
      -
        organization: "IANA"
    target: https://www.iana.org/assignments/bootp-dhcp-parameters/bootp-dhcp-parameters.xhtml#type-63-sub-options
    title: NetWare/IP Option Type 63 Sub-Option Codes
    date: false
  IAB_IPV4:
    target: https://datatracker.ietf.org/doc/statement-iab-statement-on-ipv6/
    title: IAB Statement on IPv6
    date: 2016-11-07
  IP_OPTIONS:
    author:
      -
       organization: "IANA"
    target: https://www.iana.org/assignments/ip-parameters/ip-parameters.xhtml#ip-parameters-1
    title: IP Option Numbers
    date: false
  IP_TTL:
    author:
      -
       organization: "IANA"
    target: https://www.iana.org/assignments/ip-parameters/ip-parameters.xhtml#ip-parameters-2
    title: IP Time to Live Parameter
    date: false
  MACHINE_NAMES:
    author:
      -
       organization: "IANA"
    target: https://www.iana.org/assignments/machine-names/machine-names.xhtml
    title: Machine Names
    date: false
  NOT_AN_OPTION:
    author:
      -
       name: Rodrigo Fonseca
      -
       name: George Manning Porter
      -
       name: Randy H. Katz
      -
       name: Scott Shenker
      -
       name: Ion Stoica
    target: https://www2.eecs.berkeley.edu/Pubs/TechRpts/2005/EECS-2005-24.pdf
    title: IP Options are not an option
    date: December 9, 2005
  TERMINAL_TYPES:
    author:
      -
       organization: "IANA"
    target: https://www.iana.org/assignments/terminal-type-names/terminal-type-names.xhtml
    title: Terminal Type Names
    date: false



--- abstract

IANA maintains several registries that were created for IPv4. As the IPv4 core specification
is no longer being extended and as some other registries do not have a defined IANA registration procedure,
these registries need to be updated to indicate a registration procedure or
to reflect the current practice that defining such extensions is not recommended.


--- middle

# Introduction

Several registries were created for IPv4-related protocol elements {{!RFC791}}.
These registries were created by {{?RFC1700}}, which in turn was obsoleted by {{?RFC3232}} which handed
these registries to IANA.

The IPv4 core specification {{!RFC791}} is no longer being extended (see also {{IAB_IPV4}}) and more
modern mechanisms are defined to manage names. Also, some IANA registries do not have a defined registration policy ({{Section 4 of !RFC8126}}).
Therefore, this document closes
some relevant IANA registries and changes the registration procedure for others. See more in {{sec-justification}}.

The information in the closed registries is still valid and registrations already in these registries can still be updated
per the guidance in {{Section 9.6 of !RFC8126}}.

## Justification {#sec-justification}

The justifications for the changes to IANA registries listed in {{iana-considerations}} are as follows:

{{DHC_NETWARE}}:
: Registrations are to be closed as Netware is not extended anymore.

{{IP_OPTIONS}}:
: while it is commonly understood that the use of IPv4 options is broken {{NOT_AN_OPTION}}, the registry is not to be closed but the registration procedure is set to
"IESG approval" ({{!RFC8126, Section 4.10}}).

{{IP_TTL}}:
: This registry should not have been created as the IPv4 Time to Live (TTL) ({{Section 3.1 of !RFC791}}) header field can be freely selected by source nodes.

{{MACHINE_NAMES}} and {{TERMINAL_TYPES}}:
: There are no defined registration procedures for these two registries. Moreover, there were no registrations made to these registries in the last two decades. This document specifies the registration procedure as "First Come First Served" ({{!RFC8126, Section 4.4}}).

# Operational Considerations

As one registry is closed, it cannot be extended but the existing values are still
valid (i.e., unless they are deprecated by a future document, they can still be used). These changes do not impact existing
operations that use already registered values.

The use of IPv4 options on the public Internet is broken. Solutions that rely on defining such options will probably not
be reliable. More
robust alternative means should be explored.

# Security Considerations

There are no new security considerations introduced by this document except for the registries whose registration
policies are changed to "First Come First Served". Concretely, registrations are still possible to such registries
with the risk of having unusable non-sensible data added to it, but the IANA policy is to apply common sense
filtering on the content and amount of registrations.

# IANA Considerations

This document requests IANA to close the following registry per {{Section 9.6 of RFC8126}} and add a reference to this document:

* The "NetWare/IP Option Type 63 Sub-Option Codes" registry under the "Dynamic Host Configuration Protocol (DHCP) and Bootstrap Protocol (BOOTP) Parameters" registry group {{DHC_NETWARE}}.

This document requests IANA to set the registration procedure to "IESG approval" ({{!RFC8126, Section 4.10}}) with a reference to this document for the following registry:

* The "IP Option Numbers" registry under the "Internet Protocol Version 4 (IPv4) Parameters" registry group {{IP_OPTIONS}}.

This document requests IANA to set the registration procedure to "First Come First Served" ({{!RFC8126, Section 4.4}}) with a reference to this document for the following registries:

* The "Machine Names" registry group {{MACHINE_NAMES}}.
* The "Terminal Type Names" registry group {{TERMINAL_TYPES}}.

This document also requests IANA to completely remove the "IP Time to Live Parameter" registry under the "Internet Protocol Version 4 (IPv4) Parameters" registry group  {{IP_TTL}}. If not possible, then IANA is requested to replace the existing note with the following note:

> There is no registry for the IPv4 Time To Live (TTL) as it is set by the node operating system or the node application.
> Recommended default TTL value for IPv4 is 64 {{!RFC791}}{{!RFC1122}}.

--- back

# Acknowledgments
{:numbered="false"}

Thanks to Mohamed Boucadair for the initial idea and deep review. Thanks also to Amanda Baber for the initial list of legacy registries or registries without
any specified registration procedures. Other thanks for reviewers: Brian Carpenter, Tommy Jensen, Tjeerd Pinkert, Dave Thaler.
