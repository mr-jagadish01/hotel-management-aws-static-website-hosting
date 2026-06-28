## Royal Palace Hotel Website ##

Royal Palace Hotel Website is a responsive web application designed to showcase hotel services, rooms, events, gallery, pricing, and contact information. The website provides a modern user experience across desktop, tablet, and mobile devices..

## 🏨 Project Overview ##

Royal Palace is a beautifully designed hotel website featuring:
- Responsive design that works on all devices
- Hotel information and services showcase
- Photo gallery with lightbox effects
- Events management section
- Pricing tables
- Team member profiles
- Contact form for inquiries
- Smooth scrolling navigation

## 📁 Project Structure ##

```
Royal Palace Orignal/
├── index.html                      # Main homepage
├── inner-page.html                 # Inner page template
├── portfolio-details.html          # Gallery item details
├── README.md                       # Project documentation
├── INDEX.md                        # Documentation index
├── ARCHITECTURE.md                 # Architecture documentation
├── DEPLOYMENT_GUIDE.md             # Deployment guide
├── LIVE_DEMO.md                    # Live demo report
├── QUICK_REFERENCE.md              # Quick deployment reference
├── deployment-info/                # AWS service and cost notes
│   ├── SERVICES.md
│   └── COSTS.md
├── metrics/                        # Performance and monitoring notes
│   └── PERFORMANCE_STATS.md
├── forms/
│   ├── contact.php                 # Contact form handler
│   └── Readme.txt                   # Template instructions
├── assets/
│   ├── css/
│   │   └── style.css               # Custom styling
│   ├── js/
│   │   └── main.js                 # Custom JavaScript
│   ├── img/                        # Website images and media
│   ├── scss/                       # SCSS source (pro version)
│   └── vendor/                     # Third-party libraries
│       ├── bootstrap/
│       ├── bootstrap-icons/
│       ├── boxicons/
│       ├── glightbox/
│       ├── isotope-layout/
│       ├── remixicon/
│       └── swiper/
├── AWS-Architecture-screenshot/     # Architecture and workflow screenshots
│   ├── architecture.png
│   └── workflow.png
├── AWS-Console-screenshot/          # AWS console deployment screenshots
│   ├── Screenshot 2026-06-28 192101.png
│   ├── Screenshot 2026-06-28 192123.png
│   ├── Screenshot 2026-06-28 192158.png
│   └── Screenshot 2026-06-28 192234.png
└── hotel-management-live-server-working-screenshots/
    ├── Screenshot 2026-06-28 203703.png
    ├── Screenshot 2026-06-28 203723.png
    ├── Screenshot 2026-06-28 203750.png
    ├── Screenshot 2026-06-28 203803.png
    ├── Screenshot 2026-06-28 203843.png
    ├── Screenshot 2026-06-28 203900.png
    └── Screenshot 2026-06-28 203941.png
```

## � Documentation Overview ##

- `INDEX.md` — primary documentation index for the project.
- `ARCHITECTURE.md` — AWS architecture and deployment topology.
- `DEPLOYMENT_GUIDE.md` — step-by-step S3 and CloudFront deployment instructions.
- `LIVE_DEMO.md` — live deployment evidence and AWS console summary.
- `QUICK_REFERENCE.md` — essential deployment commands and troubleshooting notes.
- `deployment-info/SERVICES.md` — AWS service inventory and roles.
- `deployment-info/COSTS.md` — cost categories and estimate guidance.
- `metrics/PERFORMANCE_STATS.md` — performance metrics and monitoring recommendations.

## �🛠️ Technologies Used ##

- **HTML5** - Semantic markup
- **CSS3** - Custom styling with Bootstrap 5
- **JavaScript** - Interactive features
- **Bootstrap 5** - Responsive framework
- **PHP** - Backend form handling
- **Third-party Libraries:**
  - Glightbox - Image lightbox
  - Swiper - Touch carousel slider
  - Isotope - Portfolio grid filtering
  - Bootstrap Icons, Boxicons, Remix Icons

## 🎨 Color Scheme ##

- **Primary Color:** #85b0be (Teal/Blue)
- **Secondary Colors:** Various shades for contrast and accessibility

## 📋 Key Features ##

### Navigation ##
- Fixed transparent header with logo
- Smooth scroll navigation
- Mobile-responsive hamburger menu
- Active state tracking on scroll

### Sections ##
- **Hero** - Eye-catching landing banner
- **About** - Hotel information and highlights
- **Services** - Amenities and services
- **Gallery** - Photo gallery with lightbox
- **Events** - Event management section
- **Pricing** - Room/package pricing
- **Team** - Staff profiles
- **Contact** - Contact form and information

### Responsive Design ##
- Mobile-first approach
- Tablet and desktop optimization
- Touch-friendly interface

## 🚀 Getting Started ##

### Prerequisites ##
- Modern web browser
- Optional: PHP server for contact form functionality

### Installation ##

1. Clone the repository
```bash
git clone https://github.com/yourusername/royal-palace.git
cd royal-palace
```

2. Open in browser
```bash
# Simple way - just open index.html in your browser
# Or use a local server for better experience
```

3. For local PHP development
```bash
# Using PHP built-in server
php -S localhost:8000

# Then visit http://localhost:8000
```

## 💬 Contact Form ##

The contact form is handled by `forms/contact.php`. To enable:

1. Ensure your hosting supports PHP
2. Update sender email in `forms/contact.php`
3. Customize validation in `assets/vendor/php-email-form/validate.js`

## 📝 Customization

### Update Hotel Information
- Edit content in `index.html`
- Update images in `assets/img/`
- Replace logo with your hotel's logo

### Styling
- Custom CSS in `assets/css/style.css`
- Modify colors and fonts as needed
- SCSS files available in pro version only

### Navigation Links
- Update navigation items in header
- Modify section IDs for smooth scrolling
- Update mobile menu in `assets/js/main.js`


## 📄 License

This project is created for educational and portfolio purposes.


## 👥 Credits

**Created by:** Mahesh Suryawanshi 

## 🤝 Contributing

Feel free to fork this project and submit pull requests with improvements.

## ❓ Support

For issues or questions, please create an issue in the repository.

---

**Last Updated:** June 18, 2026
