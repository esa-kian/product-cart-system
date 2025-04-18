# Product and Cart System

This project is a Laravel application that implements a product catalog and cart system, along with a product card component built with Vue.js and Storybook.

## Features

- Product management with database migrations and seeders
- Cart functionality with the ability to add products and calculate totals
- Comprehensive test suite for cart operations
- Product card component with Storybook integration

## Requirements

- PHP 8.1+
- Composer
- Node.js and NPM

## Installation

1. Clone the repository
   ```bash
   git clone https://github.com/esa-kian/autovex
   cd autovex
   ```

2. Install PHP dependencies
   ```bash
   composer install
   ```

3. Install Node.js dependencies
   ```bash
   npm install
   ```

4. Create a `.env` file
   ```bash
   cp .env.example .env
   ```

5. Configure your database connection in `.env` (Optional)

6. Generate application key
   ```bash
   php artisan key:generate
   ```

7. Run migrations and seed the database
   ```bash
   php artisan migrate --seed
   ```

## Running Tests

```bash
php artisan test
```

## Running Storybook

```bash
npm run storybook
```

## Project Structure

### Part One: Database Structure
- `database/migrations` - Contains migrations for products and cart tables
- `app/Models` - Contains Product, Cart, and CartItem models
- `database/seeders` - Contains seeders for products
- `tests/Feature` - Contains test files for cart functionality
  - Testing cart operations (adding products)
  - Testing total price calculations with and without VAT

### Part Two: Frontend Components
- `frontend/src/components` - Contains Vue components
  - `ProductCard.vue` - Product card component
- `frontend/src/stories` - Contains Storybook stories
  - `ProductCard.stories.js` - Stories for different product card states

## Database Design

### Products Table
- `id` - Primary key
- `title` - Product name
- `sku` - Stock keeping unit (unique identifier)
- `images` - JSON array of image paths
- `description` - Product description text
- `price` - Product price
- `created_at`, `updated_at`, `deleted_at` - Timestamps with soft delete support

### Carts Table
- `id` - Primary key
- `session_id` - Unique session identifier
- `user_id` - Optional user ID for authenticated users
- `created_at`, `updated_at` - Timestamps

### Cart Items Table
- `id` - Primary key
- `cart_id` - Foreign key to carts table
- `product_id` - Foreign key to products table
- `quantity` - Number of items
- `created_at`, `updated_at` - Timestamps

## API Reference

### Cart Methods

#### Add a product to the cart
```php
$cart->addProduct($productId, $quantity = 1)
```

#### Get cart total (excluding VAT)
```php
$cart->total_price
```

#### Get cart total (including VAT)
```php
$cart->getTotalPriceWithVat($vatRate)
```

## Frontend Components

### ProductCard
A reusable Vue component that displays product information with the following features:
- Product image display
- Title and description
- Price display (with support for sale prices)
- Add to cart button with state tracking
- Responsive design with hover effects

## Development Guidelines

1. Run tests before committing changes
   ```bash
   php artisan test
   ```

2. Use Storybook to develop UI components in isolation
   ```bash
   npm run storybook
   ```

3. Follow Laravel and Vue.js best practices
   - Use Laravel's Eloquent ORM for database operations
   - Keep controllers thin
   - Follow the single responsibility principle
   - Use Vue.js props and events for component communication

## License

This project is open-sourced software licensed under the MIT license.