# PulseGuard - Your Lightweight Health Check Solution

PulseGuard is a robust and adaptable solution designed to monitor the health and availability of critical application endpoints. This TypeScript-based project provides a simple yet powerful framework for configuring and executing periodic health checks, alerting stakeholders when anomalies are detected. Instead of relying on heavyweight monitoring platforms for simple endpoint verification, PulseGuard offers a streamlined, self-contained alternative, promoting faster deployment and reduced operational overhead.

This project addresses the need for quick and reliable endpoint monitoring without the complexities of full-fledged monitoring systems. It allows developers and operations teams to define custom health checks tailored to specific application requirements. PulseGuard excels at identifying unresponsive services, slow response times, and unexpected status codes. By automating the process of regular health checks, it enables proactive identification and resolution of potential issues before they impact users. The core goal is to ensure continuous service availability and minimize downtime, providing peace of mind and improving the overall user experience.

PulseGuard is designed for ease of integration and customization. It can be readily integrated into existing workflows, whether deployed as a standalone service or incorporated into larger monitoring pipelines. Its modular architecture promotes extensibility, allowing developers to add custom health check logic and notification channels to meet specific needs. The configuration is straightforward using environment variables and a configuration file, allowing easy deployment across different environments. With its focus on simplicity and flexibility, PulseGuard is an ideal solution for any team looking to improve the reliability and availability of their applications.

## Key Features

*   **Configurable Health Checks:** Define health checks with specific endpoints, HTTP methods (GET, POST, PUT, DELETE), expected status codes, and response body validations.
*   **Interval-Based Monitoring:** Schedule health checks to run at specified intervals, providing continuous monitoring and early detection of issues.
*   **Multiple Notification Channels:** Configure notifications via email, Slack, or other webhook-based services to alert stakeholders of failures.
*   **Customizable Thresholds:** Set thresholds for response times and error rates to trigger alerts only when predefined limits are exceeded.
*   **Detailed Logging:** Comprehensive logging of health check results, including timestamps, status codes, response times, and error messages, aiding in debugging and analysis.
*   **TypeScript-Based:** Written in TypeScript, providing strong typing, improved code maintainability, and enhanced developer experience.
*   **Lightweight Footprint:** Minimal dependencies and resource consumption, making it suitable for deployment in resource-constrained environments.

## Technology Stack

*   **TypeScript:** Used as the primary programming language, offering static typing and improved code quality.
*   **Node.js:** The runtime environment for executing the TypeScript code.
*   **Axios:** A promise-based HTTP client for making requests to the monitored endpoints.
*   **Winston:** A versatile logging library for recording health check results and errors.
*   **Nodemailer:** A module for sending email notifications. (Optional, if email notifications are enabled)
*   **dotenv:** Used for loading environment variables from a .env file.

## Installation

1.  **Clone the repository:**
    git clone https://github.com/uhsr/PulseGuard.git
    cd PulseGuard

2.  **Install dependencies:**
    npm install

3.  **Build the project:**
    npm run build

4.  **Create a .env file:**
    Create a .env file in the project root directory based on the `.env.example` file.

## Configuration

The application is configured using environment variables. Below are the available variables:

*   `NODE_ENV`: (Optional) Sets the environment (development, production, etc.). Defaults to `development`.
*   `PORT`: (Optional) The port the server will listen on. Defaults to `3000`.
*   `CONFIG_FILE`: (Required) Path to the configuration file in JSON format.
*   `EMAIL_ENABLED`: (Optional) Enable/Disable email notifications (true/false). Defaults to `false`.
*   `EMAIL_HOST`: (Required if `EMAIL_ENABLED` is true) The SMTP server hostname.
*   `EMAIL_PORT`: (Required if `EMAIL_ENABLED` is true) The SMTP server port.
*   `EMAIL_USER`: (Required if `EMAIL_ENABLED` is true) The SMTP server username.
*   `EMAIL_PASS`: (Required if `EMAIL_ENABLED` is true) The SMTP server password.
*   `EMAIL_FROM`: (Required if `EMAIL_ENABLED` is true) The sender email address.
*   `EMAIL_TO`: (Required if `EMAIL_ENABLED` is true) The recipient email address.
*   `SLACK_WEBHOOK_URL`: (Optional) The Slack webhook URL for sending notifications. If not provided, Slack notifications will be disabled.

The `CONFIG_FILE` specified should point to a JSON file containing the health check configurations. Example structure:

{
  "checks": [
    {
      "name": "API Endpoint Health",
      "url": "https://api.example.com/health",
      "method": "GET",
      "expectedStatusCode": 200,
      "interval": 60,
      "threshold": 200,
      "notificationChannels": ["email", "slack"]
    },
     {
      "name": "Database Connection",
      "url": "https://db.example.com/health",
      "method": "GET",
      "expectedStatusCode": 200,
      "interval": 300,
      "threshold": 500,
      "notificationChannels": ["slack"]
    }
  ]
}

## Usage

To start the application:

npm start

The application will start monitoring the endpoints defined in the configuration file and send notifications based on the configured channels. Logs will be written to the console.

## Contributing

We welcome contributions to PulseGuard! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write clear and concise commit messages.
4.  Submit a pull request with a detailed description of your changes.
5.  Ensure all tests pass before submitting.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/uhsr/PulseGuard/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to thank the open-source community for providing the libraries and tools that made this project possible.