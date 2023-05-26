# Flask Cafe API

This is a Flask-based API for managing cafes. It provides endpoints for retrieving, adding, updating, and deleting cafe information from a SQLite database.

## Prerequisites

- Python 3.x
- Flask
- Flask-SQLAlchemy
- dotenv

## Getting Started

1. Clone the repository:

   ```
   git clone <repository_url>
   ```

2. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Set up the database:

   The API uses a SQLite database to store cafe information. Create a file named `cafes.db` in the project directory to serve as the database.

4. Set environment variables:

   - Create a file named `.env` in the project directory.
   - Add the following line to the `.env` file and replace `<your_api_key>` with your desired API key:

     ```plaintext
     API_KEY=<your_api_key>
     ```

   Note: The API key is used for authorization purposes when deleting cafes.

5. Run the application:

   ```bash
   python main.py
   ```

   The API will be accessible at `http://localhost:5000`.

## API Endpoints

### GET /

- Description: Home page
- Response: Renders the `index.html` template.

### GET /random

- Description: Retrieve a random cafe from the database.
- Response: JSON object containing the details of a randomly selected cafe.

### GET /all

- Description: Retrieve details of all cafes in the database.
- Response: JSON object containing an array of cafe objects.

### GET /search

- Description: Search for a cafe by location.
- Query Parameter:
  - `loc`: Location of the cafe to search for.
- Response:
  - If a cafe is found at the specified location: JSON object containing the details of the cafe.
  - If no cafe is found at the specified location: JSON object with an error message.

### POST /add

- Description: Add a new cafe to the database.
- Request Body Parameters:
  - `name`: Name of the cafe (required).
  - `map_url`: URL of the cafe's location on a map (required).
  - `img_url`: URL of an image representing the cafe (required).
  - `loc`: Location of the cafe (required).
  - `sockets`: Availability of power sockets (required, boolean).
  - `toilet`: Availability of a toilet (required, boolean).
  - `wifi`: Availability of WiFi (required, boolean).
  - `calls`: Ability to take calls (required, boolean).
  - `seats`: Number of available seats (required).
  - `coffee_price`: Price of coffee (optional).
- Response: JSON object containing a success message if the cafe was added successfully.

### PATCH /update-price/<int:cafe_id>

- Description: Update the price of a cafe.
- Path Parameter:
  - `cafe_id`: ID of the cafe to update.
- Query Parameter:
  - `new_price`: New price of the cafe.
- Response:
  - If the cafe is found and the price is updated successfully: JSON object containing a success message.
  - If no cafe is found with the specified ID: JSON object with an error message and a status code of 404.

### DELETE /report-closed/<int:cafe_id>

- Description: Delete a cafe from the database.
- Path Parameter:
  - `cafe_id`: ID of the cafe to delete.
- Query Parameter:
  - `api-key`: API key for authorization.
- Response:
  - If the cafe is found and successfully deleted: JSON object containing a success message.
 

 - If no cafe is found with the specified ID: JSON object with an error message and a status code of 404.

## Documentation

For detailed information about the API endpoints and how to use them, refer to the [API Documentation](https://documenter.getpostman.com/view/27606790/2s93m5zgep) on Postman.

Feel free to explore the API and interact with the endpoints using the provided documentation.
