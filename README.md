# E-Commerce API Demo (Ruby on Rails)

This is a demo project created to compare the development experience of using various different editors/IDEs with AI features.

This project implements a RESTful API for an e-commerce application, built with Ruby on Rails. The implementation uses PostgreSQL for database storage and follows REST principles for resource management.

## Features

- Complete CRUD operations for Customers, Shop Item Categories, Shop Items, and Orders
- Data validations with descriptive error messages
- RESTful API endpoints returning JSON responses
- Comprehensive test suite for all endpoints
- Docker support for easy deployment

## System Requirements

* Ruby 3.2.8 or higher
* Rails 8.0.2 or higher
* PostgreSQL 12 or higher

## Getting Started

### Setup and Installation

1. Clone the repository:
   ```
   git clone https://github.com/dpashkevich/demo-ecommerce-api.git
   cd demo-ecommerce-api
   ```

2. Install dependencies:
   ```
   bundle install
   ```

3. Database setup:
   
   Ensure PostgreSQL is running on your system. Then create and set up the database:
   ```
   bin/rails db:create
   bin/rails db:migrate
   ```

4. Seed the database with sample data:
   ```
   bin/rails db:seed
   ```

5. Running the server:
   ```
   bin/rails server
   ```
   The API will be available at `http://localhost:3000`.

### Running Tests

Run the test suite to ensure everything is working correctly:
```
bin/rails test
```

Run RuboCop to check code style:
```
bundle exec rubocop
```

## API Endpoints

The API provides the following endpoints:

### Customers

- `GET /customers` - List all customers
- `GET /customers/:id` - Get a specific customer
- `POST /customers` - Create a new customer
- `PATCH/PUT /customers/:id` - Update a customer
- `DELETE /customers/:id` - Delete a customer

### Shop Item Categories

- `GET /shop_item_categories` - List all categories
- `GET /shop_item_categories/:id` - Get a specific category
- `POST /shop_item_categories` - Create a new category
- `PATCH/PUT /shop_item_categories/:id` - Update a category
- `DELETE /shop_item_categories/:id` - Delete a category

### Shop Items

- `GET /shop_items` - List all shop items
- `GET /shop_items/:id` - Get a specific shop item
- `POST /shop_items` - Create a new shop item
- `PATCH/PUT /shop_items/:id` - Update a shop item
- `DELETE /shop_items/:id` - Delete a shop item

### Orders

- `GET /orders` - List all orders
- `GET /orders/:id` - Get a specific order
- `POST /orders` - Create a new order
- `PATCH/PUT /orders/:id` - Update an order
- `DELETE /orders/:id` - Delete an order

## Data Models

### Customer
- ID (integer)
- Name (string)
- Surname (string)
- Email (string)

### ShopItemCategory
- ID (integer)
- Title (string)
- Description (string)

### ShopItem
- ID (integer)
- Title (string)
- Description (string)
- Price (decimal)
- Categories (list of ShopItemCategory)

### OrderItem
- ID (integer)
- ShopItem (ShopItem)
- Quantity (integer)

### Order
- ID (integer)
- Customer (Customer)
- Items (list of OrderItem)

## Deployment with Docker

This application includes Docker configuration for easy deployment:

1. Build the Docker image:
   ```
   docker build -t ecommerce-api .
   ```

2. Run the container:
   ```
   docker run -p 3000:3000 ecommerce-api
   ```

### Using Kamal for Deployment

This project is configured to use Kamal for container-based deployments:

```
bundle exec kamal setup
bundle exec kamal deploy
```

## Troubleshooting

If you encounter database connection issues, ensure that:
1. PostgreSQL is installed and running
2. Database configuration in `config/database.yml` matches your PostgreSQL setup
3. The database user has appropriate permissions