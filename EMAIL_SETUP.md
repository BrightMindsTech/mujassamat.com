# Email Configuration Guide for Mujassamat

## Overview
The Mujassamat application supports three email sending modes:
1. **MAILTO** (default) - Opens user's email client
2. **EmailJS** - Cloud-based email service (no server needed)
3. **Nodemailer** - Direct SMTP sending (recommended for production)

## Current Configuration
Currently using **MAILTO** mode, which doesn't send emails directly but opens the user's email client.

## Setting Up Gmail with Nodemailer (Recommended)

### Step 1: Create Gmail App Password
1. Go to your Google Account settings: https://myaccount.google.com/
2. Navigate to Security → 2-Step Verification (must be enabled)
3. Click on "App passwords" at the bottom
4. Select "Mail" and your device
5. Copy the generated 16-character password

### Step 2: Set Environment Variables
Add these to your `.env` file:
```env
# Email Configuration
VITE_EMAIL_MODE=NODEMAILER
EMAIL_USER=mujassamat.jo@gmail.com
EMAIL_PASSWORD=your-app-password-here

# Optional: For client-side SMTP (not recommended)
VITE_SMTP_HOST=smtp.gmail.com
VITE_SMTP_PORT=587
VITE_SMTP_USER=mujassamat.jo@gmail.com
VITE_SMTP_PASS=your-app-password-here
```

### Step 3: Restart the Application
After setting the environment variables, restart the application:
```bash
npm run dev
```

## Alternative: Using EmailJS (No Server Required)

### Step 1: Create EmailJS Account
1. Sign up at https://www.emailjs.com/
2. Add Gmail as your email service
3. Create an email template for quotes and contact forms
4. Get your Service ID, Template ID, and Public Key

### Step 2: Set Environment Variables
```env
VITE_EMAIL_MODE=EMAILJS
VITE_EMAILJS_SERVICE_ID=your-service-id
VITE_EMAILJS_TEMPLATE_ID=your-template-id
VITE_EMAILJS_PUBLIC_KEY=your-public-key
```

## Testing Email Configuration
1. Submit a quote request from `/quote`
2. Send a message from `/contact`
3. Check that emails are received at `mujassamat.jo@gmail.com`

## Security Notes
- Never commit credentials to version control
- Use app passwords, not your main Gmail password
- Consider using a dedicated email account for the application
- Keep EMAIL_PASSWORD on server-side only (not VITE_ prefixed)

## Troubleshooting
- **"Authentication failed"**: Check app password is correct
- **"Less secure app blocked"**: Use app password, not regular password
- **Emails not sending**: Check firewall/network allows SMTP (port 587)
- **Rate limiting**: Gmail has daily sending limits (500 emails/day)

## Current Implementation Status
✅ Server-side Nodemailer configured in `/server/routes.ts`
✅ Client-side email helpers in `/client/src/lib/email.ts`
✅ Environment variable support ready
⚠️ Awaiting Gmail app password configuration