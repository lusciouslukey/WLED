# GitHub Secrets Setup Instructions

## ⚠️ IMPORTANT: Security Issue Fixed

Your workflow previously contained hardcoded credentials that were publicly visible. I've updated the workflow to use GitHub Secrets instead.

## Required Actions

### 1. Add Secrets to GitHub Repository

Go to your GitHub repository: https://github.com/lusciouslukey/WLED

Then navigate to: **Settings** → **Secrets and variables** → **Actions** → **New repository secret**

Add the following 5 secrets:

| Secret Name | Value | Description |
|-------------|-------|-------------|
| `CLIENT_SSID` | `Chez-Bennett-IoT` | Your WiFi SSID (or update with new one) |
| `CLIENT_PASS` | `(your password)` | Your WiFi password |
| `WLED_AP_SSID` | `WLED` | WLED Access Point SSID |
| `WLED_AP_PASS` | `(your password)` | WLED Access Point password |
| `DEBUG_HOST` | `10.20.30.100` | Debug host IP address |

**Note:** I've intentionally left the password values blank for you to fill in. Use your actual passwords when adding them to GitHub.

### 2. Steps to Add Each Secret

For each secret above:

1. Click **"New repository secret"**
2. Enter the **Name** (e.g., `CLIENT_SSID`)
3. Enter the **Secret** value
4. Click **"Add secret"**

### 3. Change Your WiFi Password (RECOMMENDED)

Since your WiFi password was exposed in the public repository, I strongly recommend:

1. **Change your WiFi password immediately** for security
2. Update the `CLIENT_PASS` secret in GitHub with the new password
3. Verify no other devices or services depend on the old password

### 4. Test the Workflow

Once all secrets are added:

1. Go to **Actions** tab in your repository
2. Select **"WLED compile"** workflow
3. Click **"Run workflow"** → **"Run workflow"**
4. Wait for the build to complete
5. Download the bin files from the **Artifacts** section

## What Changed

The workflow now:
- ✅ Uses environment variables from GitHub Secrets
- ✅ No longer exposes credentials in the workflow file
- ✅ Uploads bin files as artifacts for easy download
- ✅ Supports both workflow_dispatch (manual) and workflow_call (automatic)

## Verification

After adding secrets, the workflow will:
1. Build 4 firmware variants (dev/master × soundReactive/standard)
2. Upload them as artifacts
3. Commit them to your repository

Your bin files will be available:
- As downloadable artifacts in GitHub Actions
- In the repository root after each successful build

## Need Help?

If you encounter any issues:
1. Verify all 5 secrets are added correctly
2. Check the Actions logs for specific error messages
3. Ensure secret names match exactly (case-sensitive)
