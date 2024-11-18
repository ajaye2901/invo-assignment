# Invoice Management API

This project is a simple Django REST Framework (DRF) application to manage invoices and their details. It provides endpoints to create and update invoices along with their associated details in a single request.

### Features

Nested Serializer: Handle invoice details inside the invoice payload.
Validation: Ensures line_total is correctly calculated as quantity * price.
Create and Update: Insert or modify invoices and their details through the /api/invoices/ endpoint.

### Assumptions

Unique Invoice Number: Each invoice has a unique invoice_number.
Line Total Validation: The line_total field must be exactly equal to quantity * price. This validation is enforced in the InvoiceDetailSerializer.
Details Replacement on Update: During updates, all old invoice details are deleted and replaced with the new ones provided in the payload.
Date Format: Dates in the payload should follow the YYYY-MM-DD format.

### Setup Instructions

1. Clone the Repository

``` git clone <repository-url> ```
``` cd <project-folder> ```

2. Set Up Virtual Environment

``` python -m venv env ```

``` source env/bin/activate  # For Linux/Mac ```
``` env\Scripts\activate     # For Windows  ```


3. Install Dependencies

``` pip install -r requirements.txt ```

4. Set Up the Database

``` python manage.py makemigrations ```
``` python manage.py migrate ```

5. Run the Development Server

``` python manage.py runserver ```

The API will be available at http://127.0.0.1:8000/api/invoices/.

API Endpoints
Create an Invoice
Endpoint: POST /api/invoices/
Payload:

{
  "invoice_number": "INV001",
  "customer_name": "John Doe",
  "date": "2024-11-12",
  "details": [
    {
      "description": "Product A",
      "quantity": 2,
      "price": 50.00,
      "line_total": 100.00
    },
    {
      "description": "Product B",
      "quantity": 1,
      "price": 75.00,
      "line_total": 75.00
    }
  ]
}


Update an Invoice
Endpoint: PUT /api/invoices/<id>/
Payload: Same as above.


