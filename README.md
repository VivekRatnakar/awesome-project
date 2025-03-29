# awesome-project LLM-Based Automation Agent

## Overview
This project is an automation agent designed to execute plain-English tasks using a Large Language Model (LLM). The agent automates various operational and business-related tasks for DataWorks Solutions, integrating seamlessly into the Continuous Integration (CI) pipeline.

## Features
- **Automated task execution** using an LLM for intermediate transformation.
- **REST API** with endpoints for executing tasks and reading results.
- **Operational and business automation tasks** handled effectively.
- **Security constraints** ensuring safe data handling.
- **Dockerized deployment** for easy execution and reproducibility.

## API Endpoints
### 1. Execute a Task
```http
POST /run?task=<task description>
```
- Parses the instruction and executes the required steps.
- **Responses:**
  - `200 OK`: Task executed successfully.
  - `400 Bad Request`: Error in task description.
  - `500 Internal Server Error`: Error in agent execution.

### 2. Read a File
```http
GET /read?path=<file path>
```
- Retrieves the content of the specified file.
- **Responses:**
  - `200 OK`: File content returned.
  - `404 Not Found`: File does not exist.

## Phase A: Operations Automation Tasks
1. **Generate Data Files:** Install `uv` (if required) and execute `datagen.py`.
2. **Format Markdown:** Use `prettier@3.4.2` to format `/data/format.md`.
3. **Count Wednesdays:** Count occurrences in `/data/dates.txt` and save the result.
4. **Sort Contacts:** Sort contacts in `/data/contacts.json` and save the sorted list.
5. **Extract Log Entries:** Write the first line of the 10 most recent log files.
6. **Index Markdown Files:** Extract titles and create `/data/docs/index.json`.
7. **Extract Email Sender:** Parse `/data/email.txt` using LLM and extract sender.
8. **Extract Credit Card Number:** Use LLM to extract data from `/data/credit-card.png`.
9. **Find Similar Comments:** Identify the most similar comments using embeddings.
10. **Calculate Ticket Sales:** Query SQLite database and save total sales for "Gold" tickets.

## Phase B: Business Automation Tasks
1. **API Data Fetching:** Retrieve data from an external API and save it.
2. **Git Repository Operations:** Clone a repository and make a commit.
3. **SQL Query Execution:** Run queries on SQLite or DuckDB.
4. **Web Scraping:** Extract relevant data from web pages.
5. **Image Processing:** Compress or resize images.
6. **Audio Transcription:** Convert MP3 files to text.
7. **Markdown to HTML Conversion:** Convert Markdown files to HTML format.
8. **CSV Filtering:** Implement an API endpoint for filtering CSV data and returning JSON.

## Security Constraints
- **Restricted Access:** The agent cannot access data outside `/data`.
- **Data Integrity:** No files can be deleted.

## Deployment Instructions
1. Clone the repository:
   ```sh
   git clone https://github.com/VivekRatnakar/awesome-project.git
   ```
2. Build the Docker image:
   ```sh
   docker build -t vivekratnakar/awesome-project.git .
   ```
3. Run the Docker container:
   ```sh
   podman run --rm -e AIPROXY_TOKEN=$AIPROXY_TOKEN -p 8000:8000 vivekratnakar/awesome-project.git
   ```

## Evaluation Criteria
1. **Correctness:** Each task is validated via `run` and `read` API calls.
2. **Security Compliance:** The agent follows security constraints.
3. **Performance:** Each API call completes within 20 seconds.
4. **Code Uniqueness:** Bonus points for diverse implementations.

## License
This project is licensed under the MIT License.

---
### Submission Checklist
- [x] Public GitHub repository with an MIT LICENSE file.
- [x] Working Dockerfile for building the application.
- [x] Public Docker image.
- [x] Automated API testing.
- [x] Submission via the provided Google Form.
