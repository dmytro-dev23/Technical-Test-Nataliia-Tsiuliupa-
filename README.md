# Technical Test (Nataliia Tsiuliupa)

## **I. Create the basic structure of a web shop.**

### Backend Structure (Model and Controller):

1. **MVC Architecture**:
   - The back end is built with MVC (Model-View-Controller) pattern and it consists of three components 
      - Model is the data and business logic, 
      - View is the presentation layer and it will be implemented by the front end,
      - Controller model handles the incoming requests and updates the model accordingly. 
   - Nest. js in this case is adopted since MVC is one of its supported features otherwise, MVC makes it ideal candidate to build complicated APIs as well as implementing business logic.

2. **Separation of Concerns**:
   - Model, controller, and service are grouped inside modules, their particular folder is named as `src/modules`, thus this "principle of separation of concerns" is maintained. 
   - Models are the entities that the data relates to, controllers determine the flow of requests-responses, and services are responsible for the business logic.

3. **RESTful API**:
   - Controllers have embedded RESTful data keepers for data manipulation that follow REST practices concerning CRUD(create, read, update and delete) operations. 
   - It guarantees that the interface between servers and clients is smooth and scalable, thereby respecting Huber's interoperability and client-server communication principles.

### Frontend Structure (View):

1. **Next.js for View Layer**:
   - Emphatically, participants in future conferences could also be provided guides that offer ideas on environmental sustainability. js is mainly utilized to get the user interface that is for developing dynamic and server-side Rendering applications such as React components which is concerned with the MVC but View architecture.
   - It does server-side rendering, code splitting, and client-side routing, harping on others function which results in better user experience and developer effectiveness.

2. **Component-Based Architecture**:
   - Component classes are separated within the `src/components` folder, which is a core feature of component-based software architecture that, in turn, gives code reusability and modularity.
   - Each one of the code sections corresponds to a particular element of the UI or some internal functionality and gives overall coherence and structure to the code.

3. **Communication via REST API**:
   - Highlighting the cultural significance of this artwork is essential to commemorating our nation’s history while also promoting cultural appreciation.
   - The procedure of the communication between the frontend and the backend of the Nest is carried out through the RESTful API endpoints, which are opened via the Nest.js controllers.
   - Next.js runs HTTP requests to the backend API endpoints to obtain data, make form submissions, and perform CRUD [create / read/ update/ remove] operations on resources, fostering communication between the View and the Model-Controller layers.

By using the MVC pattern with Next.js for the View layer and Nest.js for the Model and Controller layers, with setup communication via REST, the application architecture ensures a clear separation of concerns, promotes code maintainability, and facilitates efficient client-server communication.

### Core modules

- Product
- Category
- Customer
- Customer Address: This is where customer addresses (name, lastname, street, city, postcode, region, country, telephone) are stored and managed.
- Cart: Information about products and the customer (their data, address) is stored here until an order is created.
- Order
- Invoice: Document for payment, depends on the order.
- Shipment: Document for shipping, depends on the order.
- Credit Memo: Document for returns, depends on the order and invoice.
- Offline Payments: Payment upon receipt, pickup.
- Online Payments: Online payment.
- Shipment: Different shipping methods implementations are managed here. As Yuri mentioned, an abstract shipping class is needed. It contains an abstract method - collectShippingRates. Each specific method implements collectShippingRates - calling a specific API such as UPS, DHL, etc.
- Admin: Backend implementation for accessing the admin panel. The admin panel can also be built on the same frontend framework, using REST API endpoints, but there should be user-password restrictions.

### Structure

- **Backend:**

    ```
    |   ...some-project-configs
    |   .env
    |   package.json
    |   
    \---src
        |   main.ts
        |   
        +---config
        +---constants
        |       error-messages.ts
        |       
        +---modules
        |   +---categories
        |   |   |   categoriess.module.ts
        |   |   |   
        |   |   +---controllers
        |   |   |       categories.controller.ts
        |   |   |       some-additional-related.controller.ts
        |   |   |       
        |   |   +---dto
        |   |   |       create-categories.dto.ts
        |   |   |       
        |   |   +---entities
        |   |   |       categories.entity.ts
        |   |   |       some-additional-related.entity.ts
        |   |   |       
        |   |   +---interfaces
        |   |   |       categories.interface.ts
        |   |   |       
        |   |   +---repositories
        |   |   |       categories.repository.ts
        |   |   |       some-additional-related.repository.ts
        |   |   |       
        |   |   \---services
        |   |           categories.service.ts
        |   |           some-additional-related.service.ts
        |   |           
        |   +---customers
        |   |   |   customers.module.ts
        |   |   |   
        |   |   +---controllers
        |   |   |       customer.controller.ts
        |   |   |       some-additional-related.controller.ts
        |   |   |       
        |   |   +---dto
        |   |   |       create-customer.dto.ts
        |   |   |       
        |   |   +---entities
        |   |   |       customer.entity.ts
        |   |   |       some-additional-related.entity.ts
        |   |   |       
        |   |   +---interfaces
        |   |   |       customer.interface.ts
        |   |   |       
        |   |   +---repositories
        |   |   |       customer.repository.ts
        |   |   |       some-additional-related.repository.ts
        |   |   |       
        |   |   \---services
        |   |           customer.service.ts
        |   |           some-additional-related.service.ts
        |   |           
        |   +---orders
        |   |   |   orders.module.ts
        |   |   |   
        |   |   +---controllers
        |   |   |       order.controller.ts
        |   |   |       some-additional-related.controller.ts
        |   |   |       
        |   |   +---dto
        |   |   |       create-order.dto.ts
        |   |   |       
        |   |   +---entities
        |   |   |       order.entity.ts
        |   |   |       some-additional-related.entity.ts
        |   |   |       
        |   |   +---interfaces
        |   |   |       order.interface.ts
        |   |   |       
        |   |   +---repositories
        |   |   |       order.repository.ts
        |   |   |       some-additional-related.repository.ts
        |   |   |       
        |   |   \---services
        |   |           order.service.ts
        |   |           some-additional-related.service.ts
        |   |           
        |   +---payments
        |   |   |   payments.module.ts
        |   |   |   
        |   |   +---controllers
        |   |   |       payment.controller.ts
        |   |   |       some-additional-related.controller.ts
        |   |   |       
        |   |   +---dto
        |   |   |       create-payment.dto.ts
        |   |   |       
        |   |   +---entities
        |   |   |       payment.entity.ts
        |   |   |       some-additional-related.entity.ts
        |   |   |       
        |   |   +---interfaces
        |   |   |       payment.interface.ts
        |   |   |       
        |   |   +---repositories
        |   |   |       payment.repository.ts
        |   |   |       some-additional-related.repository.ts
        |   |   |       
        |   |   \---services
        |   |           payment.service.ts
        |   |           some-additional-related.service.ts
        |   |           
        |   +---products
        |   |   |   products.module.ts
        |   |   |   
        |   |   +---controllers
        |   |   |       product.controller.ts
        |   |   |       some-additional-related.controller.ts
        |   |   |       
        |   |   +---dto
        |   |   |       create-product.dto.ts
        |   |   |       
        |   |   +---entities
        |   |   |       product.entity.ts
        |   |   |       some-additional-related.entity.ts
        |   |   |       
        |   |   +---interfaces
        |   |   |       product.interface.ts
        |   |   |       
        |   |   +---repositories
        |   |   |       product.repository.ts
        |   |   |       some-additional-related.repository.ts
        |   |   |       
        |   |   \---services
        |   |           product.service.ts
        |   |           some-additional-related.service.ts
        |   |           
        |   \---shipping
        |       |   shipping.module.ts
        |       |   
        |       +---controllers
        |       |       shipping.controller.ts
        |       |       some-additional-related.controller.ts
        |       |       
        |       +---dto
        |       |       create-shipping.dto.ts
        |       |       
        |       +---entities
        |       |       shipping.entity.ts
        |       |       some-additional-related.entity.ts
        |       |       
        |       +---interfaces
        |       |       shipping.interface.ts
        |       |       
        |       +---repositories
        |       |       shipping.repository.ts
        |       |       some-additional-related.repository.ts
        |       |       
        |       \---services
        |               shipping.service.ts
        |               some-additional-related.service.ts
        |               
        \---utils
            +---functions
            |      some-function.ts
            |
            +---interfaces
            |       shipping.interface.ts
            |       
            +---middlewares
            |       http-request-logger.middleware.ts
            |       
            +---modules
            |   \---stripe
            |           stripe.module.ts
            |           stripe.service.ts
            |           
            +---services
            |       error-handler.service.ts
            |       logger.service.ts
            |       
            \---types
    ```
  
1. **Modular Organization**: 
   - Each of the modules (**`categories`**, **`customers`**, **`orders`** etc. ) is put in its own directory specified under **`src/modules`** and, as a result, the architecture is modular and scalable. 
   - Through this modular approach, the code for each entity is placed in one group, which allows it to be separated and contained, thus making this task easier and simpler. 
   - Allows versatility and to imed the modules as independent services. 
2. **Consistent Structure**: 
   - The structure of modules entails the presence of subdirectories that are common in every module directory. These are the **`controllers`**, **`dto`**, **`entities`**, **`interfaces`**, **`repositories`**, and **`services`** directories. 
   - This makes it possible that the essential logic is organized in a consistent form and also provides a clear hierarchy of responsibilities enabling smooth code navigation. 
   - This type of structure allows us to have more than one **`controllers`**, **`dto`**, **`entities`**, **`interfaces`**, **`repositories`**, and **`services`** in module. In this case we can reduce amount of global modules by having related entries in one place.
3. **Separation of Concerns**: 
   - Controllers are responsible for handling HTTP requests, services produce the business logic , DTOs are data transfer objects used for transferring data, entities are design to represent database models, repositories interact with database, interfaces define types. 
   - These insurances the loose coupling of each application module allows for specific responsibility, and improving the maintainability and the testability level. 
4. **Utilities and Middleware**:
   - **`functions`**, **`interfaces`**, **`middleware`** and **`modules`** are located in the **`utils`** directory and used accordingly. 
   - Centralization facilitates uniformity in the executions and increases the participation level and simultaneously maintains the clean segregation of concerns.

------

- **Frontend:**

    ```
    |   ...some-project-configs
    |   package.json
    |   
    +---public
    |       next.svg
    |       vercel.svg
    |       
    \---src
        +---api
        |       API.ts
        |       index.ts
        |       interceptors.ts
        |       
        +---app
        |   |   favicon.ico
        |   |   globals.css
        |   |   
        |   +---layout
        |   |       index.tsx
        |   |       
        |   +---not-found
        |   |       index.tsx
        |   |       
        |   \---root
        |           index.tsx
        |           
        +---components
        |   +---Some-Component-A
        |   |   |   index.tsx
        |   |   |   
        |   |   \---components
        |   |       +---Some-Component-A
        |   |       |   |   index.tsx
        |   |       |   |   
        |   |       |   \---components
        |   |       \---Some-Component-B
        |   |           |   index.tsx
        |   |           |   
        |   |           \---components
        |   \---Some-Component-B
        |       |   index.tsx
        |       |   
        |       \---components
        |           +---Some-Component-A
        |           |   |   index.tsx
        |           |   |   
        |           |   \---components
        |           \---Some-Component-B
        |               |   index.tsx
        |               |   
        |               \---components
        +---pages
        |   \---products
        |       |   index.module.scss
        |       |   index.tsx
        |       |   
        |       \---components
        |           +---Some-Component-A
        |           |   |   index.tsx
        |           |   |   
        |           |   \---components
        |           |       +---Some-Component-A
        |           |       |   |   index.tsx
        |           |       |   |   
        |           |       |   \---components
        |           |       \---Some-Component-B
        |           |           |   index.tsx
        |           |           |   
        |           |           \---components
        |           \---Some-Component-B
        |               |   index.tsx
        |               |   
        |               \---components
        |                   +---Some-Component-A
        |                   |   |   index.tsx
        |                   |   |   
        |                   |   \---components
        |                   \---Some-Component-B
        |                       |   index.tsx
        |                       |   
        |                       \---components
        \---utils
    ```

1. **Component-Based Architecture**: 
   - Components are segregated inside the **`src/components`** folder with a component-based architecture being followed. 
   - Such approach encourages code reusability and modularity that let programmers assemble intricate UIs from the smaller units of the reusable components. 
2. **Page Structure**: 
   - Next. js files are located in the **`src/pages`** directory and each of them represents a path in the app. 
   - This topsy-turvy structure reflecting Next. npm install routing library, allowing for creation and maintenance of page routes without coding.
3. **Component-specific Styles**: 
   - Component-specific stylesheets are placed at the same level as components, which made possible encapsulation and ensured that styles would be applied only to those components.

------


## II. Create a basic implementation that would be needed to handle multiple payment processing providers

```ts
import Stripe from 'stripe';
import * as braintree from 'braintree';
import * as paypal from '@paypal/checkout-server-sdk';

const config = {
   stripe: {
      apiKey: 'your_stripe_api_key'
   },
   braintree: {
      merchantId: 'your_braintree_merchant_id',
      publicKey: 'your_braintree_public_key',
      privateKey: 'your_braintree_private_key'
   },
   paypal: {
      clientId: 'your_paypal_client_id',
      secret: 'your_paypal_secret'
   }
};

export enum PaymentTypes {
   STRIPE = "stripe",
   BRAINTREE = "braintree",
   PAYPAL = "paypal",
}

interface Transaction {
   id: string;
   amount: number;
   currency: string;
   status: string;
}

type ChargeResult = {
   success: boolean;
   transaction?: Transaction;
   error?: Error;
};

export interface PaymentMethodAdapterInterface {
   charge(amount: number, currency: string, cardDetails: { token?: string; nonce?: string }): Promise<ChargeResult>;
}

export class StripeAdapter implements PaymentMethodAdapterInterface {
   private stripe: Stripe;

   constructor(private apiKey: string) {
      this.stripe = new Stripe(this.apiKey);
   }

   async charge(amount: number, currency: string, cardDetails: { token?: string }) {
      try {
         const charge = await this.stripe.charges.create({
            amount,
            currency,
            source: cardDetails.token
         });
         return {
            success: true,
            transaction: {
               id: charge.id,
               amount: charge.amount,
               currency: charge.currency,
               status: charge.status
            }
         };
      } catch (error) {
         return {success: false, error};
      }
   }
}

export class BraintreeAdapter implements PaymentMethodAdapterInterface {
   private gateway: braintree.BraintreeGateway;

   constructor(private merchantId: string, private publicKey: string, private privateKey: string) {
      this.gateway = new braintree.BraintreeGateway({
         environment: braintree.Environment.Sandbox,
         merchantId: this.merchantId,
         publicKey: this.publicKey,
         privateKey: this.privateKey
      });
   }

   async charge(amount: number, currency: string, cardDetails: { nonce?: string }) {
      try {
         const result = await this.gateway.transaction.sale({
            amount: parseFloat((amount / 100).toFixed(2)),
            paymentMethodNonce: cardDetails.nonce,
            options: {
               submitForSettlement: true
            }
         });

         if (result.success) {
            return {
               success: true,
               transaction: {
                  id: result.transaction.id,
                  amount: result.transaction.amount,
                  currency: result.transaction.currencyIsoCode,
                  status: result.transaction.status
               }
            };
         } else {
            return {success: false, error: new Error('Braintree charge failed: ' + result.message)};
         }
      } catch (error) {
         return {success: false, error};
      }
   }
}

export class PayPalAdapter implements PaymentMethodAdapterInterface {
   private client: paypal.PayPalHttpClient;

   constructor(private clientId: string, private secret: string) {
      const environment = new paypal.core.SandboxEnvironment(this.clientId, this.secret);
      this.client = new paypal.PayPalHttpClient(environment);
   }

   async charge(amount: number, currency: string, _cardDetails: { nonce?: string }) {
      try {
         const request = new paypal.orders.OrdersCreateRequest();
         request.prefer("return=representation");
         request.requestBody({
            intent: "CAPTURE",
            purchase_units: [{
               amount: {
                  currency_code: currency,
                  value: parseFloat((amount / 100).toFixed(2))
               }
            }]
         });
         const response = await this.client.execute(request);

         if (response.statusCode === 201) {
            return {
               success: true,
               transaction: {
                  id: response.result.id,
                  amount: response.result.purchase_units[0].amount.value,
                  currency: response.result.purchase_units[0].amount.currency_code,
                  status: response.result.status
               }
            };
         } else {
            return {success: false, error: new Error('PayPal charge failed')};
         }
      } catch (error) {
         return {success: false, error};
      }
   }
}

export class PaymentsFactory {
   create(provider: PaymentTypes) {
      switch (provider) {
         case PaymentTypes.STRIPE:
            return new StripeAdapter(config.stripe.apiKey);
         case PaymentTypes.PAYPAL:
            return new PayPalAdapter(config.paypal.clientId, config.paypal.secret);
         case PaymentTypes.BRAINTREE:
            return new BraintreeAdapter(config.braintree.merchantId, config.braintree.publicKey, config.braintree.privateKey);
         default:
            throw new Error('Invalid payment provider');
      }
   }
}
```
