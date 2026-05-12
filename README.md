# designswow
CRM Software Implemented In MVC framework using core and native code in PHP/MySQL/HTML/CSS/JavaScript/JQuery 
# 📊 CRM — Customer Relationship Management System

> A full-featured, native PHP/MySQL CRM built from scratch — no frameworks, no shortcuts.

---

## 📌 Overview

This is a web-based **Customer Relationship Management (CRM)** system developed using a clean **MVC (Model-View-Controller)** architecture entirely with native PHP, MySQL, HTML, JavaScript, and jQuery — without relying on any third-party backend framework. It is designed to help businesses manage the complete lifecycle of a customer: from initial lead capture all the way through to invoicing, payment collection, and post-sale followups.

The system is suitable for small-to-medium businesses looking for a self-hosted, customizable CRM solution with full source-code ownership.

---

## 🚀 Features

### 🎯 Lead Management
- Capture and register new leads with full contact details
- Classify leads by configurable **Lead Types**
- Assign leads to employees for ownership and accountability
- View and manage all leads in a searchable, paginated grid

### 🔁 Followup Management
- Log and track followups against each lead
- Record followup type, notes, next contact date and time
- Auto-schedule calendar events from followup entries
- Maintain a complete followup history per lead

### 💬 Quotation Management
- Create professional quotations from customizable templates
- Add multiple line items with product, quantity, rate, and tax
- Auto-generate PDF quotations using mPDF
- Track quotation status (draft, sent, accepted, rejected)
- Export and download quotations as PDF files

### 🛒 Orders & Sales
- Convert accepted quotations into orders
- Manage order status and delivery tracking
- Maintain a complete order history per customer

### 💰 Payment Management
- Record payments against orders
- Support for multiple configurable **Payment Types**
- Track outstanding amounts and payment history per customer

### 👥 Customer Management
- Maintain a master list of customers
- Classify customers using configurable **Customer Types**
- Manage customer bank details and financial information
- Import customers from CSV/XLS files

### 👨‍💼 Employee Management
- Add and manage employees with role-based access
- Assign employees to leads, quotations, and activities
- Track employee activities and to-do tasks
- Calendar view of employee-scheduled events (with Google Calendar API integration)

### 🏢 Organization Settings
- Configure your company profile (name, address, logo, contact)
- Manage bank accounts for invoicing purposes
- System-wide configuration panel

### 📦 Product & Inventory Master
- Define products with pricing, tax rates, and descriptions
- Organize products by **Product Types**
- Use products directly in quotation line items

### 📈 Reports & Analytics
- Dashboard with key business indicators and charts
- Reports for Leads, Customers, Employees, Quotations, Orders, and Payments
- Audit trail / activity log
- Country and currency-wise breakdowns on dashboard

### 🛠️ Master Data Management
- Countries & Currencies
- Pincodes
- Payment Types
- Lead Types
- Customer Types
- Followup Types
- Roles & Permissions
- System Configuration

---

## 🏗️ Architecture

The application follows a clean **MVC pattern**:

```
crm/
├── controllers/          # Business logic & request handling
│   ├── controller.php          # Main controller (routing hub)
│   ├── leads_controller.php
│   ├── customer_controller.php
│   ├── quotation_controller.php
│   ├── orders_controller.php
│   ├── payments_controller.php
│   ├── employee_activity_controller.php
│   ├── email_controller.php
│   ├── report_controller.php
│   ├── login_controller.php
│   └── configDB.php            # Database configuration
│
├── entities/             # Model layer — data classes (ORM-like)
│   ├── cls_leads.php
│   ├── cls_customers.php
│   ├── cls_quotations.php
│   ├── cls_orders.php
│   ├── cls_payments.php
│   ├── cls_employees.php
│   ├── cls_followup.php
│   ├── cls_products.php
│   ├── cls_roles.php
│   └── ...
│
├── js/                   # View-layer JavaScript (jQuery + vanilla JS)
├── css/                  # Stylesheets
├── assets/               # Static assets (CKEditor, Chart.js)
├── mPDF/                 # PDF generation library
├── PHPMailer-master/     # Email sending library
├── PHPExcel-1.8/         # Excel import/export library
│
├── allleads.php          # Leads list view
├── allcustomers.php      # Customers list view
├── allquotations.php     # Quotations list view
├── dashboard_*.php       # Dashboard widgets
├── index.php             # Application entry point
└── crm.sql               # Complete database schema with sample data
```

---

## 🗄️ Database Schema

The system uses **22 MySQL tables**:

| Table | Description |
|---|---|
| `leads` | Lead master data |
| `lead_types` | Lead classification types |
| `followup` | Followup records per lead |
| `followup_type` | Followup method types |
| `customers` | Customer master records |
| `customer_type` | Customer classification |
| `employees` | Employee/user records |
| `employee_activities` | Activity tracking per employee |
| `employees_to_do_activities` | Task management |
| `quotations` | Quotation header and line items (JSON) |
| `orders` | Sales orders |
| `products` | Product/service catalog |
| `product_types` | Product categories |
| `payments` | Payment records |
| `payment_types` | Payment method types |
| `organization` | Company profile |
| `bank_details` | Bank account information |
| `roles` | Role definitions for access control |
| `countries_currencies` | Country and currency master |
| `pincodes` | Pincode / zip code master |
| `calendar_events` | Scheduled events and reminders |
| `system_configuration` | System-wide settings |

---

## 🧰 Tech Stack

| Layer | Technology |
|---|---|
| **Backend** | PHP 7+ (native, no framework) |
| **Database** | MySQL / MariaDB |
| **Frontend** | HTML5, CSS3, JavaScript, jQuery |
| **UI Theme** | Bootstrap 3 + NiceAdmin template |
| **Grid Component** | jqGrid (trirand) |
| **PDF Generation** | mPDF |
| **Email** | PHPMailer |
| **Excel Import/Export** | PHPExcel 1.8 |
| **Rich Text Editor** | CKEditor |
| **Charts** | Chart.js, Morris.js |
| **Calendar** | FullCalendar.js + Google Calendar API |
| **Date Picker** | Bootstrap DateTimePicker |

---

## ⚙️ Installation

### Prerequisites

- PHP 7.0 or higher
- MySQL 5.6+ / MariaDB 10.1+
- Apache or Nginx web server
- A local or hosted LAMP/WAMP/XAMPP stack

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/crm.git
   cd crm
   ```

2. **Set up the database**
   - Create a new MySQL database named `crm`
   - Import the schema and sample data:
     ```bash
     mysql -u root -p crm < crm.sql
     ```

3. **Configure the database connection**
   - Open `controllers/configDB.php`
   - Update the credentials:
     ```php
     $host     = 'localhost';
     $dbname   = 'crm';
     $username = 'your_db_user';
     $password = 'your_db_password';
     ```

4. **Configure the web server**
   - Point your web server document root to the `crm/` directory, or place the folder inside `htdocs` / `www`
   - Ensure `mod_rewrite` is enabled (Apache)

5. **Set write permissions**
   ```bash
   chmod -R 775 quotation_files/
   chmod -R 775 mPDF/tmp/
   chmod -R 775 mPDF/ttfontdata/
   ```

6. **Access the application**
   - Open your browser: `http://localhost/crm/`
   - Default login credentials are included in the sample data (check the `employees` table in `crm.sql`)

---

## 📂 Key Files Reference

| File | Purpose |
|---|---|
| `index.php` | Application entry point & login page |
| `controllers/configDB.php` | Database connection settings |
| `controllers/controller.php` | Central request controller |
| `crm.sql` | Full database schema + sample data |
| `sidebarmenu.php` | Navigation sidebar |
| `topmenubar.php` | Top navigation bar |
| `footer.php` | Common footer |
| `settings.php` | Application settings page |
| `systemconfiguration.php` | System-level configuration UI |

---

## 🔐 Security Notes

> **Important:** Before deploying to production, please address the following:

- Change all default credentials stored in the database
- Move `configDB.php` outside the web root or restrict access via `.htaccess`
- Enable HTTPS (SSL/TLS) on your server
- Sanitize and validate all user inputs (review controller files)
- Restrict direct file access to `controllers/` and `entities/` via `.htaccess`:
  ```apacheconf
  <Directory "controllers">
      Deny from all
  </Directory>
  ```
- Remove or password-protect the `documents/` folder
- Remove sample/test data from `crm.sql` before production deployment

---

## 📸 Module Summary

| Module | View File | Controller | Entity Class |
|---|---|---|---|
| Leads | `allleads.php` | `leads_controller.php` | `cls_leads.php` |
| Followups | `leadsfollowup.php` | `controller.php` | `cls_followup.php` |
| Quotations | `allquotations.php` | `quotation_controller.php` | `cls_quotations.php` |
| Customers | `allcustomers.php` | `customer_controller.php` | `cls_customers.php` |
| Orders | `allorders.php` | `orders_controller.php` | `cls_orders.php` |
| Payments | `allpayments.php` | `payments_controller.php` | `cls_payments.php` |
| Employees | `allemployees.php` | `controller.php` | `cls_employees.php` |
| Products | `allproducts.php` | `controller.php` | `cls_products.php` |
| Reports | `*reports.php` | `report_controller.php` | — |
| Organization | `organization.php` | `controller.php` | `cls_organization.php` |
| Roles | `rolemanagement.php` | `role_controller.php` | `cls_roles.php` |

---

## 🤝 Contributing

Contributions, bug reports, and feature suggestions are welcome!

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

Please keep PRs focused and include a clear description of what was changed and why.

---

## 📝 License

This project is open-source. See the [LICENSE](LICENSE) file for details.

> The bundled third-party libraries (mPDF, PHPMailer, PHPExcel, CKEditor, Chart.js, jqGrid, FullCalendar, Bootstrap) retain their respective original licenses.

---

## 🙋 Author

Developed with ❤️ as a native PHP project — proving you don't need a heavy framework to build a complete, production-ready business application.

Author: 
Akhilesh Maurya

Company : 
https://designswow.com

Download Link : 
https://drive.google.com/file/d/13YDVpq2Ty1U9UVqXiHNN0NXsBz5IWIhB/view?usp=sharing

---

*Built on PHP · MySQL · jQuery · Bootstrap*

