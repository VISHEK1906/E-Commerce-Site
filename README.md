# 🛒 E-Commerce Platform with Authentication

A full-featured e-commerce web application built with Django, MySQL, Bootstrap, and JavaScript. This platform provides a complete online shopping experience with secure authentication, product management, and payment integration.

![Django](https://img.shields.io/badge/Django-092E20?style=flat&logo=django&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-7952B3?style=flat&logo=bootstrap&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

## 📋 Table of Contents
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [API Endpoints](#-api-endpoints)
- [Screenshots](#-screenshots)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)

## ✨ Features

### 🔐 Authentication & Authorization
- User registration with email verification
- Secure login/logout system
- Password reset functionality
- JWT-based authentication
- Role-based access control (Admin/Customer)

### 🛍️ Product Management
- Product catalog with categories
- Advanced search functionality
- Product filtering and sorting
- Detailed product pages with images
- Product reviews and ratings
- Inventory management

### 🛒 Shopping Experience
- Add to cart functionality
- Cart management (add, update, remove items)
- Wishlist feature
- Order history tracking
- Real-time stock availability

### 💳 Payment & Checkout
- Secure payment gateway integration
- Multiple payment methods support
- Order confirmation emails
- Invoice generation

### 📊 Admin Dashboard
- Product CRUD operations
- Order management
- User management
- Sales analytics
- Inventory tracking

### 🎨 User Interface
- Responsive design (mobile-friendly)
- Intuitive navigation
- Fast loading pages
- Dynamic content loading
- Modern UI with Bootstrap

## 🛠️ Tech Stack

**Backend:**
- Django 4.x
- Django REST Framework
- MySQL 8.0
- Python 3.10+

**Frontend:**
- HTML5
- CSS3
- JavaScript (ES6+)
- Bootstrap 5
- jQuery
- AJAX

**Other Tools:**
- Git for version control
- Virtual Environment (venv)
- Django Debug Toolbar

## 🚀 Installation

### Prerequisites
- Python 3.10 or higher
- MySQL 8.0 or higher
- Git
- Virtual Environment

### Step 1: Clone the Repository
```bash
git clone https://github.com/VISHEK1906/ecommerce-platform.git
cd ecommerce-platform
```

### Step 2: Create Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux/Mac
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Setup MySQL Database
```sql
CREATE DATABASE ecommerce_db;
CREATE USER 'ecommerce_user'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON ecommerce_db.* TO 'ecommerce_user'@'localhost';
FLUSH PRIVILEGES;
```

### Step 5: Configure Environment Variables
Create a `.env` file in the root directory:
```env
SECRET_KEY=your_secret_key_here
DEBUG=True
DB_NAME=ecommerce_db
DB_USER=ecommerce_user
DB_PASSWORD=your_password
DB_HOST=localhost
DB_PORT=3306

# Email Configuration
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_HOST_USER=your_email@gmail.com
EMAIL_HOST_PASSWORD=your_email_password

# Payment Gateway
PAYMENT_API_KEY=your_payment_api_key
PAYMENT_SECRET_KEY=your_payment_secret_key
```

### Step 6: Run Migrations
```bash
python manage.py makemigrations
python manage.py migrate
```

### Step 7: Create Superuser
```bash
python manage.py createsuperuser
```

### Step 8: Collect Static Files
```bash
python manage.py collectstatic
```

### Step 9: Run Development Server
```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000` in your browser.

## ⚙️ Configuration

### Database Settings
Edit `settings.py`:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': os.getenv('DB_NAME'),
        'USER': os.getenv('DB_USER'),
        'PASSWORD': os.getenv('DB_PASSWORD'),
        'HOST': os.getenv('DB_HOST'),
        'PORT': os.getenv('DB_PORT'),
    }
}
```

### Email Settings
```python
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = os.getenv('EMAIL_HOST')
EMAIL_PORT = os.getenv('EMAIL_PORT')
EMAIL_USE_TLS = True
EMAIL_HOST_USER = os.getenv('EMAIL_HOST_USER')
EMAIL_HOST_PASSWORD = os.getenv('EMAIL_HOST_PASSWORD')
```

## 📖 Usage

### For Customers
1. **Register/Login**: Create an account or login
2. **Browse Products**: Explore product catalog
3. **Search**: Use search bar to find specific products
4. **Add to Cart**: Select products and add to cart
5. **Checkout**: Proceed to checkout and complete payment
6. **Track Orders**: View order history and status

### For Admin
1. **Login to Admin Panel**: `http://127.0.0.1:8000/admin`
2. **Manage Products**: Add, edit, or delete products
3. **Process Orders**: View and update order status
4. **Manage Users**: View and manage customer accounts
5. **View Analytics**: Check sales reports and statistics

## 🔌 API Endpoints

### Authentication
```
POST /api/auth/register/          - User registration
POST /api/auth/login/             - User login
POST /api/auth/logout/            - User logout
POST /api/auth/password-reset/    - Password reset
```

### Products
```
GET    /api/products/             - List all products
GET    /api/products/<id>/        - Get product details
POST   /api/products/             - Create product (Admin)
PUT    /api/products/<id>/        - Update product (Admin)
DELETE /api/products/<id>/        - Delete product (Admin)
GET    /api/products/search/      - Search products
```

### Cart
```
GET    /api/cart/                 - View cart
POST   /api/cart/add/             - Add item to cart
PUT    /api/cart/update/<id>/     - Update cart item
DELETE /api/cart/remove/<id>/     - Remove item from cart
DELETE /api/cart/clear/           - Clear cart
```

### Orders
```
GET    /api/orders/               - List user orders
GET    /api/orders/<id>/          - Get order details
POST   /api/orders/create/        - Create new order
PUT    /api/orders/<id>/status/   - Update order status (Admin)
```

## 📸 Screenshots

### Home Page
![Home Page](screenshots/home.png)

### Product Catalog
![Products](screenshots/products.png)

### Shopping Cart
![Cart](screenshots/cart.png)

### Checkout
![Checkout](screenshots/checkout.png)

### Admin Dashboard
![Admin](screenshots/admin.png)

## 🏗️ Project Structure

```
ecommerce-platform/
│
├── ecommerce/                 # Project settings
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
│
├── products/                  # Products app
│   ├── models.py
│   ├── views.py
│   ├── serializers.py
│   └── urls.py
│
├── cart/                      # Shopping cart app
│   ├── models.py
│   ├── views.py
│   └── urls.py
│
├── orders/                    # Orders app
│   ├── models.py
│   ├── views.py
│   └── urls.py
│
├── users/                     # User authentication app
│   ├── models.py
│   ├── views.py
│   └── urls.py
│
├── static/                    # Static files
│   ├── css/
│   ├── js/
│   └── images/
│
├── templates/                 # HTML templates
│   ├── base.html
│   ├── home.html
│   └── products/
│
├── media/                     # User uploaded files
├── requirements.txt           # Python dependencies
├── manage.py                  # Django management script
└── README.md                  # This file
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 Requirements

```txt
Django==4.2.7
djangorestframework==3.14.0
mysqlclient==2.2.0
Pillow==10.1.0
python-decouple==3.8
django-cors-headers==4.3.0
django-filter==23.3
```

## 🔒 Security Features

- CSRF protection enabled
- SQL injection prevention
- XSS protection
- Secure password hashing (PBKDF2)
- HTTPS enforcement in production
- Rate limiting on API endpoints
- Input validation and sanitization

## 🚧 Roadmap

- [ ] Add social media authentication
- [ ] Implement product recommendations
- [ ] Add multi-currency support
- [ ] Integrate advanced analytics
- [ ] Add live chat support
- [ ] Mobile app development
- [ ] Add product comparison feature
- [ ] Implement discount/coupon system

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**Vishek Kumar**

- GitHub: [@VISHEK1906](https://github.com/VISHEK1906)
- LinkedIn: [vishek-kumar-vk](https://linkedin.com/in/vishek-kumar-vk)
- Email: kumarvishek1906@gmail.com

## 🙏 Acknowledgments

- Django Documentation
- Bootstrap Team
- MySQL Community
- Open Source Contributors

## 📞 Support

For support, email kumarvishek1906@gmail.com or create an issue in the repository.

---

⭐ Star this repository if you find it helpful!

**Made with ❤️ by Vishek Kumar**
