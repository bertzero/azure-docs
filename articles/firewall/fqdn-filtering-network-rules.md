---
title: Azure Firewall FQDN filtering in network rules
description: How to use Azure Firewall FQDN filtering in network rules
services: firewall
author: vhorne
ms.service: firewall
ms.topic: article
ms.date: 06/30/2020
ms.author: victorh
---

# FQDN filtering in network rules

A fully qualified domain name (FQDN) represents a domain name of a host. A domain name is associated with a single or multiple IP addresses. You can allow or block FQDNs and FQDN tags in application rules. Using custom DNS and DNS proxy settings, you can also use FQDN filtering in network rules.

## How it works

Azure Firewall translates the FQDN to an IP address(es) using its DNS settings and does rule processing based on Azure DNS or a custom DNS configuration.

To use FQDNs in network rules, you should enable DNS proxy. If you don't enable DNS proxy, secure rule processing is at risk. When it is enabled, DNS traffic is directed to Azure Firewall, where you can configure your custom DNS server. Then the firewall and clients use the same configured DNS server. If DNS proxy is not enabled, there is no guarantee that DNS traffic goes straight to the firewall for DNS client resolution. As a result, Azure Firewall may produce a different response because the client and firewall may use different servers for name resolution. FQDN filtering in network rules may be faulty or inconsistent if the client and firewall receive different DNS responses.

You can choose to override this requirement by acknowledging the risk before selecting **Save** in the rule collection.

## Next steps

[Azure Firewall DNS settings](dns-settings.md)
