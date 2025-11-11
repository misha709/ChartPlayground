# Chart Playground - Azure Static Web App Deployment

A simple chart application built with Chart.js, deployed as an Azure Static Web App.

## Features

- Interactive chart visualization using Chart.js
- Responsive design
- Real-time data updates
- Modern web interface

## Local Development

Simply open `index.html` in your browser to run the application locally.

## Azure Deployment

This project is configured for automatic deployment to Azure Static Web Apps using GitHub Actions.

### Prerequisites

1. **Azure Account**: You need an active Azure subscription
2. **GitHub Repository**: Your code should be in a GitHub repository
3. **Azure CLI** (optional): For command-line deployment

### Deployment Steps

#### Option 1: Azure Portal (Recommended for beginners)

1. **Create Azure Static Web App**:
   - Go to the [Azure Portal](https://portal.azure.com)
   - Click "Create a resource"
   - Search for "Static Web App" and select it
   - Click "Create"

2. **Configure the Static Web App**:
   - **Subscription**: Select your Azure subscription
   - **Resource Group**: Create new or use existing
   - **Name**: Choose a unique name for your app
   - **Plan Type**: Select "Free" for development
   - **Region**: Choose the closest region to your users
   - **Source**: Select "GitHub"
   - **Sign in**: Authenticate with GitHub
   - **Organization**: Select your GitHub organization/account
   - **Repository**: Select your repository containing this code
   - **Branch**: Select "main" (or your default branch)

3. **Build Configuration**:
   - **Build Presets**: Select "Custom"
   - **App location**: `/` (root directory)
   - **Api location**: Leave empty
   - **Output location**: Leave empty

4. **Review and Create**:
   - Review your settings
   - Click "Create"
   - Wait for deployment to complete

#### Option 2: Azure CLI

```bash
# Login to Azure
az login

# Create resource group (if needed)
az group create --name rg-chartplayground --location "East US"

# Create static web app
az staticwebapp create \
  --name chartplayground-app \
  --resource-group rg-chartplayground \
  --source https://github.com/YOUR_USERNAME/YOUR_REPO_NAME \
  --location "East US" \
  --branch main \
  --app-location "/" \
  --login-with-github
```

### Post-Deployment

1. **GitHub Integration**: Azure automatically creates a GitHub Actions workflow in your repository
2. **Custom Domain** (Optional): You can add a custom domain in the Azure Portal
3. **Environment Variables**: Configure any needed environment variables in the Azure Portal

### Automatic Deployment

Once configured, the app will automatically deploy when you:
- Push changes to the main branch
- Merge pull requests to the main branch

The GitHub Actions workflow will:
1. Checkout your code
2. Build the application (if needed)
3. Deploy to Azure Static Web Apps
4. Provide a preview URL for pull requests

### Configuration Files

- `staticwebapp.config.json`: Azure Static Web Apps configuration
- `.github/workflows/azure-static-web-apps.yml`: GitHub Actions deployment workflow

### Monitoring and Logs

- View deployment logs in GitHub Actions
- Monitor application performance in Azure Portal
- Access application insights and analytics

### Troubleshooting

**Common Issues:**

1. **Build Fails**: Check the GitHub Actions logs for detailed error messages
2. **404 Errors**: Ensure `staticwebapp.config.json` is configured correctly
3. **CORS Issues**: Update the global headers in `staticwebapp.config.json`

**Getting Help:**
- Check Azure Static Web Apps documentation
- Review GitHub Actions logs
- Contact Azure support for infrastructure issues

## Project Structure

```
├── index.html                              # Main application file
├── staticwebapp.config.json               # Azure Static Web Apps configuration  
├── .github/
│   └── workflows/
│       └── azure-static-web-apps.yml     # GitHub Actions deployment workflow
└── README.md                              # This file
```

## Technologies Used

- HTML5
- CSS3
- JavaScript
- Chart.js
- Azure Static Web Apps
- GitHub Actions

## License

This project is open source and available under the [MIT License](LICENSE).