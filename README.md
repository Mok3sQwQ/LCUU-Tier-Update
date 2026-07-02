# LCUU-Tier-Update
Use this to mantain our beloved LCUU

An automated Python tool designed to streamline the tiering process for Smogon's Little Cup (LC) format. This script downloads monthly usage statistics directly from Smogon, calculates tier shifts based on dynamic standard metrics (T-values), and generates formatted BBCode ready for forum posts. 

It also includes a supplementary script for formatting Viability Rankings (VR).

## Features
* **Automated Data Retrieval:** Securely fetches the latest `gen9lc-1630.txt` usage stats from Smogon while bypassing basic Cloudflare protections.
* **Interactive Configuration:** Dynamically adjusts the target date (YYYY-MM), calculates the correct Smogon cycle quarter and month, and applies the appropriate mathematical cutoff metrics.
* **Dynamic Database:** Automatically moves Pokémon between tiers (e.g., from LC OU to LC UU) based on the calculated shifts and updates the local JSON database file.
* **BBCode Report Generation:** Outputs a clean, forum-ready tier shift report with usage percentages.
* **VR Formatter:** Converts raw lists of Pokémon and tiers into highly formatted, color-coded BBCode for Viability Ranking threads.

## Files Overview
* `tier_updater.py`: The main interactive script. It handles downloading stats, processing the math, generating the report, and updating the JSON database.
* `tiers.json`: The live database containing the current tier placements for all LC Pokémon. This file is automatically updated whenever `tier_updater.py` processes new shifts.
* `vr_post.py`: A supplementary script that takes raw text lists of Pokémon and tiers and outputs formatted BBCode with official Smogon tier colors.
* `stats.txt`: The raw text file downloaded from Smogon containing the monthly usage data. 
* `tier_shift_report.txt`: The generated output file containing the BBCode summary of rises and drops.

## Prerequisites
* Python 3.x installed on your system.
* No external libraries required (uses built-in `urllib`, `json`, `math`, and `os` modules).

## How to use tier_updater.py
1. Ensure `tier_updater.py` and `tiers.json` are in the same folder.
2. Open your terminal or command prompt and run the script:
   `python tier_updater.py`
3. The script will prompt you to enter the target year and month (e.g., 2026-06). It will automatically:
3.1. Determine the current Smogon Cycle (Quarter and Month).
3.2. Download the relevant usage stats and save them as stats.txt.
3.3. Calculate the usage cutoffs and determine any Rises or Drops.
3.4. Generate a BBCode report and save it to tier_shift_report.txt
3.5. Reorganize the tier arrays alphabetically and overwrite tiers.json with the new tierings.
Customization: To tweak the standard configuration (such as adding recently banned Pokémon so their residual usage doesn't skew data, or changing the base T-value), open tierchanges.py in a text editor and modify the variables at the top of the file under the Configuration Settings section.

## How to Use the vr_post.py
1. Open vr_post.py in a text editor.
2. Paste your raw column of Pokémon into the mons_input variable.
3. Paste your corresponding column of tiers (S, A+, A, etc.) into the tiers_input variable.
4. Run the script: `python vr_post.py`
5. Copy the outputted BBCode directly into the Smogon forums.

This script is an expanded version of a tool originally created by Albi_75. Huge thanks for providing the initial foundation! You can check out the original project here: https://github.com/Albi-75/lc-lowtiers-resources
