---
layout: post
title:  Mobile Security Testing Guide (MSTG)
description: MSTG-NETWORK
date:   2023-08-26 15:01:35 +0700
image:  '/images/20.jpg'
tags:   [Penetration Tester, Red Team, Cheatsheet ]
---


# Table of Contents - MSTG Network Communication

- [MSTG-NETWORK-1: Data is encrypted on the network using TLS. The secure channel is used consistently throughout the app.](#mstg-network-1-data-is-encrypted-on-the-network-using-tls-the-secure-channel-is-used-consistently-throughout-the-app)
- [MSTG-NETWORK-2: The TLS settings are in line with current best practices, or as close as possible if the mobile operating system does not support the recommended standards.](#mstg-network-2-the-tls-settings-are-in-line-with-current-best-practices-or-as-close-as-possible-if-the-mobile-operating-system-does-not-support-the-recommended-standards)
- [MSTG-NETWORK-3: The app verifies the X.509 certificate of the remote endpoint when the secure channel is established. Only certificates signed by a trusted CA are accepted.](#mstg-network-3-the-app-verifies-the-x509-certificate-of-the-remote-endpoint-when-the-secure-channel-is-established-only-certificates-signed-by-a-trusted-ca-are-accepted)
- [MSTG-NETWORK-4: The app either uses its own certificate store, or pins the endpoint certificate or public key, and subsequently does not establish connections with endpoints that offer a different certificate or key, even if signed by a trusted CA.](#mstg-network-4-the-app-either-uses-its-own-certificate-store-or-pins-the-endpoint-certificate-or-public-key-and-subsequently-does-not-establish-connections-with-endpoints-that-offer-a-different-certificate-or-key-even-if-signed-by-a-trusted-ca)
- [MSTG-NETWORK-5: The app doesn't rely on a single insecure communication channel (email or SMS) for critical operations, such as enrollments and account recovery.](#mstg-network-5-the-app-doesnt-rely-on-a-single-insecure-communication-channel-email-or-sms-for-critical-operations-such-as-enrollments-and-account-recovery)
- [MSTG-NETWORK-6: The app only depends on up-to-date connectivity and security libraries.](#mstg-network-6-the-app-only-depends-on-up-to-date-connectivity-and-security-libraries)

## MSTG-NETWORK-1: Data is encrypted on the network using TLS. The secure channel is used consistently throughout the app. <a id="mstg-network-1-data-is-encrypted-on-the-network-using-tls-the-secure-channel-is-used-consistently-throughout-the-app"></a>

## MSTG-NETWORK-2: The TLS settings are in line with current best practices, or as close as possible if the mobile operating system does not support the recommended standards. <a id="mstg-network-2-the-tls-settings-are-in-line-with-current-best-practices-or-as-close-as-possible-if-the-mobile-operating-system-does-not-support-the-recommended-standards"></a>

## MSTG-NETWORK-3: The app verifies the X.509 certificate of the remote endpoint when the secure channel is established. Only certificates signed by a trusted CA are accepted. <a id="mstg-network-3-the-app-verifies-the-x509-certificate-of-the-remote-endpoint-when-the-secure-channel-is-established-only-certificates-signed-by-a-trusted-ca-are-accepted"></a>

## MSTG-NETWORK-4: The app either uses its own certificate store, or pins the endpoint certificate or public key, and subsequently does not establish connections with endpoints that offer a different certificate or key, even if signed by a trusted CA. <a id="mstg-network-4-the-app-either-uses-its-own-certificate-store-or-pins-the-endpoint-certificate-or-public-key-and-subsequently-does-not-establish-connections-with-endpoints-that-offer-a-different-certificate-or-key-even-if-signed-by-a-trusted-ca"></a>

## MSTG-NETWORK-5: The app doesn't rely on a single insecure communication channel (email or SMS) for critical operations, such as enrollments and account recovery. <a id="mstg-network-5-the-app-doesnt-rely-on-a-single-insecure-communication-channel-email-or-sms-for-critical-operations-such-as-enrollments-and-account-recovery"></a>

## MSTG-NETWORK-6: The app only depends on up-to-date connectivity and security libraries. <a id="mstg-network-6-the-app-only-depends-on-up-to-date-connectivity-and-security-libraries"></a>
