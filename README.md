<<<<<<< HEAD
# TechStore - E-commerce Web Application

A modern e-commerce web application built with Flask, DynamoDB, and AWS Elastic Beanstalk. This application demonstrates user registration, authentication, and a sample e-commerce interface.

## Features

- **User Registration & Authentication**: Secure user registration and login system
- **DynamoDB Integration**: User data stored in AWS DynamoDB
- **Modern UI**: Responsive design with Bootstrap 5 and custom CSS
- **E-commerce Interface**: Sample product catalog with shopping cart functionality
- **AWS Elastic Beanstalk**: Easy deployment and scaling
- **RESTful API**: API endpoints for user management

## Technology Stack

- **Backend**: Flask (Python)
- **Database**: AWS DynamoDB
- **Deployment**: AWS Elastic Beanstalk
- **Frontend**: HTML5, CSS3, JavaScript, Bootstrap 5
- **Authentication**: bcrypt for password hashing
- **Forms**: Flask-WTF with validation

## Project Structure

```
elastic-beanstalk/
├── application.py              # Main Flask application
├── requirements.txt            # Python dependencies
├── Procfile                    # Elastic Beanstalk configuration
├── .ebextensions/              # Elastic Beanstalk extensions
│   ├── 01_packages.config      # Package installation
│   └── 02_environment.config   # Environment variables
├── templates/                  # HTML templates
│   ├── base.html              # Base template
│   ├── home.html              # Home page
│   ├── register.html          # Registration page
│   ├── login.html             # Login page
│   └── profile.html           # User profile page
├── static/                     # Static files
│   ├── css/
│   │   └── style.css          # Custom styles
│   └── js/
│       └── script.js          # JavaScript functionality
└── README.md                   # This file
```

## Prerequisites

- Python 3.8 or higher
- AWS CLI configured
- AWS Elastic Beanstalk CLI (optional)
- AWS DynamoDB table (will be created automatically)

## Local Development Setup

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd elastic-beanstalk
   ```

2. **Create a virtual environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up AWS credentials**:
   ```bash
   aws configure
   ```

5. **Run the application locally**:
   ```bash
   python application.py
   ```

6. **Access the application**:
   Open your browser and go to `http://localhost:5000`

## AWS Setup

### 1. DynamoDB Table

The application will automatically create a DynamoDB table named `ecommerce-users` with the following structure:

- **Primary Key**: `email` (String)
- **Attributes**:
  - `name` (String)
  - `password` (String) - Hashed with bcrypt
  - `created_at` (String) - ISO format timestamp

### 2. IAM Permissions

Ensure your AWS credentials have the following permissions:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "dynamodb:CreateTable",
                "dynamodb:DescribeTable",
                "dynamodb:GetItem",
                "dynamodb:PutItem",
                "dynamodb:Scan",
                "dynamodb:UpdateItem",
                "dynamodb:DeleteItem"
            ],
            "Resource": "arn:aws:dynamodb:*:*:table/ecommerce-users"
        }
    ]
}
```

## Deployment to Elastic Beanstalk

### Method 1: Using AWS Console

1. **Create an Elastic Beanstalk application**:
   - Go to AWS Elastic Beanstalk Console
   - Click "Create Application"
   - Choose "Web server environment"
   - Platform: Python
   - Platform branch: Python 3.8
   - Platform version: Latest

2. **Upload your code**:
   - Create a ZIP file of your project (excluding `venv/` and `__pycache__/`)
   - Upload the ZIP file in the Elastic Beanstalk console

3. **Configure environment variables**:
   - Go to Configuration → Software
   - Add environment variables:
     - `SECRET_KEY`: Your secret key
     - `DYNAMODB_TABLE`: `ecommerce-users`
     - `AWS_DEFAULT_REGION`: `us-east-1`

### Method 2: Using EB CLI

1. **Install EB CLI**:
   ```bash
   pip install awsebcli
   ```

2. **Initialize EB application**:
   ```bash
   eb init
   ```

3. **Create environment**:
   ```bash
   eb create production
   ```

4. **Deploy**:
   ```bash
   eb deploy
   ```

## API Endpoints

### Authentication
- `POST /register` - User registration
- `POST /login` - User login
- `GET /logout` - User logout

### User Management
- `GET /profile` - User profile page
- `GET /api/users` - List all users (requires authentication)

### Pages
- `GET /` - Home page with products
- `GET /register` - Registration form
- `GET /login` - Login form

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `SECRET_KEY` | Flask secret key | `your-secret-key-change-in-production` |
| `DYNAMODB_TABLE` | DynamoDB table name | `ecommerce-users` |
| `AWS_DEFAULT_REGION` | AWS region | `us-east-1` |
| `FLASK_ENV` | Flask environment | `production` |
| `FLASK_DEBUG` | Flask debug mode | `False` |

## Security Features

- **Password Hashing**: Passwords are hashed using bcrypt
- **CSRF Protection**: Flask-WTF provides CSRF protection
- **Input Validation**: Form validation on both client and server side
- **Session Management**: Secure session handling
- **Environment Variables**: Sensitive data stored in environment variables

## Customization

### Adding New Products

Edit the `products` list in `application.py`:

```python
products = [
    {
        'id': 5,
        'name': 'New Product',
        'price': 299.99,
        'description': 'Product description',
        'image': 'https://example.com/image.jpg'
    }
]
```

### Styling

Modify `static/css/style.css` to customize the appearance.

### JavaScript Functionality

Edit `static/js/script.js` to add new interactive features.

## Troubleshooting

### Common Issues

1. **DynamoDB Connection Error**:
   - Ensure AWS credentials are properly configured
   - Check IAM permissions for DynamoDB
   - Verify the region is correct

2. **Elastic Beanstalk Deployment Issues**:
   - Check the logs in the Elastic Beanstalk console
   - Ensure all dependencies are in `requirements.txt`
   - Verify the `Procfile` is correct

3. **Static Files Not Loading**:
   - Check the `.ebextensions/01_packages.config` file
   - Ensure static files are in the correct directory

### Logs

- **Local**: Check console output
- **Elastic Beanstalk**: Go to Environment → Logs → Request logs

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support and questions:
- Create an issue in the repository
- Check the AWS documentation for Elastic Beanstalk and DynamoDB
- Review the Flask documentation for web framework questions 
=======
# elastic-beanstalk-ecommerce-app
>>>>>>> d89ff78641029e00cb2dbeba9cfef085ec0495e2
