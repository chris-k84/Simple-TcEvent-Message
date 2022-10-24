# TwinCAT Simple Event Messenger

## Contents

1. [Background](#Background})
2. [Project Description](#Description)
3. [System Design](#System-Design)
4. [Tests](#Tests)
5. [Support](#Support)
6. [Requirements](#Requirements)
7. [Documents](#Document-List)

## Background

I wanted to make some code and test what it did, but i found that i ended up writting lots of stuff just to get any idea what was going on. I was creating variables to log states and values so i could trace back issues. Then i discovered the **[ADSLOGSTR](https://infosys.beckhoff.com/english.php?content=../content/1033/tcplclib_tc2_system/31033611.html&id=)** block, which allows you to send messgaes to the TwinCAT output window. I made a basic block to encapulate this and have used it for ages. 

However, TwinCAT now has the **[TcEventLogger](https://infosys.beckhoff.com/content/1033/tc3_eventlogger/4278559115.html?id=4498649442738105815)** function, which allows you to log messages, set alarms and has pluggins for .NET, TcHMI as well as the dev interface.

So i started this project to make a new version of my old block. This block allows a simple interface to log messages which can be displayed in the XAE or TcHMI as required by logging to the event logger extension.

## Description

The block is quite simple it is based on the **[FB_TcMessage](https://infosys.beckhoff.com/content/1033/tc3_eventlogger/5003041163.html?id=3352751725740089607)** block from the Event Logger library. 

Its wrapped in a class that encapsulates the operation providing a method and property access.

The property allows you to set a severity for the logger, while the Send method allows you to send the event with a string message as long as the level is greater then or equal to the level set through the property.

## System Design

There is a interface for the class TcMessage_Ext, i currently envisage a few options for this however two seem most sensible.

1. use a TcMEssage_Ext concrete implementation at each required location, this allows modular control of elements allowing you to set levels independantly.

2. create a single instance of TcMessage_Ext and pass the interface into each object, this would mean a global implementation and global logging level. but would be more manageable in terms of architecture. 

## Tests

Tests will be performed using the TcUnit framework where possible. There currently isnt a integration framework for ST in IEC61131. However as far as possible test should be included and run before any code deployment after any modification.
Main documentation site is available on: **[www.tcunit.org](https://www.tcunit.org)**

## Support

code was developed/modified by:

1. Chris Knight

## Requirements: 

TwinCAT 3 4024.32

## Document List









