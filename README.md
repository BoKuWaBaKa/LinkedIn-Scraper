# LinkedIn Company Data Fetcher

This project is a web application that fetches LinkedIn company data such as the number of followers and employees for a given company. The application consists of a backend server built with Flask and a frontend built with React.

## Backend

The backend is built with Flask and uses Selenium for web scraping LinkedIn data. It includes the following dependencies:

- `Flask`: A lightweight WSGI web application framework in Python.
- `Flask-CORS`: A Flask extension for handling Cross-Origin Resource Sharing (CORS).
- `selenium`: A tool for automating web browsers.
- `BeautifulSoup`: A library for parsing HTML and XML documents.
- `bs2json`: A library to convert BeautifulSoup objects to JSON.

### Installation

1. **Clone the repository:**
    ```bash
    git clone https://github.com/youessaitch/linkedin-data-fetcher.git
    cd linkedin-data-fetcher
    ```

3. **Update the `driver_path` variable in the `SELENIUM/app.py` file, depending on the web browser you wish to use. I have provided the drivers for Chrome and Edge with this repository. (Versions may vary, so you can download the latest version of your web-driver from the internet.)**
    ```python
    example: (for me it was)
    driver_path = r"D:\linkedin-data-fetcher-master\SELENIUM\edgedriver_win64\msedgedriver.exe"
    ```

4. **Update the argument of `username.send_keys` and `pword.send_keys` in the `SELENIUM/app.py` file with your own Linkedin E-mail and Password**


5. **Run the backend server: (make sure to be on the path `\SELENIUM`)**
    ```python
    python app.py
    ```

### Code Explanation

- **`get_linkedin_data(company)`**: This function uses Selenium to log into LinkedIn and fetch the number of followers and employees for a specified company. It handles the login process, navigates to the company's LinkedIn page, scrapes the data, and returns it as a dictionary.
- **API Endpoint `/api/data`**: This POST endpoint receives a JSON object with the company name, calls the `get_linkedin_data` function, and returns the scraped data as a JSON response.

## Frontend

The frontend is built with React and styled-components for styling. It includes the following dependencies:

- `React`: A JavaScript library for building user interfaces.
- `styled-components`: A library for styling React components.
- `React useState hook`: For managing state in functional components.

### Installation

1. **Open up a new terminal window**

2. **Navigate to the `frontend` directory:**
    ```
    cd frontend
    ```

3. **Install the dependencies: (NOTE: update the package.json if the version gets too old)**
    ```bash
    npm install
    ```

4. **Run the React app:**
    ```bash
    npm start
    ```

### Code Explanation

- **App Component**: The main component that renders the form for inputting company names, handles form submission, and displays the fetched data.
  - **State Management**: Uses `useState` hook to manage the state for companies, data, loading, and error.
  - **handleChange**: Updates the `companies` state when the textarea value changes.
  - **handleSubmit**: Handles form submission, sends a POST request to the backend API for each company, and updates the state with the fetched data.
  - **Styled Components**: Utilizes `styled-components` for styling various parts of the application, such as the container, header, form, buttons, and result display.

## Usage

1. **Open 2 terminals on the LINKEDIN-DATA-FETCHER folder**

2. **Start the Backend Server in one of the terminals**:
    ```bash
    cd SELENIUM
    python app.py
    ```

3. **Start the Frontend Development Server on the other terminal**:
    ```bash
    cd frontend
    npm start
    ```

4. **Open the Application in a Browser**:
    - Navigate to `http://localhost:3000` in your web browser.
    - Enter company names in the textarea, each on a new line.
    - Click the "Get Data" button to fetch LinkedIn data for the entered companies.
    - The results will be displayed below.

## Notes

- **Manual OTP Entry**: In case login proceeds only through OTP verification, the script waits for manual OTP entry for 20 seconds(which you can change from the app.py file inside SELENIUM) during the LinkedIn login process. Ensure you enter the OTP within the given time frame.
- **LinkedIn Credentials**: Replace the placeholder `your-email@gmail.com` and `your-password` in the `get_linkedin_data` function with valid LinkedIn credentials.
- **Web-Driver Path**: Ensure the web driver's executable path is correct in the backend code

## Created by Sharath S(IIT Kharagpur'26)
### Demo video : https://tinyurl.com/msk44z2k
