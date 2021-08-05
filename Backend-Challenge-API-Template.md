# BACKEND CHALLENGE TEMPLATE DOCUMENTATION

LOCAL BASE-URL:     <http://localhost:port>

REMOTE BASE-URL:      <https://remote-url>

## NOTE: It is important that you must create a docker file in the root of the solution for running the application. And also make sure your package-lock.json file is pushed with the code, i.e remove package-lock.json or yarn.lock file from gitignore

## 1. DEPARTMENTS

### 1.1. GET ALL DEPARTMENTS

**Description:** This endpoint retrieve the list of departments from the database and returns an array of department objects to the user .

**Path:** /departments

**Method:** GET

**Status:** 200

**Success response:**

```json
[
  {
    "department_id": integer,
    "name": string,
    "description" : string,
  },
  {
    "department_id": integer,
    "name": string,
    "description" : string,
  },
]
```

### 1.2 GET A SINGLE DEPARTMENT

**Description:** This endpoint get a single department using the department Id in the request params.

**Path:** /departments/{department_id}

**Method:** GET

**Success response:**

**Status:** 200

```json
{
"department_id": integer,
"name": string,
"description" : string,
}
```

## 2. CATEGORIES

### 2.1 GET ALL CATEGORIES

**Description:** This endpoint returns a list of product categories to the user.

**Path:** /categories

**Method:** GET

**Status:** 200

**Success response:**

```json
{
“rows”:  [
    {
      "category_id": integer,
      "name": string,
      "description" : string,
      "department_id": integer,
    },
    {
      "category_id": integer,
      "name": string,
      "description" : string,
      "department_id": integer,
    },
  ]
}
```

### 2.2 GET A SINGLE CATEGORY

**Description:** This endpoint returns a single category using the category id.

**Path:** /categories/{category_id}

**Method:** GET

**Success response:**

**Status:** 200

```json
{
"category_id": integer,
"name": string,
"description" : string,
"department_id" : integer,
}
```

### 2.3 GET PRODUCT CATEGORY

**Description:** This endpoint returns the category of a particular product.

**Path:** /categories/inProduct/{product_id}

**Method:** GET

**Status:** 200

**Success response:**

```json
{
  "category_id": integer,
  "department_id" : integer,
  "name": string (category name e.g French)
}
```

### 2.4 GET ALL CATEGORIES IN A DEPARTMENT

**Description:** This endpoint returns a list of categories in a department.

**Path:** /categories/inDepartment/{department_id}

**Method:** GET

**Status:** 200

**Success response:**

```json
{
  "rows":  [
    {
      "category_id": integer,
      "name": string,
      "description" : string,
      "department_id": integer,
    },
    {
      "category_id": integer,
      "name": string,
      "description" : string,
      "department_id": integer,
    },
  ]
}

## 3. ATTRIBUTES

### 3.1 GET ALL ATTRIBUTES

**Description:** This endpoint returns a list of attributes from the database.

**Path:** /attributes

**Method:** GET

**Status:** 200

**Success response:**

```json
[
  {
    "attribute_id": integer,
    "name": string,
  },
  {
    "attribute_id": integer,
    "name": string,
  },
]
```

### 3.2 GET SINGLE ATTRIBUTES

**Description:** This endpoint returns a single attribute using the attribute id.

**Path:** /attributes/{attribute_id}

**Method:** GET

**Status:** 200

**Success response:**

```json
{
  "attribute_id": integer,
  "name": string,
}
```

### 3.3 GET ALL ATTRIBUTE VALUES IN AN ATTRIBUTE

**Description:** This endpoint returns a list of  values for a single attribute using the attribute id.

**Path:** /attributes/values/{attribute_id}

**Method:** GET

**Status:** 200

**Success response:**

```json
[
  {
    "attribute_value_id": integer,
    "value": string,
  }, {
    "attribute_value_id": integer,
    "value": string,
  },
]
```

### 3.4 GET ALL ATTRIBUTES OF A PRODUCT

**Description:** This endpoint returns a list of attributes for a single product using the product id

**Path:** /attributes/inProduct/{product_id}

**Method:** GET

**Status:** 200

**Success response:**

```json
[
  {
    "attribute_name": string,
    "attribute_value_id": integer,
    "attribute_value": string,
  },
  {
    "attribute_name": string,
    "attribute_value_id": integer,
    "attribute_value": string,
  },
]
```

## 4. PRODUCTS

### 4.1 GET ALL PRODUCTS

**Description:** This endpoint returns a list of products in the database. It should return a paginated response.

**Path:** /products

**Method:** GET

**Status:** 200

```json
params:
{
  "page": integer,                                                  //The starting page, default: 1
  "limit": integer,                                                    //Limit per page, default: 20
  "description_length": integer                            //Limit of the description, default: 200
}
```

**Success response:**

```json
{
  "paginationMeta":   {
  "currentPage": integer,                // Current page number
  "currentPageSize": integer,        // The page limit
  "totalPages": integer,                 // The total number of pages for all products
  "totalRecords": integer,               // The total number of product in the database
},
"rows":  [
    {
      "product_id": integer,
      "name": string,
      "description": string,
      "price": string,
      "discounted_price": string,
      "thumbnail": string,
    },
    {
      "product_id": integer,
      "name": string,
      "description": string,
      "price": string,
      "discounted_price": string,
      "thumbnail": string,
    },
  ]
}
```

### 4.2 SEARCH PRODUCTS

**Description:** This endpoint returns a list of product that matches the search value.

**Path:** /products/search?query_string={search value}&all_words=on

**Method:** GET

**Status:** 200

```json
params: {
  "page": integer,                                                  //The starting page, default: 1
  "limit": integer,                                                    //Limit per page, default: 20
  "description_length": integer,                            //Limit of the description, default: 200
  "query_string": string,                                        //Item to be searched
  "all_words": string,                                             //on or off, different mode of searching
}
```

**Success response:**

```json
{
  "rows":  [
    {
      "product_id": integer,
      "name": string,
      "description": string,
      "price": string,
      "discounted_price": string,
      "thumbnail": string,
    },
    {
      "product_id": integer,
      "name": string,
      "description": string,
      "price": string,
      "discounted_price": string,
      "thumbnail": string,
    },
  ]
}
```

### 4.3 GET A SINGLE PRODUCT

**Description:** This endpoint returns a single product object using the product id.

**Path:** /products/{product_id}

**Method:** GET

**Status:** 200

```json
params: {
  "description_length": integer                            //Limit of the description, default: 200
}
```

**Success response:**

```json
{
  "product_id": integer,
  "name": string,
  "description": string,
  "price": string,
  "discounted_price": string,
  "image": string,
  "image_2": string,
  "thumbnail": string,
  "displayl": integer,
}
```

### 4.4 GET ALL PRODUCTS IN A CATEGORY

**Description:** This endpoint should return list of products in a category using the category id in the request params.

**Path:** /products/inCategory/{category_id}

**Method:** GET

**Status:** 200

```json
params: {
  "page": integer,                                                  //The starting page, default: 1
  "limit": integer,                                                    //Limit per page, default: 20
  "description_length": integer                            //Limit of the description, default: 200
}
```

**Success response:**

```json
{
  "rows":  [
    {
      "product_id": integer,
      "name": string,
      "description": string,
      "price": string,
      "discounted_price": string,
      "thumbnail": string,
    },
    {
      "product_id": integer,
      "name": string,
      "description": string,
      "price": string,
      "discounted_price": string,
      "thumbnail": string,
    },
  ]
}
```

### 4.5 GET ALL PRODUCTS IN A DEPARTMENT

**Description:** This endpoint returns list of products in a department using the department id in the request params.

**Path:** /products/inDepartment/{department_id}

**Method:** GET

**Status:** 200

```json
params: {
  "page": integer,                                                  //The starting page, default: 1
  "limit": integer,                                                    //Limit per page, default: 20
  "description_length": integer                            //Limit of the description, default: 200
}
```

**Success response:**

```json
{
  "rows": [
    {
      "product_id": integer,
      "name": string,
      "description": string,
      "price": string,
      "discounted_price": string,
      "thumbnail": string,
    },
    {
      "product_id": integer,
      "name": string,
      "description": string,
      "price": string,
      "discounted_price": string,
      "thumbnail": string,
    },
  ]
}
```

### 4.6 GET REVIEWS OF A PRODUCT

**Description:** This endpoint returns a list reviews for a product using the product id in the request params.

**Path:** /products/{product_id}/reviews

**Method:** GET

**Status:** 200

**Success response:**

```json
{
  [
    {
      "name": string,
      "review": string,
      "rating": integer,
      "created_on": string (datetime),
    },
    {
      "name": string,
      "review": string,
      "rating": integer,
      "created_on": string (datetime),
    },
  ]
}
```

### 4.7 POST A PRODUCT REVIEW

**Description:** This endpoint allows a user to post a product review.

**Path:** /products/{product_id}/reviews

**Method:** POST

**Status:** 201

**Request body:**

```json
{
  "product_id": integer,
  "review": string,
  "rating": integer,
}
```

**Success response:**

```json
{
  "name": string,
  "review": string,
  "rating": integer,
  "created_on": string (datetime),
}
```

## 5. CUSTOMERS

### 5.1 CREATE A NEW CUSTOMER

**Description:** This endpoints allow a user to create a new account.

**Path:** /customers

**Method:** POST

**Status:** 201

**Request body:**

```json
{
  "name": string,
  "email": string,
  "password": string,
}
```

**Success response:**

```json
{
  "customer": {
    "customer_id" : integer,
    "name" : string,
    "email" : string,
    "address_1" : null,
    "address_2" : null,
    "city" : null,
    "region" : null,
    "postal_code" : null,
    "shipping_region_id" : integer,
    "credit_card" : null,
    "day_phone" : null,
    "eve_phone" : null,
    "mob_phone" : null,
  },
  "accessToken": string,
  "expiresIn": string,
}
```

### 5.2 LOGIN A CUSTOMER

**Description:** This endpoint allows a user to login to their customer account.

**Path:** /customers/login

**Method:** POST

**Status:** 200

**Request body:**

```json
{
  "email": string,
  "password": string,
}
```

**Success response:**

```json
{
  "customer": {
    "customer_id" : integer,
    "name" : string,
    "email" : string,
    "address_1" : null,
    "address_2" : null,
    "city" : null,
    "region" : null,
    "postal_code" : null,
    "shipping_region_id" : integer,
    "credit_card" : null,
    "day_phone" : null,
    "eve_phone" : null,
    "mob_phone" : null,
  },
  "accessToken": string,
  "expiresIn": string,
}
```

### 5.3 FACEBOOK LOGIN

**Description:** This endpoint allows a user to login to the application using facebook.

**Path:** /customers/facebook

**Method:** POST

**Status:** 200

**Request body:**

```json
{
"access_token": string,
}
```

**Success response:**

```json
{
  "customer": {
    "customer_id" : integer,
    "name" : string,
    "email" : string,
    "address_1" : null,
    "address_2" : null,
    "city" : null,
    "region" : null,
    "postal_code" : null,
    "shipping_region_id" : integer,
    "credit_card" : null,
    "day_phone" : null,
    "eve_phone" : null,
    "mob_phone" : null,
  },
  "accessToken": string,
  "expiresIn": string,
}
```

### 5.4 GET A CUSTOMER BY ID

**Description:** This endpoint retrieves customer information using the customer id in the token provided in the header of the request.

**Path:** /customers

**Method:** GET

**Status:** 200

**Success response:**

```json
{
  "customer_id" : integer,
  "name" : string,
  "email" : string,
  "address_1" : string,
  "address_2" : string,
  "city" : string,
  "region" : string,
  "postal_code" : string,
  "shipping_region_id" : integer,
  "credit_card" : string,
  "day_phone" : string,
  "eve_phone" : string,
  "mob_phone" : string,
}
```

### 5.5 UPDATE CUSTOMER DETAILS

**Description:** This endpoint updates the customer details.

**Path:** /customer

**Method:** PUT

**Status:** 200

**Request object:**

```json
{
  "email" : string,
  "name" : string,
  "day_phone" : string,
  "eve_phone" : string,
  "mob_phone" : string,
}
```

**Success response:**

```json
{
  "customer_id" : integer,
  "name" : string,
  "email" : string,
  "address_1" : string,
  "address_2" : string,
  "city" : string,
  "region" : string,
  "postal_code" : string,
  "shipping_region_id" : integer,
  "credit_card" : string,
  "day_phone" : string,
  "eve_phone" : string,
  "mob_phone" : string,
}
```

### 5.6 UPDATE CUSTOMER ADDRESS

**Description:** This endpoint updates the customer address.

**Path:** /customer/address

**Method:** PUT

**Status:** 200

**Request object:**

```json
{
  "address_1" : string,
  "address_2" : string,
  "city" : string,
  "region" : string,
  "postal_code" : string,
  "shipping_region_id" : integer,
}
```

**Success response:**

```json
{
  "customer_id" : integer,
  "name" : string,
  "email" : string,
  "address_1" : string,
  "address_2" : string,
  "city" : string,
  "region" : string,
  "postal_code" : string,
  "shipping_region_id" : integer,
  "credit_card" : string,
  "day_phone" : string,
  "eve_phone" : string,
  "mob_phone" : string,
}
```

### 5.7 UPDATE CUSTOMER CREDIT CARD

**Description:** This endpoint updates the customer address.

**Path:** /customer/creditCard

**Method:** PUT

**Status:** 200

**Request object:**

```json
{
  "credit_card" : string,
}
```

**Success response:**

```json
{
  "customer_id" : integer,
  "name" : string,
  "email" : string,
  "address_1" : string,
  "address_2" : string,
  "city" : string,
  "region" : string,
  "postal_code" : string,
  "shipping_region_id" : integer,
  "credit_card" : string, (xxxxxxxxxxxx7890)
  "day_phone" : string,
  "eve_phone" : string,
  "mob_phone" : string,
}
```

## 6. ORDERS

### 6.1 CREATE AN ORDER

**Description:** This endpoint creates an order for a customer.

**Path:** /orders

**Method:** POST

**Status:** 201

**Request object:**

```json
{
  "cart_id" : string,
  "shipping_id" : integer,
  "tax_id" : integer,
}
```

**Success response:**

```json
{
  "order_id" : integer,
}
```

### 6.2 GET AN ORDER

**Description:** This endpoint returns a single order with list of order items.

**Path:** /orders/{order_id}

**Method:** GET

**Status:** 200

**Success response:**

```json
{
  "order_id" : integer,
  "order_items" : [
    {
      "product_id" : integer,
      "attributes" : string,
      "product_name" : string,
      "quantity" : integer,
      "unit_cost" : string,
      "subtotal" : string,
    },
    {
      "product_id" : integer,
      "attributes" : string,
      "product_name" : string,
      "quantity" : integer,
      "unit_cost" : string,
      "subtotal" : string,
    },
  ]
}
```

### 6.3 GET CUSTOMERS ORDER

**Description:** This endpoint returns a list of orders placed by a customer.

**Path:** /orders/inCustomer

**Method:** GET

**Status:** 200

**Success response:**

```json
[
  {
    "order_id" : integer,
    "total_amount" : string,
    "created_on" : datetime,
    "shipped_on" : datetime,   // datetime default null
    "name" : string,     // customer name
  },
  {
    "order_id" : integer,
    "total_amount" : string,
    "created_on" : datetime,
    "shipped_on" : datetime,   // datetime default null
    "name" : string,     // customer name
  },
]
```

### 6.4 GET ORDER SHORT DETAILS

**Description:** This endpoint returns a short details of an order using the order id in the request param.

**Path:** /orders/shortDetail/{order_id}

**Method:** GET

**Status:** 200

**Success response:**

```json
{
  "order_id" : integer,
  "total_amount" : string,
  "created_on" : string,
  "shipped_on" : string,
  "status" : string,
  "name" : string,
}
```

## 7. SHOPPING CART

### 7.1 GENERATE CART UNIQUE ID

**Description:** This endpoint is meant to generate a unique cart Id for adding product to a shopping cart.

**Path:** /shoppingcart/generateUniqueId

**Method:** GET

**Status:** 200

**Success response:**

```json
{
  "cart_id" : string,
}
```

### 7.2 ADD PRODUCT TO SHOPPING CART

**Description:** This endpoint add product to the shopping cart.

**Path:** /shoppingcart/add

**Method:** POST

**Status:** 201

**Request object:**

```json
{
  "cart_id" : string,
  "product_id" : integer,
  "attributes" : string,
  "quantity" : integer,
}
```

**Success response:**

```json
{
  "item_id" : integer,
  "cart_id" : integer,
  "attributes" : string,
  "product_id" : integer,
  "quantity" : integer,
}
```

### 7.3 GET LIST OF PRODUCTS IN A SHOPPING CART

**Description:** This endpoint returns a list of items in the shopping cart using the cart id in the request params.

**Path:** /shoppingcart/{cart_id}

**Method:** GET

**Status:** 200

**Success response:**

```json
[
  {
    "item_id" : integer,
    "cart_id" : integer,
    "name" : string,
    "attributes" : string,
    "product_id" : integer,
    "image" : string,
    "price" : string,
    "discounted_price" : string,
    "quantity" : integer,
    "subtotal" : string,
  },
  {
    "item_id" : integer,
    "cart_id" : integer,
    "name" : string,
    "attributes" : string,
    "product_id" : integer,
    "image" : string,
    "price" : string,
    "discounted_price" : string,
    "quantity" : integer,
    "subtotal" : string,
  }
]
```

### 7.4 UPDATE CART ITEM QUANTITY

**Description:** This endpoint updates the quantity of an item in the shopping cart using the item id in the request param

**Path:** /shoppingcart/update/{item_id}

**Method:** PUT

**Status:** 200

**Request object:**

```json
{
  "quantity" : integer,
}
```

**Success response:**

```json
{
  "item_id" : integer,
  "cart_id" : integer,
  "attributes" : string,
  "product_id" : integer,
  "quantity" : integer,
}
```

### 7.5 EMPTY SHOPPING CART

**Description:** This endpoint deletes all items in the shopping cart and returns an empty array.

**Path:** /shoppingcart/empty/{cart_id}

**Method:** DELETE

**Status:** 200

**Success response:**

```json
{}
```

### 7.6 REMOVE ITEM FROM SHOPPING CART

**Description:** This endpoint remove a single item from the shopping cart using the item id in the request params.

**Path:** /shoppingcart/removeProduct/{item_id}

**Method:** DELETE

**Status:** 200

**Success response:**

```json
{
  "message" : string,
}
```

## 8. TAX

### 8.1 GET ALL TAXES

**Description:** This endpoint returns a list of taxes in the database.

**Path:** /tax

**Method:** GET

**Status:** 200

**Success response:**

```json
[
  {
    "tax_id" : integer,
    "tax_type" : string,
    "tax_percentage" : string,
  },
  {
    "tax_id" : integer,
    "tax_type" : string,
    "tax_percentage" : string,
  }
]
```

### 8.1 GET A SINGLE TAX

**Description:** This endpoint returns a single tax using the tax id in the request param.

**Path:** /tax/{tax_id}

**Method:** GET

**Status:** 200

**Success response:**

```json
{
  "tax_id" : integer,
  "tax_type" : string,
  "tax_percentage" : string,
}
```

## 9. SHIPPING

### 9.1 GET ALL SHIPPING REGIONS

**Description:** This endpoint returns a list of shipping regions in the database

**Path:** /shipping/regions

**Method:** GET

**Status:** 200

**Success response:**

```json
[
  {
    "shipping_region_id" : integer,
    "shipping_region" : string,
  },
  {
    "shipping_region_id" : integer,
    "shipping_region" : string,
  }
]
```

### 9.2 GET ALL SHIPPINGS IN A REGION

**Description:** This endpoint returns the list of shipping in a selected region using the shipping region id in the request param.

**Path:** /shipping/regions/{shipping_region_id}

**Method:** GET

**Status:** 200

**Success response:**

```json
[
  {
    "shipping_id" : integer,
    "shipping_type" : string,
    "shipping_cost" : string,
    "shipping_region_id" : string,
  },
  {
    "shipping_id" : integer,
    "shipping_type" : string,
    "shipping_cost" : string,
    "shipping_region_id" : string,
  }
]
```

## 10. STRIPE

### 10.1 POST PAYMENT TO STRIPE

**Description:** This endpoint post payment to stripe.

**Path:** /stripe/charge

**Method:** POST

**Status:** 200

**Request object:**

```json
{
  "stripeToken" : string,
  "email" : string,
  "order_id" : integer,
}
```

**Stripe Payment object:**

```json
{
  "stripeToken" : string,
  "order_id" : integer,
  "description" : string,
  "amount" : integer,
  "currency" : string,
}
```

**Success response:**

```json
{
  Object returned from stripe,
  "message" : string,
}
```

## 10. REQUEST HEADER TOKEN FORMAT

**Description:** The recommended Authorization header format.  
Only handle this header for the APIs that relate to customer  
or cart (which only apply for the API groups: customer, order, shopping cart, and Stripe).

```json
USER-KEY:  “Bearer ey6ujkf88hjhf87bhr787y.hlo98ruiure8o9ujlorjljkrg.ihhurwhiu98jhge”
```
