# Medusa Plugin Wishlist

A plugin for Medusa that adds wishlist functionality to your e-commerce store.

## Installation

Run the following command in the directory of your Medusa backend to install the plugin:

### Using npm:

```sh
npm install medusa-v2-plugin-wishlist
```

### Using Yarn:

```sh
yarn add medusa-v2-plugin-wishlist
```

## Configuration

After installation, add the plugin to the `plugins` array in your Medusa configuration file `medusa-config.js` or `medusa-config.ts`:

```js
module.exports = defineConfig({
  plugins: [
    {
      resolve: "medusa-v2-plugin-wishlist",
      options: {},
    },
  ],
});
```

## Database Migration

Medusa Wishlist introduces new models in the database. To have it working, you need to execute migrations:

```sh
npx medusa db:migrate
```

## Features

- Create a Wishlist for a Customer
- Add products to a wishlist
- Remove products from a wishlist
- Retrieve a user's wishlist
- Share a wishlist

## Usage

Once installed and configured, the wishlist API will be available for use. You can use Medusa's REST endpoints to interact with the wishlist feature.

### Create a Wishlist for a Customer

You can create a wishlist for a customer using the following `cURL` command:

```sh
curl -X POST 'localhost:9000/store/customers/me/wishlists' \
--header 'x-publishable-api-key: {api_key}' \
--header 'Authorization: Bearer {token}'
```

If the wishlist is already created, it returns the existing wishlist.

### Add an Item to the Wishlist

You can add an item to a user's wishlist using the following `cURL` command:

```sh
curl -X POST 'localhost:9000/store/customers/me/wishlists/items' \
--header 'Content-Type: application/json'  \
--header 'x-publishable-api-key: YOUR_API_KEY' \
--header 'Authorization: Bearer YOUR_TOKEN' \
--data-raw '{
    "variant_id": "YOUR_VARIANT_ID"
}'
```

### Remove an Item from the Wishlist

You can remove an item from a user's wishlist using the following `cURL` command:

```sh
curl -X DELETE 'localhost:9000/store/customers/me/wishlists/items/{item_id}' \
--header 'x-publishable-api-key: YOUR_API_KEY' \
--header 'Authorization: Bearer YOUR_TOKEN'
```

### Retrieve a User's Wishlist

You can retrieve a user's wishlist using the following `cURL` command:

```sh
curl -X GET 'localhost:9000/store/customers/me/wishlists' \
--header 'x-publishable-api-key: YOUR_API_KEY' \
--header 'Authorization: Bearer YOUR_TOKEN'
```

### Share a Wishlist

You can share a user's wishlist using the following `cURL` command:

```sh
curl -X POST 'localhost:9000/store/customers/me/wishlists/share' \
--header 'x-publishable-api-key: YOUR_API_KEY' \
--header 'Authorization: Bearer YOUR_TOKEN'
```

## License

This project is licensed under the MIT License - see the LICENSE file for details.
