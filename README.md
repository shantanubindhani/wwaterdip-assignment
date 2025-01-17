﻿# Task Management API

This project is a simple Task Management API required as an assignment by waterdip labs.
This has been built using Flask and SQLAlchemy with SQLite as the database. It provides a set of endpoints to manage tasks, allowing users to create, retrieve, update, and delete tasks. The API also supports bulk operations for adding and deleting tasks. It is tested using a separate test file.

## Project Structure

```
.
├── dev
│   ├── tasks.py           # Main application file that runs the API server
│   └── task_model.py      # Model file that handles database interactions
├── tests
│    ├── ss1.png            # Screenshot of API sample run
│    ├── ss2.png
│    └── test.py            # Test file containing tests for API endpoints
├── run.sh                      # Bash script to automate running the API and ├── tests
├── README.md                   # Project documentation
├── requirements.txt            # List of project dependencies
└── LICENSE
```

## Requirements

Make sure you have the following installed:

- Python 3.x

You can install the required Python packages using pip. A `requirements.txt` file is provided for convenience:

```bash
pip install -r requirements.txt
```

## Usage

1. **Run the API Server and Tests**:

   You can run the API server and tests using the provided `run.sh` script:

   ```bash
   chmod +x run.sh   # Make the script executable
   ./run.sh          # Execute the script
   ```

   This script checks if the required directories exist, starts the API server in the background, waits for it to initialize, and then runs the tests.

2. **API Endpoints**:

   The following API endpoints are available:

   - **Create Task**: `POST /v1/tasks`
     - Body: `{"title": "Task Title"}`
     - Response: `{"id": <task_id>}`

   - **Bulk Create Tasks**: `POST /v1/tasks`
     - Body: `{"tasks": [{"title": "Task Title 1"}, {"title": "Task Title 2"}]}`
     - Response: `{"id": [<task_id1>, <task_id2>]}`

   - **List All Tasks**: `GET /v1/tasks`
     - Response: `{"tasks": [{"id": <task_id>, "title": "Task Title", "is_completed": false}]}`

   - **Get Task by ID**: `GET /v1/tasks/<task_id>`
     - Response: `{"id": <task_id>, "title": "Task Title", "is_completed": false}`

   - **Update Task**: `PUT /v1/tasks/<task_id>`
     - Body: `{"title": "Updated Task Title", "is_completed": true}`
     - Response: `204 No Content`

   - **Delete Task**: `DELETE /v1/tasks/<task_id>`
     - Response: `204 No Content`

   - **Bulk Delete Tasks**: `DELETE /v1/tasks`
     - Body: `{"tasks": [{"id": <task_id1>}, {"id": <task_id2>},]}` 
     - Response: `204 No Content`

## Testing

The `test.py` file contains several test functions that use the `requests` library to send requests to the API and validate the responses:

- **test_create_task**: Tests the creation of a new task.
- **test_list_all_tasks**: Tests retrieving the list of tasks.
- **test_get_task**: Tests retrieving a task by its ID.
- **test_update_task**: Tests updating an existing task.
- **test_delete_task**: Tests deleting a task by its ID.

To run the tests manually, you can execute:

```bash
pytest tests/test.py
```
## Sample run
<img src="./tests/ss1.png" alt="Image 1" width="700" height="400">
<img src="./tests/ss2.png" alt="Image 2" width="700" height="300">



## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
