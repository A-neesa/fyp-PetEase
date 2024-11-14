# PetEase

## About The Project
PetEase is a mobile app designed to make caring for pets simpler and more convenient for pet owners. It provides easy access to a variety of high-quality pet products, from food to grooming supplies, along with personalized recommendations tailored to each pet’s needs.

## Business Rules

### 1. Admin

**Attributes**:  
- **Name**: The admin's name.  
- **Email**: Unique email address for account identification and login.  
- **Phone Number**: Unique phone number for contact and verification.  
- **Password**: Secure password for account login.  

**Relationships**:  
- An **Admin** manages multiple **Products**, **Orders**.  
- An **Admin** can add, edit, or remove **Products** from the catalog and manage stock availability.  
  
**Uniqueness**:  
- Each admin must have a unique **email** and **phoneNo**.  

**Mandatory Fields**:  
- **fullname**, **email**, **phoneNo**, **password**.

---

### 2. Users

**Attributes**:  
- **Full Name**: The user’s full name.  
- **Email**: Unique email address for account identification and login.  
- **Password**: Secure password for account login.  
- **Phone Number**: Unique phone number for contact and verification.  

**Relationships**:  
- A **User** can add multiple **Products** to their **Cart** and place **Orders**.  
- A **User** can leave **Reviews** for products they have purchased.  
- A **User** can receive **Notifications** regarding deals, order updates, and promotions.  

**Uniqueness**:  
- Each **User** must have a unique **email** and **phone number**.  

**Mandatory Fields**:  
- **fullName**, **email**, **password**, **phoneNo**.

**Optional Fields**:  
- **profileImage**.

---

### 3. Product

**Attributes**:  
- **Name**: The name of the product.  
- **Brand**: The brand of the product.  
- **Category**: The category of the product.  
- **Price**: The price of the product.  
- **Stock Quantity**: The available stock for the product.  
- **Image**: A picture of the product.  
- **Description**: A detailed description of the product.  

**Relationships**:  
- A **Product** can be added to multiple **Carts** and **Orders**.  
- A **Product** can receive multiple **Reviews** from **Users**.  
- A **Product** belongs to one **Category**.  

**Uniqueness**:  
- Each **Product** must have a unique **name** and **id**.  

**Mandatory Fields**:  
- **name**, **brand**, **category_id**, **price**, **stock**, **image**.

**Optional Fields**:  
- **description**.

---

### 4. Cart

**Attributes**:  
- **user_id**: The ID of the user associated with the cart.  
- **product_id**: The ID of the product in the cart.  
- **quantity**: The quantity of the product in the cart.  
- **total_price**: The total price of products in the cart.  

**Relationships**:  
- A **Cart** is associated with a single **User** and can contain multiple **Products**.  
- A **Cart** is created for the purpose of placing an **Order** once the user checks out.  

**Uniqueness**:  
- Each **Cart** is unique to a **user_id**.  

**Mandatory Fields**:  
- **user_id**, **product_id**, **quantity**, **total_price**.

---

### 5. Orders

**Attributes**:  
- **order_id**: Unique identifier for the order.  
- **user_id**: The ID of the user who placed the order.  
- **order_date**: The date the order was placed.  
- **status**: The current status of the order (Pending, Processing, Shipped, Delivered, Cancelled).  
- **total_amount**: The total cost of the order.  

**Relationships**:  
- An **Order** is placed by a **User** after checking out their **Cart**.  
- An **Order** contains multiple **Order_Items** that track the products purchased.  
- An **Order** is linked to one **Payment** transaction for processing the payment.  

**Uniqueness**:  
- Each **Order** must have a unique **order_id**.  

**Mandatory Fields**:  
- **user_id**, **order_date**, **status**, **total_amount**.

---

### 6. Order_Items

**Attributes**:  
- **order_id**: The ID of the associated order.  
- **product_id**: The ID of the product in the order.  
- **quantity**: The quantity of the product in the order.  
- **price**: The price of the product at the time of order.  

**Relationships**:  
- Each **Order_Item** is associated with one **Order** and one **Product**.  
- An **Order_Item** contributes to the total cost of the **Order**.  

**Uniqueness**:  
- Each **Order_Item** must be unique to a combination of **order_id** and **product_id**.  

**Mandatory Fields**:  
- **order_id**, **product_id**, **quantity**, **price**.

---

### 7. Review

**Attributes**:  
- **user_id**: The ID of the user submitting the review.  
- **rating**: The rating provided by the user.  
- **comment**: The review comment written by the user.  
- **product_id**: The ID of the product being reviewed.  

**Relationships**:  
- A **Review** is associated with one **Product** and one **User**.  
- A **Review** can only be submitted for a **Product** after it has been purchased by the **User**.  

**Uniqueness**:  
- Each **Review** must be unique to a combination of **user_id** and **product_id**.  

**Mandatory Fields**:  
- **customer_id**, **rating**, **comment**, **product_id**.

---

### 8. Payment

**Attributes**:  
- **user_id**: The ID of the user making the payment.  
- **order_id**: The ID of the order being paid for.  
- **payment_method**: The method of payment (e.g., credit/debit card, e-wallet, bank transfer).  
- **status**: The payment status (Paid, Pending, Failed).  

**Relationships**:  
- A **Payment** is linked to a single **Order**.  
- A **Payment** is processed once the **Order** is confirmed.  

**Uniqueness**:  
- Each **Payment** must be linked to a unique **order_id**.  

**Mandatory Fields**:  
- **user_id**, **order_id**, **payment_method**, **status**.

---

### 9. Categories

**Attributes**:  
- **categoryName**: The name of the category.  
  

**Relationships**:  
- A **Category** can have multiple **Products** assigned to it.  
- **Products** can be filtered based on their **Category** for easier browsing.  

**Uniqueness**:  
- Each **Category** must have a unique **categoryName**.  

**Mandatory Fields**:  
- **categoryName**.

**Optional Fields**:  
.

---

### 10. Notifications

**Purpose**:  
Manages in-app notifications for deals, restocks, order status updates, and reminders.

**Attributes**:  
- **notification_id**: Unique identifier for the notification.  
- **user_id**: The ID of the user receiving the notification.   
- **type**: The type of notification (e.g., order update, promo, restock).  
- **sent_date**: The date the notification was sent.  
 
**Relationships**:  
- A **Notification** is sent to a **User** and may pertain to their **Orders** or **Products** they are interested in.  

**Uniqueness**:  
- Each **Notification** has a unique **notification_id**.  

**Mandatory Fields**:  
- **customer_id**,  **type**, **sent_date**.





  
