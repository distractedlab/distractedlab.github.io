# Privacy Policy · Mark & Ask

[简体中文](PRIVACY.zh-CN.md)

Mark & Ask (by DistractedLab) · Effective date: 2026-11-25

## Overview

This policy describes Mark & Ask 0.4.0. Mark & Ask is a local-first browser extension: it has no account system and no DistractedLab-run server. Your notes and settings stay in your browser. This page explains the exceptions, the data involved, and how to remove it.

## What the extension stores

The extension stores this data on your device to provide marking, page remarks, reading status, the Notes Library, and export:

- Page records: URL, canonical URL, domain, title, reading status, and created and updated times.
- Marks: selected text with its anchoring context and character positions, or an image address, description, and anchoring context. Marks also include their style, any annotation, and creation time. The last jointly observed reading order and observation time are kept locally and excluded from backups.
- Page remarks.
- Settings: interface language, mark visibility and theme, ordering and filtering, AI endpoint, model and context budget, chat roles, Markdown templates, and the Vault folder permission.

## Storage and local data

Where it is stored: IndexedDB holds page records, page remarks, and marks, plus a second local database for the AI endpoint, model, encrypted API key, and Vault folder handle; chrome.storage.local holds the settings listed above; chrome.storage.session holds only the current annotation focus, which is cleared when the browser closes.

The extension uses this data only to provide these features. There is no cloud sync, and the extension contains no analytics, advertising, or telemetry code.

Local records are not encrypted. Anyone who can access your browser profile or computer can read them. The API key is handled separately, as described below.

## What the extension reads

- When you open the side panel, it reads the current tab’s URL and title to match saved records. It does not read your browsing history or other tabs.
- To show saved marks, it reads the text and structure of the page you are viewing. This happens locally.
- It reads a selection or page text when you mark text, ask about a selection, attach a page, or generate Markdown.

## What leaves the browser

The extension itself sends data only to the AI service you configure. Apart from AI requests, data leaves the browser only when you open and submit the feedback form, which is a normal web page hosted by Tally. The websites you visit, your AI provider, and Tally have their own privacy policies.

Chat, selection questions, chat with a page attached, and Markdown generation use the same saved AI service. Testing the connection or saving a new service or API key requests the model list without sending page content. Remote services require HTTPS. Loopback services may use HTTP. Requests reject redirects, carry no cookies, and send no referrer. Responses larger than 2 MB are not read.

Your AI provider, which may be a relay, receives the request content and ordinary network information such as your IP address, and handles it under its own terms and privacy policy. DistractedLab does not operate that service and does not receive these requests.

The request contains the selected template or instruction and, depending on the action:

- Chat: your question and up to six recent messages that fit the budget. Attaching a page includes its title and the relevant passages shown in the preview.
- Explain selection: clicking the button sends the page title, an explanation request, the selected text (up to 12,000 characters extracted), and a short excerpt of nearby text. The chat draft and any attached page text stay in the composer.
- Summarize notes and annotations: the page title, mark types (highlight, underline or standalone annotation), passages, annotations and page remarks that fit the budget. Current-page Markdown uses located marks in reading order. For a separate historical review, you can choose to send currently unlocated quotations and annotations with their last known relative order or an unknown-order label. This choice starts off for each request.
- Page summary and structured notes: the page title and passages selected across sections. The preview indicates omissions due to extraction and request limits.

## What is not sent

Not sent: page URLs, mark colors, underline shapes, locator offsets, images, records from other pages, or the API key in the body. The key travels only in the Authorization header. Chat history is kept in memory for the current side-panel session and is lost when the panel closes.

## Feedback form

The feedback link in About opens the Tally form for your interface language in a new tab. The extension does not pre-fill or transmit your notes, page addresses, browsing history, or API key. Tally receives what you type and submit, plus ordinary network information such as your IP address, and handles it under [Tally’s privacy notice](https://tally.so/help/privacy-policy). Submissions are read to answer and improve the product. Please do not submit API keys, passwords, or other secrets.

## The API key

- The key is encrypted with AES-256-GCM in the extension’s local database. The decryption key is stored in the same database, so this keeps the plaintext out of backups, exports, and casual storage reads, but it does not protect against someone who can access your browser profile or operating-system account.
- The key is sent only to your AI provider, over HTTPS, in the Authorization header.
- The key is excluded from backups.
- The key cannot be recovered after uninstalling the extension or losing its local data. Removing it from this device does not revoke it; revoke it at the provider if a device is lost or exposed.

## How long data is kept and how to remove it

Because the records are only in your browser, DistractedLab does not have access to them and cannot read, export, or delete them for you. Feedback submissions are held by Tally; use the [feedback form](https://tally.so/r/X54k7L) for questions about them.

- Local records remain until you delete them, clear browser data, or uninstall the extension.
- You can view your records in the Notes Library and export them as JSON from Backup and restore.
- Delete a page and its marks and remarks in the Notes Library, or remove the key in AI settings.
- Uninstalling the extension removes its local records, settings, and key. Revoking its site access stops marking and highlight restoration.
- Chat history is in memory and disappears when the side panel closes.
- Backups, Markdown files, and files in your Vault folder are outside the extension and remain until you delete them.

## Permissions

- activeTab, scripting: add and restore marks on the page you are viewing.
- tabs: read the current tab’s title and URL to match records.
- storage: store local records and settings.
- sidePanel, contextMenus: show the side panel and the right-click menu.
- `file:///*`: read local HTML files to add marks after you enable Allow access to file URLs in Chrome’s extension details; the file address is stored in your local records.
- Optional permissions: access to the AI endpoint you enter and downloading exported files; both are requested only when used.

## Changes

If this page changes, the effective date at the top is updated.

## Contact

For privacy questions, use the [feedback form](https://tally.so/r/X54k7L).

© 2026 DistractedLab. All rights reserved.
