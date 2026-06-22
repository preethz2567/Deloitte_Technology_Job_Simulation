# Deloitte Technology Job Simulation - Telemetry Conversion  TASK1

## Overview
This project is part of the Deloitte Technology Job Simulation. The goal is to standardize telemetry data from different devices into a single, unified JSON format. The application reads device telemetry data in various formats and processes them into an expected, unified schema.

## Approach

The project requires parsing two distinct formats of telemetry data into a target unified schema:

### Data Format 1
- **Location:** The location is provided as a single string delimited by `/` (e.g., `japan/tokyo/keiyō-industrial-zone/daikibo-factory-meiyo/section-1`). We split this string and map the individual parts to `country`, `city`, `area`, `factory`, and `section`.
- **Status & Temperature:** The `operationStatus` and `temp` fields are extracted and nested under a `data` object as `status` and `temperature`.

### Data Format 2
- **Device ID & Type:** These are nested under a `device` object in the source, so we extract them into the top-level `deviceID` and `deviceType` properties.
- **Timestamp:** The timestamp is provided as an ISO 8601 string. We parse this string using `datetime.datetime.strptime()` and convert it into a Unix timestamp (milliseconds since the epoch) for consistency.
- **Location:** The location data is already structured as individual fields, so we map them directly into the nested `location` object.

### Testing
The script uses the built-in `unittest` module to verify that both data formats successfully convert to the exact structure defined in `data-result.json`.

## Usage
Simply run the script to execute the conversion logic and run the test suite:
```bash
python main.py
```
All test cases passed successfully!
<img width="1861" height="1030" alt="image" src="https://github.com/user-attachments/assets/73dc0a64-24eb-4c0a-bfd0-1c3756f62201" />
