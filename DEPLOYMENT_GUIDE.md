# Oracle Bot V2 - Deployment Guide

## 📋 Prerequisites

Before deploying, ensure you have:
- [ ] GitHub account
- [ ] Render.com account (free tier available)
- [ ] Groq API key (get from https://console.groq.com/)
- [ ] All project files ready

## 🚀 Step-by-Step Deployment

### Step 1: Prepare Your Files

Verify you have all files in `oracle-bot-v2/`:
```
oracle-bot-v2/
├── app.py
├── requirements.txt
├── natal_calculator.py
├── ai_system_prompt.txt
├── business_rag.json
├── cultural_avatars_rag.json
├── deepsyke_core_rag.json
├── engagement_protocol.json
├── templates/index.html
├── start.sh
├── .render-build.sh
└── README.md
```

### Step 2: Create GitHub Repository

1. Go to https://github.com/new
2. Repository name: `oracle-bot-v2` (or your preferred name)
3. Make it **Public** (for free Render deployment)
4. Click "Create repository"

### Step 3: Upload Files to GitHub

**CRITICAL: How to create the templates folder correctly**

The `templates/index.html` file structure is tricky on GitHub. Follow these exact steps:

#### Method 1: Using GitHub Web Interface (Easiest)

1. On your repository page, click "Add file" → "Create new file"
2. **IMPORTANT**: In the "Name your file" field, type: `templates/index.html`
   - Notice the forward slash `/` - this tells GitHub to create a folder
3. Paste the entire content of `index.html` into the file editor
4. Click "Commit changes"

GitHub will automatically:
- Create the `templates` folder
- Place `index.html` inside it
- Handle the folder structure correctly

#### Method 2: Using Git Command Line

If you prefer using git commands:

```bash
# Navigate to your project directory
cd oracle-bot-v2

# Initialize git repository (if not already done)
git init

# Add all files
git add .

# Commit changes
git commit -m "Initial commit - Oracle Bot V2"

# Add remote repository
git remote add origin https://github.com/YOUR_USERNAME/oracle-bot-v2.git

# Push to GitHub
git branch -M main
git push -u origin main
```

**Verification:**
After pushing, go to your GitHub repository and verify:
- You should see a `templates` folder
- Inside `templates`, you should see `index.html`
- All other files should be in the root directory

### Step 4: Deploy to Render

#### Create Render Account
1. Go to https://render.com/
2. Sign up or log in
3. Connect your GitHub account

#### Create New Web Service

1. After logging in, click "New +" in the top right
2. Select "Web Service"

#### Configure Web Service

**Step 4.1: Connect Repository**
- Click "Connect" next to your `oracle-bot-v2` repository
- Wait for Render to analyze your repository

**Step 4.2: Configure Build & Runtime**

**Name**: `oracle-bot-v2` (or your preferred name)

**Region**: Choose region closest to your users (e.g., Oregon, Frankfurt)

**Branch**: `main` (or your default branch)

**Runtime**: `Python 3`

**Build Command**:
```
pip install -r requirements.txt
```

**Start Command**:
```
python app.py
```

**Instance Type**: `Free` (for testing) or `Standard` (for production)

**Step 4.3: Add Environment Variable**

1. Scroll down to "Environment Variables"
2. Click "Add Environment Variable"
3. Key: `GROQ_API_KEY`
4. Value: Your actual Groq API key
5. Click "Save"

**Step 4.4: Deploy**

1. Click "Create Web Service" at the bottom
2. Wait for deployment (usually 2-3 minutes)
3. Monitor deployment logs

### Step 5: Verify Deployment

Once deployment is complete:

1. Render will provide a URL like: `https://oracle-bot-v2.onrender.com`
2. Click the URL to access your bot
3. Test the basic flow:
   - Fill in name, gender, birth date
   - Click "Begin Your Oracle Session"
   - Verify greeting appears
   - Send a test message
   - Verify AI responds

### Step 6: Test Enhanced Features

Test the new V2 features:

1. **Full Profile Test**:
   - Fill in all 5 self-discovery questions
   - Add 2-3 relationships
   - Submit and verify greeting mentions profile data

2. **Partial Profile Test**:
   - Fill in only some optional questions
   - Add 1 relationship
   - Verify bot works with partial data

3. **Basic Profile Test**:
   - Only fill required fields (name, gender, DOB)
   - Verify bot works with minimal data

4. **Relationship Calculation Test**:
   - Add relationships with known types
   - Verify greeting mentions relationship types
   - Chat and verify relationships are referenced

## 🔧 Troubleshooting

### Issue: "No such file or directory: templates/index.html"

**Cause**: Incorrect folder structure on GitHub

**Solution**:
1. Delete the repository (or rename it to backup)
2. Create new repository
3. Follow Step 3 exactly - create `templates/index.html` with the slash
4. Verify folder structure on GitHub before deploying

### Issue: Build fails with "ModuleNotFoundError"

**Cause**: Dependencies not installed

**Solution**:
1. Verify `requirements.txt` contains:
   ```
   flask
   flask-cors
   requests
   ```
2. Check build logs for specific error
3. Ensure build command is: `pip install -r requirements.txt`

### Issue: "GROQ_API_KEY not found"

**Cause**: Environment variable not set

**Solution**:
1. Go to your Render service
2. Click "Environment Variables" tab
3. Add `GROQ_API_KEY` with your actual key
4. Redeploy the service

### Issue: "Port already in use" (local testing)

**Cause**: Another service using port 9010

**Solution**:
```bash
# Find process using port 9010
lsof -i :9010

# Kill the process
kill -9 <PID>

# Or use different port
export PORT=9011
python app.py
```

### Issue: AI responses are generic

**Cause**: API key invalid or Groq API down

**Solution**:
1. Verify GROQ_API_KEY is correct
2. Check Groq API status at https://status.groq.com/
3. Check Render logs for API errors
4. Test API key manually using curl

### Issue: Page loads but form doesn't work

**Cause**: JavaScript errors or API route issues

**Solution**:
1. Open browser DevTools (F12)
2. Check Console for errors
3. Check Network tab for failed API calls
4. Verify API routes in app.py match those in index.html

## 📊 Monitoring Your Bot

### Check Render Logs
1. Go to your Render service
2. Click "Logs" tab
3. Monitor for errors or warnings

### Check Service Health
```
curl https://oracle-bot-v2.onrender.com/health
```

Should return:
```json
{
  "status": "healthy",
  "service": "oracle-bot-v2"
}
```

### Monitor Usage (Free Tier)
- Free tier: 512MB RAM, 0.1 CPU
- Limited hours per month (750 hours)
- After limit reached, service goes to sleep

## 🔄 Updating Your Bot

When making changes:

1. Update files locally
2. Commit and push to GitHub
3. Render auto-detects changes and redeploys
4. Monitor deployment logs

### Manual Redeploy
If auto-deploy doesn't trigger:
1. Go to Render service
2. Click "Manual Deploy"
3. Select branch and click "Deploy"

## 💰 Cost Considerations

### Free Tier
- 512MB RAM
- 0.1 CPU
- 750 hours/month
- Good for testing and development

### Paid Tier
- Standard: $7/month (2GB RAM, 1 CPU)
- Pro: $25/month (4GB RAM, 2 CPU)
- Better for production usage

### Groq API Costs
- Groq offers free tier with generous limits
- Monitor usage at https://console.groq.com/
- Set up alerts if needed

## 🔒 Security Best Practices

1. **Never commit API keys** to GitHub
2. Use environment variables for sensitive data
3. Keep dependencies updated
4. Monitor logs for suspicious activity
5. Use HTTPS only (Render provides this automatically)

## 🎯 Post-Deployment Checklist

- [ ] Bot is accessible at the Render URL
- [ ] Basic profile flow works
- [ ] Full profile intake works
- [ ] Relationship calculations are accurate
- [ ] AI responds to messages
- [ ] Integration analysis appears in responses
- [ ] Relationships are referenced appropriately
- [ ] CA references are sparse (1 per 5-7 messages)
- [ ] No errors in Render logs
- [ ] Performance is acceptable

## 📞 Getting Help

If you encounter issues:

1. Check this guide's troubleshooting section
2. Review Render logs
3. Check Groq API status
4. Verify all files are uploaded correctly
5. Test locally first, then deploy

## 🎉 Success!

Your Oracle Bot V2 is now live! Users can:
- Create comprehensive profiles
- Get integration level analysis
- Receive gravitor pattern insights
- Add relationship information
- Get personalized coaching with AI

Monitor usage and iterate based on user feedback. Good luck!

---

**Additional Resources**:
- Render Documentation: https://render.com/docs
- Groq API Documentation: https://console.groq.com/docs
- Flask Documentation: https://flask.palletsprojects.com/