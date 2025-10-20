# PythonAnywhere Deployment Guide

## 1. Upload Your Code
- Upload your project to PythonAnywhere via Git or file upload
- Ensure the project structure is: `/home/yourusername/NEW_hangarin2/projectsite/`

## 2. Set Up Virtual Environment
```bash
cd /home/yourusername/NEW_hangarin2
python3.10 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## 3. Configure Environment Variables
In PythonAnywhere Web tab → Environment variables:
- `DJANGO_DEBUG` = `False`
- `DJANGO_ALLOWED_HOSTS` = `youjeez.pythonanywhere.com`
- `EMAIL_HOST_USER` = `your-gmail@gmail.com` (optional, for email)
- `EMAIL_HOST_PASSWORD` = `your-app-password` (optional, for email)
- `DEFAULT_FROM_EMAIL` = `noreply@youjeez.pythonanywhere.com`

## 4. Database Setup
```bash
cd /home/yourusername/NEW_hangarin2/projectsite
python manage.py migrate
python manage.py createsuperuser
```

## 5. Static Files
```bash
python manage.py collectstatic --noinput
```

## 6. Web App Configuration
- **Source code**: `/home/yourusername/NEW_hangarin2/projectsite`
- **Working directory**: `/home/yourusername/NEW_hangarin2/projectsite`
- **Virtualenv**: `/home/yourusername/NEW_hangarin2/venv`
- **WSGI file**: `/home/yourusername/NEW_hangarin2/projectsite/projectsite/wsgi.py`

## 7. Static Files Mapping
- **URL**: `/static/`
- **Directory**: `/home/yourusername/NEW_hangarin2/projectsite/staticfiles`

## 8. Social Login Setup (Optional)
1. Go to Django admin → Social Applications
2. Add Google provider:
   - Provider: Google
   - Client id: from Google Cloud Console
   - Secret key: from Google Cloud Console
   - Sites: select your site
3. Add GitHub provider:
   - Provider: GitHub
   - Client id: from GitHub Developer Settings
   - Secret key: from GitHub Developer Settings
   - Sites: select your site

## 9. Reload Web App
Click "Reload" in the Web tab

## 10. Test
Visit `https://youjeez.pythonanywhere.com/`
- Should redirect to login page
- Test signup/login functionality
- Verify static files (CSS/JS) load correctly

## Troubleshooting
- If CSS doesn't load: check static files mapping path
- If 500 errors: check PythonAnywhere error logs
- If email issues: verify EMAIL_HOST_USER/PASSWORD are set
