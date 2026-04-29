```mermaid
flowchart TD

%% ====================================================
%% Airport Customer Relationship Management System
%% Application Flow Diagram - Q3.2
%% ====================================================

%% ---------- ENTRY POINT ----------
Start([User opens the CRMS app]):::entry


%% ---------- IN-APP SCREENS ----------
Overview["<u>Screen 01</u><br/><b>Flights Overview</b><br/><i>List of saved flights with live status</i>"]:::screen

Detail["<u>Screen 02</u><br/><b>Flight Detail</b><br/><i>Full boarding-pass style breakdown</i>"]:::screen


%% ---------- SYSTEM-LEVEL TOUCHPOINTS ----------
Lock["<u>Screen 03</u><br/><b>Lock-screen Notification</b><br/><i>Compact alert delivered by iOS</i>"]:::system

LockExpanded["<u>Screen 04</u><br/><b>Notification Expanded</b><br/><i>Tap-and-hold reveals full alert content</i>"]:::system


%% ---------- USER ACTIONS ----------
Start -->|Launch app| Overview
Overview -->|Tap 'View' on a flight card| Detail
Detail -->|Tap back-chevron| Overview

%% Asynchronous server-pushed event - boarding gate change
Server[(<b>Server-side</b><br/><i>Gate change detected</i>)]:::server
Server -.->|Push notification| Lock
Lock -->|Tap-and-hold notification| LockExpanded
LockExpanded -->|Tap 'View in app'| Detail
Lock -->|Tap notification| Detail

```