---
layout: post
title:  Mobile Security Testing Guide (MSTG)
description: MSTG-PLATFORM
date:   2023-08-26 15:01:35 +0700
image:  '/images/20.jpg'
tags:   [Penetration Tester, Red Team, Cheatsheet ]
---

# Table of Contents - MSTG Platform Interaction

- [MSTG-PLATFORM-1: The app only requests the minimum set of permissions necessary.](#mstg-platform-1-the-app-only-requests-the-minimum-set-of-permissions-necessary)
- [MSTG-PLATFORM-2: All inputs from external sources and the user are validated and if necessary sanitized. This includes data received via the UI, IPC mechanisms such as intents, custom URLs, and network sources.](#mstg-platform-2-all-inputs-from-external-sources-and-the-user-are-validated-and-if-necessary-sanitized-this-includes-data-received-via-the-ui-ipc-mechanisms-such-as-intents-custom-urls-and-network-sources)
- [MSTG-PLATFORM-3: The app does not export sensitive functionality via custom URL schemes, unless these mechanisms are properly protected.](#mstg-platform-3-the-app-does-not-export-sensitive-functionality-via-custom-url-schemes-unless-these-mechanisms-are-properly-protected)
- [MSTG-PLATFORM-4: The app does not export sensitive functionality through IPC facilities, unless these mechanisms are properly protected.](#mstg-platform-4-the-app-does-not-export-sensitive-functionality-through-ipc-facilities-unless-these-mechanisms-are-properly-protected)
- [MSTG-PLATFORM-5: JavaScript is disabled in WebViews unless explicitly required.](#mstg-platform-5-javascript-is-disabled-in-webviews-unless-explicitly-required)
- [MSTG-PLATFORM-6: WebViews are configured to allow only the minimum set of protocol handlers required (ideally, only https is supported). Potentially dangerous handlers, such as file, tel and app-id, are disabled.](#mstg-platform-6-webviews-are-configured-to-allow-only-the-minimum-set-of-protocol-handlers-required-ideally-only-https-is-supported-potentially-dangerous-handlers-such-as-file-tel-and-app-id-are-disabled)
- [MSTG-PLATFORM-7: If native methods of the app are exposed to a WebView, verify that the WebView only renders JavaScript contained within the app package.](#mstg-platform-7-if-native-methods-of-the-app-are-exposed-to-a-webview-verify-that-the-webview-only-renders-javascript-contained-within-the-app-package)
- [MSTG-PLATFORM-8: Object deserialization, if any, is implemented using safe serialization APIs.](#mstg-platform-8-object-deserialization-if-any-is-implemented-using-safe-serialization-apis)
- [MSTG-PLATFORM-9: The app protects itself against screen overlay attacks. (Android only)](#mstg-platform-9-the-app-protects-itself-against-screen-overlay-attacks-android-only)
- [MSTG-PLATFORM-10: A WebView's cache, storage, and loaded resources (JavaScript, etc.) should be cleared before the WebView is destroyed.](#mstg-platform-10-a-webviews-cache-storage-and-loaded-resources-javascript-etc-should-be-cleared-before-the-webview-is-destroyed)
- [MSTG-PLATFORM-11: Verify that the app prevents usage of custom third-party keyboards whenever sensitive data is entered.](#mstg-platform-11-verify-that-the-app-prevents-usage-of-custom-third-party-keyboards-whenever-sensitive-data-is-entered)

## MSTG-PLATFORM-1: The app only requests the minimum set of permissions necessary. <a id="mstg-platform-1-the-app-only-requests-the-minimum-set-of-permissions-necessary"></a>

## MSTG-PLATFORM-2: All inputs from external sources and the user are validated and if necessary sanitized. This includes data received via the UI, IPC mechanisms such as intents, custom URLs, and network sources. <a id="mstg-platform-2-all-inputs-from-external-sources-and-the-user-are-validated-and-if-necessary-sanitized-this-includes-data-received-via-the-ui-ipc-mechanisms-such-as-intents-custom-urls-and-network-sources"></a>

## MSTG-PLATFORM-3: The app does not export sensitive functionality via custom URL schemes, unless these mechanisms are properly protected. <a id="mstg-platform-3-the-app-does-not-export-sensitive-functionality-via-custom-url-schemes-unless-these-mechanisms-are-properly-protected"></a>

## MSTG-PLATFORM-4: The app does not export sensitive functionality through IPC facilities, unless these mechanisms are properly protected. <a id="mstg-platform-4-the-app-does-not-export-sensitive-functionality-through-ipc-facilities-unless-these-mechanisms-are-properly-protected"></a>

## MSTG-PLATFORM-5: JavaScript is disabled in WebViews unless explicitly required. <a id="mstg-platform-5-javascript-is-disabled-in-webviews-unless-explicitly-required"></a>

## MSTG-PLATFORM-6: WebViews are configured to allow only the minimum set of protocol handlers required (ideally, only https is supported). Potentially dangerous handlers, such as file, tel and app-id, are disabled. <a id="mstg-platform-6-webviews-are-configured-to-allow-only-the-minimum-set-of-protocol-handlers-required-ideally-only-https-is-supported-potentially-dangerous-handlers-such-as-file-tel-and-app-id-are-disabled"></a>

## MSTG-PLATFORM-7: If native methods of the app are exposed to a WebView, verify that the WebView only renders JavaScript contained within the app package. <a id="mstg-platform-7-if-native-methods-of-the-app-are-exposed-to-a-webview-verify-that-the-webview-only-renders-javascript-contained-within-the-app-package"></a>

## MSTG-PLATFORM-8: Object deserialization, if any, is implemented using safe serialization APIs. <a id="mstg-platform-8-object-deserialization-if-any-is-implemented-using-safe-serialization-apis"></a>

## MSTG-PLATFORM-9: The app protects itself against screen overlay attacks. (Android only) <a id="mstg-platform-9-the-app-protects-itself-against-screen-overlay-attacks-android-only"></a>

## MSTG-PLATFORM-10: A WebView's cache, storage, and loaded resources (JavaScript, etc.) should be cleared before the WebView is destroyed. <a id="mstg-platform-10-a-webviews-cache-storage-and-loaded-resources-javascript-etc-should-be-cleared-before-the-webview-is-destroyed"></a>

## MSTG-PLATFORM-11: Verify that the app prevents usage of custom third-party keyboards whenever sensitive data is entered. <a id="mstg-platform-11-verify-that-the-app-prevents-usage-of-custom-third-party-keyboards-whenever-sensitive-data-is-entered"></a>
