# DDEV Setup Guide

## Prerequisites

Make sure you have DDEV installed:

```bash
brew install ddev
```

## Setup Steps

### 1. Start DDEV

```bash
ddev start
```

### 2. Access Your Site

- **Main Site**: https://sse.ddev.site

The site will be available at the DDEV URL. DDEV automatically handles:
- Virtual host configuration
- SSL certificates
- PHP-FPM configuration
- Apache configuration

## Project Configuration

The DDEV project is configured with:
- PHP 8.2
- Apache with PHP-FPM
- Document root: `public/`
- PHP configuration optimized for SSE (in `.ddev/php/`)

## Useful Commands

```bash
# Start DDEV
ddev start

# Stop DDEV
ddev stop

# Restart DDEV
ddev restart

# Check DDEV status
ddev describe

# View logs
ddev logs

# SSH into container
ddev ssh

# Run PHP commands
ddev exec php -v
ddev exec php -m  # List loaded modules
```

## Troubleshooting

### SSE Connection Failed

**Check DDEV is running:**
```bash
ddev describe
```

**View error logs:**
```bash
ddev logs
```

**Restart DDEV:**
```bash
ddev restart
```

### Updates Not Detected

**Check file permissions:**
```bash
ddev exec ls -la /var/www/html/public/data/messages.json
```

**Test SSE server directly:**
```bash
curl https://sse.ddev.site/sse-server.php
```

**Check message storage:**
```bash
ddev exec cat /var/www/html/public/data/messages.json
```
