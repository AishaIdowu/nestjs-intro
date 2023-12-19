<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="200" alt="Nest Logo" /></a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

  <p align="center">A progressive <a href="http://nodejs.org" target="_blank">Node.js</a> framework for building efficient and scalable server-side applications.</p>
    <p align="center">
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/dm/@nestjs/common.svg" alt="NPM Downloads" /></a>
<a href="https://circleci.com/gh/nestjs/nest" target="_blank"><img src="https://img.shields.io/circleci/build/github/nestjs/nest/master" alt="CircleCI" /></a>
<a href="https://coveralls.io/github/nestjs/nest?branch=master" target="_blank"><img src="https://coveralls.io/repos/github/nestjs/nest/badge.svg?branch=master#9" alt="Coverage" /></a>
<a href="https://discord.gg/G7Qnnhy" target="_blank"><img src="https://img.shields.io/badge/discord-online-brightgreen.svg" alt="Discord"/></a>
<a href="https://opencollective.com/nest#backer" target="_blank"><img src="https://opencollective.com/nest/backers/badge.svg" alt="Backers on Open Collective" /></a>
<a href="https://opencollective.com/nest#sponsor" target="_blank"><img src="https://opencollective.com/nest/sponsors/badge.svg" alt="Sponsors on Open Collective" /></a>
  <a href="https://paypal.me/kamilmysliwiec" target="_blank"><img src="https://img.shields.io/badge/Donate-PayPal-ff3f59.svg"/></a>
    <a href="https://opencollective.com/nest#sponsor"  target="_blank"><img src="https://img.shields.io/badge/Support%20us-Open%20Collective-41B883.svg" alt="Support us"></a>
  <a href="https://twitter.com/nestframework" target="_blank"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow"></a>
</p>
  <!--[![Backers on Open Collective](https://opencollective.com/nest/backers/badge.svg)](https://opencollective.com/nest#backer)
  [![Sponsors on Open Collective](https://opencollective.com/nest/sponsors/badge.svg)](https://opencollective.com/nest#sponsor)-->



# NestJS Products Service

This repository contains a NestJS service for managing products. The service provides functionality to insert, retrieve, update, and delete products. Each product has a unique identifier, title, description, and price.

## Installation

To use this service in your NestJS application, follow these steps:

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/your-repo.git
   ```

2. Navigate to the project directory:

   ```bash
   cd your-repo
   ```

3. Install dependencies:

   ```bash
   npm install
   ```

## Running the app

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```

## Usage

To use the `ProductsService` in your NestJS application, import it into your module and include it in the `providers` array.

```typescript
import { Module } from '@nestjs/common';
import { ProductsService } from './path-to-products-service/products.service';

@Module({
  providers: [ProductsService],
})
export class YourModule {}
```

Then, inject the `ProductsService` into your controllers or other services to interact with products.

### Example:

```typescript
import { Controller, Get, Param } from '@nestjs/common';
import { ProductsService } from './path-to-products-service/products.service';

@Controller('products')
export class ProductsController {
  constructor(private readonly productsService: ProductsService) {}

  @Get()
  getAllProducts() {
    return this.productsService.getProducts();
  }

  @Get(':id')
  getProductById(@Param('id') productId: string) {
    return this.productsService.getSingleProduct(productId);
  }

  // Add other CRUD operations as needed
}
```

## API Endpoints

- **GET /products**: Retrieve a list of all products.
- **GET /products/:id**: Retrieve details of a single product by its ID.
- **POST /products**: Insert a new product.
- **PUT /products/:id**: Update an existing product by ID.
- **DELETE /products/:id**: Delete a product by its ID.

## Methods

### `insertProduct(title: string, description: string, price: number): string`

Insert a new product with the given title, description, and price. Returns the ID of the newly created product.

### `getProducts(): Product[]`

Retrieve a list of all products.

### `getSingleProduct(productId: string): { product: Product }`

Retrieve details of a single product by its ID.

### `updateProduct(productId: string, title: string, desc: string, price: number): void`

Update an existing product by ID. Provide the new title, description, and/or price to update the product.

### `deleteProduct(prodId: string): void`

Delete a product by its ID.

## Error Handling

If a product is not found during retrieval or update operations, a `NotFoundException` is thrown.

Feel free to integrate and customize this service to suit your specific application requirements. If you encounter any issues or have suggestions, please open an issue on this repository.
