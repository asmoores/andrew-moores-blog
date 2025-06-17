# Analytics Setup Instructions

Your blog is now ready for Google Analytics 4 tracking. To enable visitor and page view tracking:

## Steps to Set Up Google Analytics 4

1. **Create a Google Analytics account:**
   - Go to https://analytics.google.com/
   - Sign in with your Google account
   - Click "Start measuring"

2. **Set up a property:**
   - Enter your account name
   - Choose your data sharing settings
   - Create a new property for your blog
   - Enter your website name and URL
   - Select your industry category and time zone

3. **Create a Data Stream:**
   - Choose "Web" as your platform
   - Enter your website URL (your final domain)
   - Enter a stream name (e.g., "Blog Website")
   - Click "Create stream"

4. **Get your Measurement ID:**
   - After creating the stream, you'll see a Measurement ID (format: G-XXXXXXXXXX)
   - Copy this ID

5. **Enable tracking in your blog:**
   - Open `hugo.toml` in your blog directory
   - Find the line: `# googleAnalytics = "G-XXXXXXXXXX"`
   - Remove the `#` and replace `G-XXXXXXXXXX` with your actual Measurement ID
   - Example: `googleAnalytics = "G-ABC1234567"`
   - Save the file and rebuild your site with `hugo`

## What You'll Track

Once enabled, Google Analytics will automatically track:
- **Unique visitors** (users who visit your site)
- **Page views** (total number of pages viewed)
- **Sessions** (visit sessions)
- **Bounce rate** (single-page visits)
- **Traffic sources** (how people find your site)
- **Popular pages** (which content performs best)
- **Geographic data** (where your visitors are from)

## Viewing Your Data

- Visit https://analytics.google.com/
- Select your property
- View real-time data in the "Realtime" report
- View historical data in the "Reports" section
- Set up custom dashboards for the metrics you care about most

## Privacy Note

The implementation includes Google Analytics 4, which is designed to be more privacy-conscious than previous versions and complies with GDPR requirements. No additional privacy configuration is needed for basic compliance.