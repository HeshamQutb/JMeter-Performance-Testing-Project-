# JMeter Performance Testing Assignment

[![JMeter Logo](https://jmeter.apache.org/images/logo.svg)](https://jmeter.apache.org/)

## Project Overview
This repository contains a complete JMeter-based performance testing project as part of a software testing assignment. It includes:
- **API Testing Flow**: Scripts for authenticating, creating, retrieving, updating, and deleting bookings using the Restful Booker API[](https://restful-booker.herokuapp.com).
- **Web Testing Flow**: End-to-end user journey simulation on the JPetStore demo site[](https://petstore.octoperf.com), covering registration, product selection, cart management, and order confirmation.
- **Load Profiling**: Configurations for stepping ramp-up (100 users) and spiked load profiles using JMeter plugins.
- **SLA Analysis**: Report on a 10-minute run with 2 users, validating error rates and response time percentiles.

The scripts follow best practices: parameterization via CSV, text-based assertions for navigation validation, HTTP Request Defaults for environment independence, constant timers for realistic pacing, cache/cookie management, and more.

## Features
- Parameterized data for registration and API bodies (e.g., random usernames to avoid duplicates).
- Custom assertions to verify page content and order submission ("Thank you, your order has been submitted.").
- Load test results with Aggregate Report and SLA validation (all passed: 0.48% errors, 90% < 341ms, 99% < 1158ms).
- Modular structure with Simple Controllers for each step.

<grok-card data-id="f9416e" data-type="image_card"></grok-card>


## Installation
1. Download and install Apache JMeter (version 5.5 or later) from [jmeter.apache.org](https://jmeter.apache.org/download_jmeter.cgi).
2. Install JMeter Plugins Manager (place plugins-manager.jar in lib/ext, restart JMeter) for Stepping/Ultimate Thread Groups.
3. Clone this repository: `git clone https://github.com/yourusername/jmeter-performance-testing-assignment.git`.
4. Place CSV files (auth_data.csv, booking_data.csv, petstore_data.csv) in the JMeter bin directory or specify full paths in the script.

## Usage
1. Open `JMeter_Assignment.jmx` in JMeter GUI.
2. For functional test: Run with 1 thread.
3. For performance (Question II): Enable the "Performance Thread Group" (2 users, 600s duration), run, view Aggregate Report.
4. For load profiles (Question III): Open `JMeter_Assignment_first.jmx` and `JMeter_Assignment_second.jmx` to preview configurations (no run needed).

Example run command (non-GUI): `jmeter -n -t JMeter_Assignment.jmx -l results.csv`.

## Screenshots
- Performance Dashboard Example:

<grok-card data-id="ffd475" data-type="image_card"></grok-card>


- SLA Validation Report (from assignment):
  (Insert your Report.pdf screenshot here or link to it in the repo.)

## Contributing
Feel free to fork and submit pull requests for improvements, such as additional assertions or distributed testing setups. Follow standard GitHub flow.

## License
MIT License - see [LICENSE](LICENSE) file for details.

Project completed on October 31, 2025. Contact: [Your Email/LinkedIn].
