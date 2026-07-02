# LCUU-Tier-Update
Use this to mantaine our beloved LCUU

An automated Python tool designed to streamline the tiering process for Smogon's Little Cup (LC) format. This script downloads monthly usage statistics directly from Smogon, calculates tier shifts based on dynamic standard metrics (T-values), and generates formatted BBCode ready for forum posts. 

It also includes a supplementary script for formatting Viability Rankings (VR).

## Features
* **Automated Data Retrieval:** Securely fetches the latest `gen9lc-1630.txt` usage stats from Smogon while bypassing basic Cloudflare protections.
* **Interactive Configuration:** Dynamically adjusts the target date (YYYY-MM), calculates the correct Smogon cycle quarter and month, and applies the appropriate mathematical cutoff metrics.
* **Dynamic Database:** Automatically moves Pokémon between tiers (e.g., from LC OU to LC UU) based on the calculated shifts and updates the local JSON database file.
* **BBCode Report Generation:** Outputs a clean, forum-ready tier shift report with usage percentages.
* **VR Formatter:** Converts raw lists of Pokémon and tiers into highly formatted, color-coded BBCode for Viability Ranking threads.

## Files Overview
* `tierchanges.py`: The main interactive script. It handles downloading stats, processing the math, generating the report, and updating the JSON database.
* `tiers.json`: The live database containing the current tier placements for all LC Pokémon[cite: 7]. This file is automatically updated whenever `tierchanges.py` processes new shifts.
* `vrpostupdated.py`: A supplementary script that takes raw text lists of Pokémon and tiers and outputs formatted BBCode with official Smogon tier colors.
* `stats.txt`: The raw text file downloaded from Smogon containing the monthly usage data[cite: 4, 6]. 
* `tier_shift_report.txt`: The generated output file containing the BBCode summary of rises and drops[cite: 5, 6].

## Prerequisites
* Python 3.x installed on your system.
* No external libraries required (uses built-in `urllib`, `json`, `math`, and `os` modules).

## tierchanges.py
1. Ensure `tierchanges.py` and `tiers.json` are in the same folder.
2. Open your terminal or command prompt and run the script:
   `python tierchanges.py`
The script will prompt you to enter the target year and month (e.g., 2026-06).  It will automatically:
Determine the current Smogon Cycle (Quarter and Month).
Download the relevant usage stats and save them as stats.txt.
Calculate the usage cutoffs and determine any Rises or Drops.
Generate a BBCode report and save it to tier_shift_report.txt
Reorganize the tier arrays alphabetically and overwrite tiers.json with the new tierings.
CustomizationTo tweak the standard configuration (such as adding recently banned Pokémon so their residual usage doesn't skew data, or changing the base T-value), open tierchanges.py in a text editor and modify the variables at the top of the file under the Configuration Settings section.

##How to Use the VR Formatter
1. Open vrpostupdated.py in a text editor.
2. Paste your raw column of Pokémon into the mons_input variable.
3. Paste your corresponding column of tiers (S, A+, A, etc.) into the tiers_input variable.
4. Run the script: `python vrpostupdated.py`
Copy the outputted BBCode directly into the Smogon forums.
