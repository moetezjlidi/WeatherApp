# AppMeteo - Weather Application

A comprehensive weather application built with JavaFX that provides current weather information and 7-day forecasts for cities worldwide. The application offers both a graphical user interface (GUI) and a command-line interface (CLI) for user convenience.

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
  - [GUI Application](#gui-application)
  - [CLI Application](#cli-application)
- [Building and Testing](#building-and-testing)
- [Project Structure](#project-structure)
- [Technologies Used](#technologies-used)
- [API Information](#api-information)
- [Contributing](#contributing)
- [License](#license)
- [Authors](#authors)

## Features

### Core Features
- **Real-time Weather Data**: Get current weather information for any city worldwide
- **7-Day Forecast**: View weather predictions for the next 7 days
- **Hourly Forecast**: Access detailed 24-hour weather forecasts
- **Favorite Cities**: Save up to 6 favorite cities for quick access
- **Temperature Charts**: Visualize temperature trends with interactive line charts
- **Dual Interface**: Choose between GUI and CLI based on your preference
- **Weather Icons**: Visual representation of weather conditions
- **Multiple Temperature Views**: Morning, afternoon, and evening temperatures

### GUI Features
- Interactive date picker (limited to next 7 days)
- Visual weather icons
- Temperature trend graphs
- Favorite cities management with quick view
- Hourly forecast display

### CLI Features
- Simple command-based interface
- Favorite cities management (add/remove)
- Weather lookup by city and date
- Displays weather for favorite cities on startup

## Prerequisites

Before you begin, ensure you have the following installed:

- **Java Development Kit (JDK)**: Version 11 or higher
  - [Download JDK](https://www.oracle.com/java/technologies/downloads/)
- **Gradle**: Version 6.0 or higher (or use the included Gradle wrapper)
  - The project includes Gradle wrapper scripts (`gradlew` and `gradlew.bat`)
- **JavaFX**: Included via Gradle dependencies
- **Internet Connection**: Required for fetching weather data from OpenWeatherMap API

### System Requirements
- **Operating System**: Windows, macOS, or Linux
- **Memory**: Minimum 512 MB RAM (1 GB recommended)
- **Display**: For GUI, a display resolution of at least 800x600

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/moetezjlidi/WeatherApp.git
cd WeatherApp
```

### 2. Build the Project

Using Gradle wrapper (recommended):

**On Linux/macOS:**
```bash
./gradlew build
```

**On Windows:**
```bash
gradlew.bat build
```

Or using installed Gradle:
```bash
gradle build
```

## Configuration

### API Key Setup

The application uses the OpenWeatherMap API. The current implementation includes a default API key, but for production use, you should obtain your own:

1. Sign up at [OpenWeatherMap](https://openweathermap.org/api)
2. Get your free API key
3. Update the API key in the following files:
   - `src/main/java/app/appmeteo/controller/AppMeteoController.java`
   - Look for the `appid` parameter in API URLs

**Example:**
```java
String url = "http://api.openweathermap.org/data/2.5/weather?q=" + ville + "&appid=YOUR_API_KEY&units=metric";
```

### Favorite Cities Configuration

Favorite cities are stored in:
```
src/main/java/app/appmeteo/controller/fav.txt
```

You can manually edit this file or use the application to manage favorites.

## Usage

### GUI Application

Launch the graphical interface:

**Using Gradle:**
```bash
./gradlew run
```

**Using Java:**
```bash
java -jar build/libs/appmeteo-0.0.0.jar
```

#### GUI Instructions:
1. **Search for a City**: Enter a city name in the text field and select a date from the date picker
2. **View Weather**: Click the search button to display weather information
3. **Manage Favorites**:
   - Add cities to favorites (maximum 6 cities)
   - View favorite cities on the left panel
   - Remove cities from favorites
4. **View Charts**: Click the chart button to see temperature trends
5. **Hourly Forecast**: Access detailed hourly predictions for the next 24 hours

### CLI Application

Launch the command-line interface:

```bash
./gradlew runCLI
```

#### CLI Commands:

- **`help`**: Display all available commands
- **`weather`**: Look up weather for a specific city and date
  - You'll be prompted to enter a city name
  - Enter a date in format: `dd/MM/yyyy`
- **`favorite`**: Manage favorite cities
  - `add [CITY]`: Add a city to favorites (e.g., `add Paris`)
  - `remove [CITY]`: Remove a city from favorites (e.g., `remove Paris`)
  - `done`: Exit favorite management mode
- **`end`**: Close the application

#### CLI Example Session:

```
Welcome to the weather app

Input your command please (type 'help' for see all commands) : weather

Input your city : Paris
Input a date (dd/MM/yyyy) : 05/02/2026

On 05/02/2026 in Paris, it will be :
8 °C in the morning.
12 °C in the afternoon.
10 °C in the evening.
There will be a clear sky.
```

## Building and Testing

### Run Tests

Execute the test suite:

```bash
./gradlew test
```

For headless testing (useful in CI environments):
```bash
./gradlew test -Pheadless=true
```

### Generate Javadoc

Generate API documentation:

```bash
./gradlew javadoc
```

Documentation will be available in `build/docs/javadoc/`

### Clean Build

Remove build artifacts:

```bash
./gradlew clean
```

### Full Build Cycle

```bash
./gradlew clean build test
```

## Project Structure

```
WeatherApp/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── app/
│   │   │       └── appmeteo/
│   │   │           ├── AppMeteo.java          # Main GUI application
│   │   │           ├── AppMeteoCLI.java       # CLI application
│   │   │           ├── controller/
│   │   │           │   ├── AppMeteoController.java  # GUI controller
│   │   │           │   └── fav.txt           # Favorite cities storage
│   │   │           └── model/
│   │   │               └── Authors.java       # Authors model
│   │   └── resources/
│   │       └── app/
│   │           └── appmeteo/
│   │               └── view/
│   │                   ├── appmeteo.fxml     # Main GUI layout
│   │                   └── prev.fxml         # Preview layout
│   └── test/
│       └── java/
│           └── app/
│               └── appmeteo/
│                   └── model/
│                       ├── AuthorsTest.java
│                       └── AppMeteoCLITest.java
├── build.gradle                # Gradle build configuration
├── settings.gradle             # Project settings
├── gradlew                     # Gradle wrapper (Unix)
├── gradlew.bat                 # Gradle wrapper (Windows)
└── README.md                   # This file
```

## Technologies Used

### Core Technologies
- **Java 11**: Primary programming language
- **JavaFX**: GUI framework for the desktop application
- **Gradle**: Build automation and dependency management

### Libraries and Dependencies
- **JavaFX Controls, FXML, Web**: UI components and layout
- **JSON-Java (org.json)**: JSON parsing for API responses
- **OpenWeatherMap API**: Weather data provider
- **Ikonli**: Icon support for JavaFX
  - FontAwesome 5 pack
  - Material Design pack
- **ControlsFX**: Enhanced JavaFX controls
- **Griffon JavaFX**: Additional JavaFX utilities

### Testing Frameworks
- **JUnit 5 (Jupiter)**: Unit testing framework
- **TestFX**: JavaFX testing framework
- **OpenJFX Monocle**: Headless testing support

## API Information

### OpenWeatherMap API

This application uses the following OpenWeatherMap API endpoints:

1. **Current Weather Data**:
   - Endpoint: `http://api.openweathermap.org/data/2.5/weather`
   - Purpose: Get current weather for a specific city

2. **One Call API**:
   - Endpoint: `https://api.openweathermap.org/data/2.5/onecall`
   - Purpose: Get 7-day forecast and hourly data

### API Response Format
- Temperature: Metric units (Celsius)
- Timezone: UTC
- Data includes: temperature, weather description, humidity, wind speed, and more

### Rate Limits
- Free tier: 60 calls per minute
- Daily limit: 1,000,000 calls (free tier)

For more information, visit [OpenWeatherMap API Documentation](https://openweathermap.org/api)

## Contributing

Contributions are welcome! Here's how you can help:

### Reporting Issues
1. Check if the issue already exists in the issue tracker
2. Provide detailed description of the problem
3. Include steps to reproduce
4. Mention your environment (OS, Java version, etc.)

### Submitting Pull Requests
1. Fork the repository
2. Create a new branch for your feature: `git checkout -b feature-name`
3. Make your changes
4. Write or update tests as needed
5. Ensure all tests pass: `./gradlew test`
6. Commit your changes: `git commit -m 'Add some feature'`
7. Push to your fork: `git push origin feature-name`
8. Submit a pull request

### Coding Standards
- Follow Java naming conventions
- Add comments for complex logic
- Write unit tests for new features
- Ensure code is properly formatted
- Update documentation as needed

## License

This project was created as part of a software engineering course (UE Projet: initiation génie logiciel).

## Authors

**Moetez Jlidi**
- GitHub: [@moetezjlidi](https://github.com/moetezjlidi)

### Project Group
- This is a group project: **Meteo GROUPE S**

---

## Acknowledgments

- Weather data provided by [OpenWeatherMap](https://openweathermap.org/)
- Weather icons from OpenWeatherMap
- Built with JavaFX framework

## Support

For questions, issues, or suggestions:
1. Open an issue in the GitHub repository
2. Contact the project maintainers

---

**Note**: This application is for educational purposes as part of a software engineering course project.
