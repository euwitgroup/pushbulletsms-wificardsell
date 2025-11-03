# 📱 SMS & Card Sale

A comprehensive Laravel-based web application for SMS sending and WiFi card sales management with admin panel, payment gateway integration, and automated features.

---

## 🌟 Key Features

### SMS Management System
- ✅ Send bulk SMS to multiple recipients
- ✅ Multiple SMS gateway support
- ✅ Customizable SMS templates
- ✅ SMS history tracking
- ✅ Gateway cost management
- ✅ Package-based pricing

### WiFi Card Sales System
- ✅ Guest checkout (no login required)
- ✅ Category-based card organization
- ✅ Automated key delivery via SMS
- ✅ Auto-restock expired pending cards (2-minute timeout)
- ✅ Real-time inventory management
- ✅ Transaction history
- ✅ Card history tracking

### User Management
- ✅ Role-based access control (Admin/User)
- ✅ KYC verification system
- ✅ Profile management
- ✅ Wallet & balance management
- ✅ Transaction history

### Payment Integration
- ✅ RupantorPay payment gateway
- ✅ Secure guest payments
- ✅ Automated transaction tracking
- ✅ Success/Cancel handling
- ✅ Webhook support

### Admin Panel
- ✅ Comprehensive dashboard with statistics
- ✅ User management
- ✅ SMS package management
- ✅ WiFi card management
- ✅ Content management (Blog, FAQ, Sliders)
- ✅ Settings configuration
- ✅ Reports and analytics

### Additional Features
- ✅ Multi-channel notifications (Email, SMS, Pushbullet, In-app)
- ✅ Responsive mobile-friendly design
- ✅ SEO optimized
- ✅ Security hardened
- ✅ Automated scheduled tasks
- ✅ Queue support for background jobs

---

## 📋 Tech Stack

- **Framework**: Laravel 9.52.21
- **PHP**: 8.2.12
- **Database**: MySQL 5.7+
- **Frontend**: Blade Templates, jQuery, SweetAlert2
- **CSS**: Bootstrap, Custom CSS
- **Icons**: Font Awesome
- **Payment**: RupantorPay
- **Notifications**: Pushbullet API

---

## 📦 Installation

### ⚡ Web-Based Installation Wizard (NEW!)

The easiest way to install! A WordPress-like installer that handles everything automatically.

**Just 3 Steps**:
1. Upload files to your server
2. Set permissions: `chmod -R 775 storage bootstrap/cache`
3. Visit: `https://yourdomain.com/install`

**Features**:
- ✅ Automatic requirements check
- ✅ Live database connection test
- ✅ One-click migration & seeding
- ✅ Modern, step-by-step wizard
- ✅ Takes only 5-10 minutes!

👉 **See [INSTALLATION_WIZARD_GUIDE.md](INSTALLATION_WIZARD_GUIDE.md) for details**

---

### Local Development Setup

1. **Clone Repository**
```bash
git clone <your-repository-url>
cd sms_&_Card_Sale
```

2. **Install Dependencies**
```bash
composer install
npm install
```

3. **Environment Configuration**
```bash
cp .env.example .env
php artisan key:generate
```

4. **Configure Database**
Update `.env` file with your database credentials:
```env
DB_DATABASE=your_database_name
DB_USERNAME=your_database_user
DB_PASSWORD=your_database_password
```

5. **Run Migrations & Seeders**
```bash
php artisan migrate
php artisan db:seed
```

6. **Create Storage Link**
```bash
php artisan storage:link
```

7. **Build Assets**
```bash
npm run dev
```

8. **Start Development Server**
```bash
php artisan serve
```

Visit: `http://localhost:8000`

**Default Admin Credentials**:
- Email: `admin@example.com`
- Password: `password`

---

## 🚀 Production Deployment

### Complete Deployment Documentation

We've created comprehensive guides for deploying to a live server:

1. **📖 [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md)** - Complete step-by-step deployment instructions
2. **✅ [PRE_DEPLOYMENT_CHECKLIST.md](PRE_DEPLOYMENT_CHECKLIST.md)** - Checklist before deployment
3. **📄 [ENV_PRODUCTION_TEMPLATE.txt](ENV_PRODUCTION_TEMPLATE.txt)** - Production environment template
4. **⚙️ [nginx.conf.example](nginx.conf.example)** - Nginx configuration
5. **⚙️ [apache.conf.example](apache.conf.example)** - Apache configuration
6. **🔧 [deploy.sh](deploy.sh)** - Automated deployment script

### Quick Deployment Steps

1. **Prepare Your Server** (Ubuntu/Debian)
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install php8.2-fpm php8.2-mysql nginx mysql-server composer nodejs npm
```

2. **Upload Project Files**
```bash
cd /var/www/
sudo git clone <your-repository-url> sms-card-sale
cd sms-card-sale
```

3. **Install Dependencies**
```bash
composer install --no-dev --optimize-autoloader
npm install && npm run production
```

4. **Configure Environment**
```bash
cp ENV_PRODUCTION_TEMPLATE.txt .env
nano .env
# Update all production values
php artisan key:generate
```

5. **Set Up Database**
```bash
mysql -u root -p
# Create database and user
php artisan migrate --force
php artisan db:seed --force
```

6. **Set Permissions**
```bash
sudo chown -R www-data:www-data /var/www/sms-card-sale
sudo chmod -R 775 storage bootstrap/cache
```

7. **Configure Web Server**
```bash
# For Nginx
sudo cp nginx.conf.example /etc/nginx/sites-available/sms-card-sale
sudo ln -s /etc/nginx/sites-available/sms-card-sale /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx

# For Apache
sudo cp apache.conf.example /etc/apache2/sites-available/sms-card-sale.conf
sudo a2ensite sms-card-sale.conf
sudo a2enmod rewrite headers
sudo systemctl restart apache2
```

8. **Install SSL Certificate**
```bash
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
```

9. **Set Up Cron Jobs**
```bash
sudo crontab -e -u www-data
# Add: * * * * * cd /var/www/sms-card-sale && php artisan schedule:run >> /dev/null 2>&1
```

10. **Optimize for Production**
```bash
php artisan config:cache
php artisan route:cache
php artisan view:cache
```

**For detailed instructions, see [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md)**

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md) | Complete deployment guide with all steps |
| [PRE_DEPLOYMENT_CHECKLIST.md](PRE_DEPLOYMENT_CHECKLIST.md) | Pre-deployment checklist |
| [ENV_PRODUCTION_TEMPLATE.txt](ENV_PRODUCTION_TEMPLATE.txt) | Production environment variables |
| [nginx.conf.example](nginx.conf.example) | Nginx server configuration |
| [apache.conf.example](apache.conf.example) | Apache server configuration |
| [deploy.sh](deploy.sh) | Automated deployment script |

---

## 🔐 Security

### Production Security Checklist

- ✅ Set `APP_ENV=production` and `APP_DEBUG=false`
- ✅ Use strong database passwords
- ✅ Enable HTTPS with SSL certificate
- ✅ Set proper file permissions (775 for storage)
- ✅ Configure firewall (UFW/iptables)
- ✅ Enable CSRF protection
- ✅ Use environment variables for sensitive data
- ✅ Set up automated backups
- ✅ Configure rate limiting
- ✅ Keep Laravel and dependencies updated

---

## ⚙️ Configuration

### Required Environment Variables

```env
APP_URL=https://yourdomain.com
DB_DATABASE=your_database
DB_USERNAME=your_user
DB_PASSWORD=your_password
MAIL_HOST=smtp.gmail.com
MAIL_USERNAME=your-email@gmail.com
MAIL_PASSWORD=your-app-password
RUPANTORPAY_API_KEY=your_api_key
PUSHBULLET_ACCESS_TOKEN=your_token
```

See `ENV_PRODUCTION_TEMPLATE.txt` for complete configuration.

---

## 🔄 Scheduled Tasks

The application includes automated scheduled tasks:

| Task | Schedule | Purpose |
|------|----------|---------|
| Release Expired Pending Cards | Every Minute | Auto-release card keys after 2 minutes |

**Setup**: Add to crontab
```bash
* * * * * cd /path-to-project && php artisan schedule:run >> /dev/null 2>&1
```

---

## 🧪 Testing

### Run Tests
```bash
php artisan test
```

### Test Coverage
- Unit Tests: `tests/Unit/`
- Feature Tests: `tests/Feature/`

---

## 🔄 Updating

When updating your live application:

```bash
cd /var/www/sms-card-sale
sudo git pull origin main
composer install --no-dev --optimize-autoloader
npm install && npm run production
php artisan migrate --force
php artisan config:cache
php artisan route:cache
php artisan view:cache
sudo systemctl restart nginx
```

Or use the automated script:
```bash
sudo bash deploy.sh
```

---

## 📊 Database Structure

The application uses 24 database tables:

**Core Tables**:
- users, transactions, sms_history, settings

**SMS System**:
- sms_packages, sms_templates, sms_gateways, sms_prices

**WiFi Card System**:
- card_categories, card_types, card_keys, card_transactions

**Content Management**:
- blogs, faqs, hero_sliders, why_choose_us, comparison_features, contact_infos

**Notifications**:
- notifications

---

## 🛠️ Troubleshooting

### Common Issues

**500 Internal Server Error**
```bash
tail -100 storage/logs/laravel.log
php artisan config:clear
php artisan cache:clear
```

**Permission Denied**
```bash
sudo chmod -R 775 storage bootstrap/cache
sudo chown -R www-data:www-data storage bootstrap/cache
```

**Storage Link Not Working**
```bash
php artisan storage:link
```

**Database Connection Error**
- Check `.env` credentials
- Verify MySQL is running: `sudo systemctl status mysql`

---

## 📞 Support

For deployment issues or questions:

1. Check [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md)
2. Review [PRE_DEPLOYMENT_CHECKLIST.md](PRE_DEPLOYMENT_CHECKLIST.md)
3. Check Laravel logs: `storage/logs/laravel.log`
4. Check web server logs: `/var/log/nginx/` or `/var/log/apache2/`

---

## 📝 License

This project is proprietary software. All rights reserved.

---

## 👨‍💻 Development

**Built with** ❤️ using Laravel

**Version**: 1.0.0  
**Last Updated**: November 2, 2025  
**PHP Version**: 8.2.12  
**Laravel Version**: 9.52.21

---

## 🎉 Ready to Deploy?

1. ✅ Review [PRE_DEPLOYMENT_CHECKLIST.md](PRE_DEPLOYMENT_CHECKLIST.md)
2. ✅ Follow [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md)
3. ✅ Test all features
4. ✅ Monitor logs for 24 hours
5. ✅ Celebrate! 🎊

---

**Need Help Deploying?** Check out our comprehensive [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md)!
