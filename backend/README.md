# Back-end Model (MongoDB)

Link : http://localhost:5001/graphql

## List
* [Model](#Model)
    * [User Model](#User-Model)
    * [Product Model](#Product-Model)
    * [Promotion Model](#Promotion-Model)
    * [Customer Model](#Customer-Model)
    * [Category Model](#Category-Model)

* [Mutation](#Mutation)
  * [User Mutation](#User-Mutation)
    * [createUser](#createUser)
    * [updateUserById](#updateUserById)
    * [removeUserById](#removeUserById)
    * [login](#login)
  * [Product Mutation](#Product-Mutation)
    * [createProduct](#createProduct)
    * [updateProductById](#updateProductById)
    * [removeProductById](#removeProductById)
  * [Promotion Mutation](#Promotion-Mutation)
    * [createPromotion](#createPromotion)
    * [updatePromotionById](#updatePromotionById)
    * [removePromotionById](#removePromotionById)
  * [Customer Mutation](#Customer-Mutation)
     * [createCustomer](#createCustomer)
     * [updateCustomerById](#updateCustomerById)
     * [removeCustomerById](#removeCustomerById)
  * [Category Mutation](#Category-Mutation)
    * [createCategory](#createCategory)
    * [updateCategoryById](#updateCategoryById)
    * [removeCategoryById](#removeCategoryById)
* [Query](#Query)
    * [UserQuery](#UserQuery)
    * [ProductQuery](#ProductQuery)
    * [PromotionQuery](#PromotionQuery)
    * [CustomerQuery](#CustomerQuery)
    * [CategoryQuery](#CategoryQuery)

## Model

### User Model

|    Name     |          Type          |
| :---------: | :--------------------: |
|    type     | ENUM (CUSTOMER, ADMIN) |
|    name     |         String         |
|  username   |     String, unique     |
|  password   |         String         |
| dateOfBirth |          Date          |

#### Product Model

|    Name     |            Type            |
| :---------: | :------------------------: |
|    name     |           String           |
|    slug     |       String, unique       |
| description |           String           |
|  quantity   | String \*Change to Integer |
|    price    |  String \*Change to Float  |
|  imageUrl   |           String           |
|    tags     |           Array            |
|  timestamp  |            Date            |

#### Promotion Model

|    Name     |           Type           |
| :---------: | :----------------------: |
|    name     |          String          |
| description |          String          |
|   active    |         Boolean          |
|    code     |      String, unique      |
|   endDate   |           Date           |
|  discount   | String \*Change to Float |
|   minimum   | String \*Change to Float |
|  timestamp  |           Date           |

#### Customer Model

|    Name     |          Type          |
| :---------: | :--------------------: |
| nameAddress | ENUM (CUSTOMER, ADMIN) |
|   address   |         String         |
|    email    |     String, unique     |
|     tel     |         String         |
|  authorId   |      <b>User</b>       |

#### Category Model
|    Name     |          Type          |
| :---------: | :--------------------: |
| name | ENUM String |
|   slug   |         String, unique         |

<!-- #### Cart (?????????????????????????????????)

|   Name    |  Type  |
| :-------: | :----: |
|  cartNo   | String |
| timestamp |  Date  |

#### CartItem (??????????????????????????????????????????)

|   Name    |            Type            |
| :-------: | :------------------------: |
|  cartId   |        <b>Cart</b>         |
| productId |       <b>Product</b>       |
| quantity  | String \*Change to Integer |

#### Payment

|   Name    |                        Type                         |
| :-------: | :-------------------------------------------------: |
|   type    | ENUM (COD, TRANSFER) \*????????????????????????????????????????????? ???????????? ????????????????????? |
| productId |                   <b>Product</b>                    |
| quantity  |             String \*Change to Integer              | -->

<hr>

## Mutation

### User Mutation

##### createUser

```
mutation{
  createUser(record:{
    type:CUSTOMER
    name:"Fourthza"
    username:"fourthza1"
    password:"1234"
    dateOfBirth:"2020-06-26"
  }) {
    recordId
  }
}
```

#### updateUserById

```
mutation{
  updateUserById(_id:"6072a13eb8c74417c0d60dac", record:{
    name:"Fourth"
  }){
    recordId
  }
}
```

#### removeUserById

```
mutation{
  removeUserById(_id:"6072a13eb8c74417c0d60dac"){
    recordId
  }
}
```

##### login

```
mutation{
  login(username:"Fourthza" password:"1234"){
    token
    user{
      _id
      name
    }
  }
}
```

### Product Mutation

#### createProduct

```
mutation{
  createProduct(record:{
    name:"555555"
    slug:"bed123"
    description:"1234"
    price:"1234"
    imageUrl:"www.1234.com"
    quantity:"10"
    tags:["mirror","best price"]
    categoryId:"6077f320d54feb383a9abf59"
  }) {
    recordId
  }
}
```

#### updateProductById

```
mutation{
  updateProductById(_id:"6072a141b8c74417c0d60dad", record:{
    name:"product update"
  }){
    recordId
  }
}
```

#### removeProductById

```
mutation{
  removeProductById(_id:"6072a141b8c74417c0d60dad"){
    recordId
  }
}
```

### Promotion Mutation

#### createPromotion

```
mutation{
  createPromotion(record:{
    type:FREESHIPPING
    name:"1234"
    description:"1234"
    amount:"10"
    active:true
    code:"12345"
    endDate:"2021-04-07"
    discount:"20"
    minimumPrice:"20"
    categoryId:"6077f320d54feb383a9abf59"
    
  }) {
    recordId
  }
}
```

#### updatePromotionById

```
mutation{
  updatePromotionById(_id:"6072a143b8c74417c0d60dae", record:{
    name:"promotion best seller"
  }){
    recordId
  }
}
```

#### removePromotionById

```
mutation{
  removePromotionById(_id:"6072a143b8c74417c0d60dae"){
    recordId
  }
}
```

### Customer Mutation

#### createCustomer

```
mutation{
  createCustomer(record:{
    nameAddress:"address"
    address:"address"
    email:"email@h.com"
    tel:"0123456789"
    authorId:"606d5676e3f7c30f44cb6289"
  }) {
    recordId
  }
}
```

#### updateCustomerById

```
mutation{
  updateCustomerById(_id:"6072a15cb8c74417c0d60daf", record:{
    tel:"test hello"
  }){
    recordId
  }
}
```

#### removeCustomerById

```
mutation{
  removeCustomerById(_id:"6072a15cb8c74417c0d60daf"){
    recordId
  }
}
```

### Category Mutation

#### createCategory

```
mutation{
  createCategory(record:{
    name:"Bedroom"
    slug:"bedroom"
  }) {
    recordId
  }
}
```

#### updateCategoryById

```
mutation{
  updateCategoryById(_id:"6077f1f1d54feb383a9abf58", record:{
    name:"bedroom"
  }){
    recordId
  }
}
```

#### removeCategoryById

```
mutation{
  removeCategoryById(_id:"6077f1f1d54feb383a9abf58"){
    recordId
  }
}
```

<hr>

## Query

#### UserQuery

```
query{
  user{
    _id
    name
    username
    type
  }
}
```

##### HTTP HEADERS\*

```
{
  "Authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MDZkNTY3NmUzZjdjMzBmNDRjYjYyODkiLCJpYXQiOjE2MTgxMTQ2MzMsImV4cCI6MTYxODIwMTAzM30.ma2Mklxz78njpgfO3zRnWcKvMUorXPjfTtHV6n8he00"
}
```

#### ProductQuery

```
query{
  products{
    name
    slug
    description
    price
    imageUrl
    quantity
    tags
    timestamp
    category{
      name
      slug
    }
  }
}

```

#### PromotionQuery

```
query{
  promotions{
    type
    name
    description
    amount
    active
    code
    endDate
    discount
    minimumPrice
    timestamp
    category{
      name
    }
    product{
      name
    }
  }
}
```

#### CustomerQuery

```
query{
  customers{
    author{
      name
      username
      dateOfBirth
    }
    nameAddress
    address
    email
    tel
  }
}
```

#### CategoryQuery
```
query{
  category{
    name
    slug
  }
}
```
