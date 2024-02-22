---
layout: post
title:  Mobile Security Testing Guide (MSTG)
description: MSTG-RESILIENCE
date:   2023-08-28 15:01:35 +0700
image:  '/images/20.jpg'
tags:   [Penetration Tester, Red Team, Cheatsheet ]
---

# Table of Contents - MSTG Impede Dynamic Analysis and Tampering

- [MSTG-RESILIENCE-1: The app detects, and responds to, the presence of a rooted or jailbroken device either by alerting the user or terminating the app.](#mstg-resilience-1-the-app-detects-and-responds-to-the-presence-of-a-rooted-or-jailbroken-device-either-by-alerting-the-user-or-terminating-the-app)
- [MSTG-RESILIENCE-2: The app prevents debugging and/or detects, and responds to, a debugger being attached. All available debugging protocols must be covered.](#mstg-resilience-2-the-app-prevents-debugging-andor-detects-and-responds-to-a-debugger-being-attached-all-available-debugging-protocols-must-be-covered)
- [MSTG-RESILIENCE-3: The app detects, and responds to, tampering with executable files and critical data within its own sandbox.](#mstg-resilience-3-the-app-detects-and-responds-to-tampering-with-executable-files-and-critical-data-within-its-own-sandbox)
- [MSTG-RESILIENCE-4: The app detects, and responds to, the presence of widely used reverse engineering tools and frameworks on the device.](#mstg-resilience-4-the-app-detects-and-responds-to-the-presence-of-widely-used-reverse-engineering-tools-and-frameworks-on-the-device)
- [MSTG-RESILIENCE-5: The app detects, and responds to, being run in an emulator.](#mstg-resilience-5-the-app-detects-and-responds-to-being-run-in-an-emulator)
- [MSTG-RESILIENCE-6: The app detects, and responds to, tampering the code and data in its own memory space.](#mstg-resilience-6-the-app-detects-and-responds-to-tampering-the-code-and-data-in-its-own-memory-space)
- [MSTG-RESILIENCE-7: The app implements multiple mechanisms in each defense category (8.1 to 8.6). Note that resiliency scales with the amount, diversity of the originality of the mechanisms used.](#mstg-resilience-7-the-app-implements-multiple-mechanisms-in-each-defense-category-81-to-86-note-that-resiliency-scales-with-the-amount-diversity-of-the-originality-of-the-mechanisms-used)
- [MSTG-RESILIENCE-8: The detection mechanisms trigger responses of different types, including delayed and stealthy responses.](#mstg-resilience-8-the-detection-mechanisms-trigger-responses-of-different-types-including-delayed-and-stealthy-responses)
- [MSTG-RESILIENCE-9: Obfuscation is applied to programmatic defenses, which in turn impede de-obfuscation via dynamic analysis.](#mstg-resilience-9-obfuscation-is-applied-to-programmatic-defenses-which-in-turn-impede-de-obfuscation-via-dynamic-analysis)
- [MSTG-RESILIENCE-10: The app implements a 'device binding' functionality using a device fingerprint derived from multiple properties unique to the device.](#mstg-resilience-10-the-app-implements-a-device-binding-functionality-using-a-device-fingerprint-derived-from-multiple-properties-unique-to-the-device)
- [MSTG-RESILIENCE-11: All executable files and libraries belonging to the app are either encrypted on the file level and/or important code and data segments inside the executables are encrypted or packed. Trivial static analysis does not reveal important code or data.](#mstg-resilience-11-all-executable-files-and-libraries-belonging-to-the-app-are-either-encrypted-on-the-file-level-andor-important-code-and-data-segments-inside-the-executables-are-encrypted-or-packed-trivial-static-analysis-does-not-reveal-important-code-or-data)
- [MSTG-RESILIENCE-12: If the goal of obfuscation is to protect sensitive computations, an obfuscation scheme is used that is both appropriate for the particular task and robust against manual and automated de-obfuscation methods, considering currently published research. The effectiveness of the obfuscation scheme must be verified through manual testing. Note that hardware-based isolation features are preferred over obfuscation whenever possible.](#mstg-resilience-12-if-the-goal-of-obfuscation-is-to-protect-sensitive-computations-an-obfuscation-scheme-is-used-that-is-both-appropriate-for-the-particular-task-and-robust-against-manual-and-automated-de-obfuscation-methods-considering-currently-published-research-the-effectiveness-of-the-obfuscation-scheme-must-be-verified-through-manual-testing-note-that-hardware-based-isolation-features-are-preferred-over-obfuscation-whenever-possible)
- [MSTG-RESILIENCE-13: As a defense in depth, next to having solid hardening of the communicating parties, application level payload encryption can be applied to further impede eavesdropping.](#mstg-resilience-13-as-a-defense-in-depth-next-to-having-solid-hardening-of-the-communicating-parties-application-level-payload-encryption-can-be-applied-to-further-impede-eavesdropping)

## MSTG-RESILIENCE-1: The app detects, and responds to, the presence of a rooted or jailbroken device either by alerting the user or terminating the app. <a id="mstg-resilience-1-the-app-detects-and-responds-to-the-presence-of-a-rooted-or-jailbroken-device-either-by-alerting-the-user-or-terminating-the-app"></a>

## MSTG-RESILIENCE-2: The app prevents debugging and/or detects, and responds to, a debugger being attached. All available debugging protocols must be covered. <a id="mstg-resilience-2-the-app-prevents-debugging-andor-detects-and-responds-to-a-debugger-being-attached-all-available-debugging-protocols-must-be-covered"></a>

## MSTG-RESILIENCE-3: The app detects, and responds to, tampering with executable files and critical data within its own sandbox. <a id="mstg-resilience-3-the-app-detects-and-responds-to-tampering-with-executable-files-and-critical-data-within-its-own-sandbox"></a>

## MSTG-RESILIENCE-4: The app detects, and responds to, the presence of widely used reverse engineering tools and frameworks on the device. <a id="mstg-resilience-4-the-app-detects-and-responds-to-the-presence-of-widely-used-reverse-engineering-tools-and-frameworks-on-the-device"></a>

## MSTG-RESILIENCE-5: The app detects, and responds to, being run in an emulator. <a id="mstg-resilience-5-the-app-detects-and-responds-to-being-run-in-an-emulator"></a>

## MSTG-RESILIENCE-6: The app detects, and responds to, tampering the code and data in its own memory space. <a id="mstg-resilience-6-the-app-detects-and-responds-to-tampering-the-code-and-data-in-its-own-memory-space"></a>

## MSTG-RESILIENCE-7: The app implements multiple mechanisms in each defense category (8.1 to 8.6). Note that resiliency scales with the amount, diversity of the originality of the mechanisms used. <a id="mstg-resilience-7-the-app-implements-multiple-mechanisms-in-each-defense-category-81-to-86-note-that-resiliency-scales-with-the-amount-diversity-of-the-originality-of-the-mechanisms-used"></a>

## MSTG-RESILIENCE-8: The detection mechanisms trigger responses of different types, including delayed and stealthy responses. <a id="mstg-resilience-8-the-detection-mechanisms-trigger-responses-of-different-types-including-delayed-and-stealthy-responses"></a>

## MSTG-RESILIENCE-9: Obfuscation is applied to programmatic defenses, which in turn impede de-obfuscation via dynamic analysis. <a id="mstg-resilience-9-obfuscation-is-applied-to-programmatic-defenses-which-in-turn-impede-de-obfuscation-via-dynamic-analysis"></a>

## MSTG-RESILIENCE-10: The app implements a 'device binding' functionality using a device fingerprint derived from multiple properties unique to the device. <a id="mstg-resilience-10-the-app-implements-a-device-binding-functionality-using-a-device-fingerprint-derived-from-multiple-properties-unique-to-the-device"></a>

## MSTG-RESILIENCE-11: All executable files and libraries belonging to the app are either encrypted on the file level and/or important code and data segments inside the executables are encrypted or packed. Trivial static analysis does not reveal important code or data. <a id="mstg-resilience-11-all-executable-files-and-libraries-belonging-to-the-app-are-either-encrypted-on-the-file-level-andor-important-code-and-data-segments-inside-the-executables-are-encrypted-or-packed-trivial-static-analysis-does-not-reveal-important-code-or-data"></a>

## MSTG-RESILIENCE-12: If the goal of obfuscation is to protect sensitive computations, an obfuscation scheme is used that is both appropriate for the particular task and robust against manual and automated de-obfuscation methods, considering currently published research. The effectiveness of the obfuscation scheme must be verified through manual testing. Note that hardware-based isolation features are preferred over obfuscation whenever possible. <a id="mstg-resilience-12-if-the-goal-of-obfuscation-is-to-protect-sensitive-computations-an-obfuscation-scheme-is-used-that-is-both-appropriate-for-the-particular-task-and-robust-against-manual-and-automated-de-obfuscation-methods-considering-currently-published-research-the-effectiveness-of-the-obfuscation-scheme-must-be-verified-through-manual-testing-note-that-hardware-based-isolation
