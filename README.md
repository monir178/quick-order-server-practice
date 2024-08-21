# AmarPay Backend Integration 
## API Documentation

## Base URL
**Production:**  
`https://quick-order-server.vercel.app/`

## Endpoints

### 1. Get All Products
- **Endpoint:** `/api/v1/product/`
- **Method:** `GET`
- **Description:** Retrieves a list of all available products.
- **Request:**
  - **URL:** `[Base URL]/api/v1/product/`
  - **Headers:** None
  - **Body:** None


### 2. Get Product by ID
- **Endpoint:** `/api/v1/product/:id`
- **Method:** `GET`
- **Description:** Retrieves details of a specific product by its ID.
- **Request:**
  - **URL:** `[Base URL]/api/v1/product/:id`
  - **Path Parameter:** 
    - `id` (string) - The ID of the product to retrieve.
  - **Headers:** None
  - **Body:** None


### 3. Create Order
- **Endpoint:** `/api/v1/order/create`
- **Method:** `POST`
- **Description:** Creates a new order with the provided user and product details.
- **Request:**
  - **URL:** `[Base URL]/api/v1/order/create`
  - **Headers:** 
    - `Content-Type: application/json`
  - **Body:** 
    ```json
    {
      "user": {
        "name": "John Doe",
        "email": "john.doe@example.com",
        "phone": "+1234567890",
        "address": "123 Elm Street, Springfield, IL, 62701"
      },
      "products": [
        {
          "product": "66c213b684e1efacd201fc7a",
          "quantity": 2
        },
        {
          "product": "66c213b684e1efacd201fc81",
          "quantity": 1
        }
      ]
    }
    ```
- **Response:**
  ```json
  {
    "success": true,
    "message": "Order created successfully!",
    "data": {
        "result": "true",
        "payment_url": "https://sandbox.aamarpay.com/paynow.php?track=AAM1723999262542317"
    }
  }
  ```


### 4. Verify Payment
- **Endpoint:** `/api/payment/verify`
- **Method:** `GET`
- **Description:** Verifies the payment status of a transaction.
- **Request:**
  - **URL:** `[Base URL]/api/payment/verify?transactionId=TNX-ID`
  - **Query Parameter:** 
    - `transactionId` (string) - The transaction ID of the payment to verify.
  - **Headers:** None
  - **Body:** None



## Notes
- Ensure that the `transactionId` used for payment verification is accurate to avoid false verification results.
- The payment URL generated in the response of order creation should be used to redirect users for completing their payment.