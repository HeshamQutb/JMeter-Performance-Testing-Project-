# JMeter Performance Testing Project

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![JMeter Version](https://img.shields.io/badge/JMeter-5.6-blue)](https://jmeter.apache.org/)
[![GitHub Issues](https://img.shields.io/github/issues/HeshamQutb/JMeter-Performance-Testing-Project-)](https://github.com/HeshamQutb/JMeter-Performance-Testing-Project-/issues)
[![GitHub Stars](https://img.shields.io/github/stars/HeshamQutb/JMeter-Performance-Testing-Project-?style=social)](https://github.com/HeshamQutb/JMeter-Performance-Testing-Project-)

## Table of Contents
- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Tools and Technologies](#tools-and-technologies)
- [Project Structure](#project-structure)
- [Setup and Configuration](#setup-and-configuration)
- [Detailed Steps for Execution](#detailed-steps-for-execution)
- [Load Profiling Configurations](#load-profiling-configurations)
- [SLA Analysis and Results](#sla-analysis-and-results)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Project Overview
This repository hosts a comprehensive JMeter-based performance testing project. The project demonstrates load testing for both API endpoints (using Restful Booker) and web user journeys (using JPetStore demo site). It includes script development for functional flows, parameterization for data independence, assertions for validation, and custom load profiles with SLA evaluations.

The project covers:
- **API Flow**: Authentication, booking creation, retrieval, conditional update, and deletion.
- **Web Flow**: User registration, product browsing, cart management, and order confirmation on JPetStore.
- **Performance Analysis**: 10-minute test with 2 users, SLA validation (error rates, response percentiles).
- **Load Profiles**: Stepping ramp-up to 100 users and spiked loads with holds.

All scripts adhere to best practices for realism and reliability, ensuring reproducibility across environments.

## Key Features
- **Parameterization**: Dynamic data handling via CSV, text-based response validations for each step (e.g., "Thank you, your order has been submitted." for web confirmation).
- **Environment Independence**: HTTP Request Defaults for base URL, protocol, and timeouts.
- **Realistic Simulation**: Constant Timers (1000ms think time) for user pauses, Cache and Cookie Managers for session management and cache clearing per iteration.
- **Error Handling**: Custom logic for conditional updates/deletes (e.g., If Controller with JEXL3 for ID checks).
- **Load Testing**: Aggregate Reports for metrics, with all SLAs passed (0.48% errors, 90% < 341ms, 99% < 1158ms).
- **Modular Design**: Simple Controllers for grouping steps, facilitating maintenance and scalability.

## Tools and Technologies
- **Apache JMeter (v5.6)**: Core tool for script development, recording, and load simulation.
- **JMeter Plugins Manager**: For advanced Thread Groups (Stepping and Ultimate).
- **Firefox Browser**: Used for recording web flows via JMeter's HTTP(S) Test Script Recorder (with proxy and certificate setup).
- **CSV Files**: For data parameterization (Test_data_UI.csv, Test_data_API.csv).
- **Other**: Debug Samplers for variable inspection, BeanShell/JEXL3 for dynamic logic (e.g., random usernames).

No additional installations required beyond JMeter and plugins.

## Project Structure
.
├── API\JMeter_Assignment_API.jmx     # Main script with API, Thread Group
├── API\Test_data_API.csv             # CSV for API create token credentials
├── API\Report.pdf                    # SLA analysis with Aggregate Report screenshot and table
├── UI\JMeter_Assignment_UI.jmx       # Main script with Web flows, Thread Group
├── UI\Test_data_UI.csv               # CSV for Web registration data
├── JMeter_Assignment_first.jmx       # Stepping Thread Group load profile
├── JMeter_Assignment_second.jmx      # Ultimate Thread Group spiked load profile
└── README.md                         # This file


## Setup and Configuration
1. **Download JMeter**: Get Apache JMeter v5.6 or later from [jmeter.apache.org/download_jmeter.cgi](https://jmeter.apache.org/download_jmeter.cgi). Extract and add `bin` to your PATH.
2. **Install Plugins**: Download plugins-manager.jar from [jmeter-plugins.org](https://jmeter-plugins.org/get/), place in `lib/ext`, restart JMeter. In Options > Plugins Manager, install "Stepping Thread Group" and "Ultimate Thread Group".
3. **Clone this Repository**: `git clone https://github.com/HeshamQutb/JMeter-Performance-Testing-Project-.git`.
4. **Prepare CSVs**: Place CSV files in JMeter's `bin` directory or update paths in the script's CSV Data Set Configs.
5. **Browser Setup for Recording (if re-recording)**: In Firefox, import JMeter certificate, set proxy to localhost:8888 for HTTP/HTTPS.

## Detailed Steps for Execution
### Functional Testing
1. Open `JMeter_Assignment.jmx` in JMeter GUI.
2. Ensure CSVs are loaded (check paths in CSV Data Set Configs).
3. Run with 1 thread (Run > Start).
4. Verify in View Results Tree: All assertions pass (green), with dynamic usernames and order confirmation text.

### Performance Testing
1. Enable "Performance Thread Group" (2 users, ramp-up 10s, duration 600s, loops forever).
2. Add/Enable Aggregate Report listener.
3. Run the test.
4. Export results to CSV if needed (`jmeter -n -t JMeter_Assignment.jmx -l results.csv`).
5. Analyze SLAs from TOTAL row (as in Report.pdf).

### Load Profile Preview
1. Open `JMeter_Assignment_first.jmx` > View Stepping Thread Group preview.
2. Open `JMeter_Assignment_second.jmx` > View Ultimate Thread Group schedules.

## Load Profiling Configurations
- **Stepping**: Ramp-up 100 users at 1/s, hold 3000s, ramp-down 1/s.
- **Spiked (Bonus)**: Normal 60 users (ramp 1/s, hold 600s, down 1/s); Spike A at 120s (+60 users at 10/s, hold 60s, down 10/s); Spike B at 360s (similar).

## SLA Analysis and Results
From the 10-minute run:
- Error %: 0.48% < 10% (Passed)
- 90% Line: 341 ms < 3000 ms (Passed)
- 99% Line: 1158 ms < 5000 ms (Passed)

See Report.pdf for screenshot and shaded table.

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/YourFeature`).
3. Commit changes (`git commit -m "Add YourFeature"`).
4. Push to branch (`git push origin feature/YourFeature`).
5. Open a Pull Request with details on changes.

Please follow code standards: Use descriptive sampler names, comment complex logic, and test before PR.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact
For questions or feedback, reach out via LinkedIn or email: [www.linkedin.com/in/hesham-qutb].
Project completed on October 29, 2025.
