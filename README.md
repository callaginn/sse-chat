# SSE Real-time Messenger
A real-time chat application using Server-Sent Events (SSE) for instant message delivery.

## 🎯 Quick Start

1. **Setup**: Follow [SETUP.md](SETUP.md) to configure DDEV
2. **Access**: http://sse.ddev.site

## 📁 Project Structure

```
sse-chat/
├── public/
│   ├── index.php           # Main chat interface
│   ├── sse-server.php      # SSE event stream
│   ├── receiver.php        # Message receiver endpoint
│   ├── assets/             # CSS and JavaScript
│   └── data/
│       └── messages.json   # Message storage
├── .ddev/                  # DDEV configuration
└── SETUP.md                # Setup and testing guide
```

## 🚀 How It Works

**Real-time Messenger:**
- Multi-user chat application using SSE
- Messages stored in `messages.json` with full history
- Each tab has unique identity (via sessionStorage)
- Real-time message broadcasting to all connected clients

**Pros:**
- ✅ Real-time updates (< 100ms)
- ✅ Persistent message history
- ✅ Multiple users/tabs support
- ✅ Modern, sleek UI with gradients
- ✅ Automatic reconnection
- ✅ Message delivery tracking

**Best for:** Real-time chat, collaboration tools, live messaging demos

## 🔧 How SSE Works

1. **Client connects** to `sse-server.php` via `EventSource`
2. **Server sends events** using `text/event-stream` format
3. **Browser receives** real-time updates without polling
4. **Heartbeat** keeps connection alive (every 2.5 seconds)
5. **Messages broadcast** to all connected clients instantly

### SSE Event Types

- `connected` - Initial connection established
- `message` - New message received (triggers display)
- `heartbeat` - Keep-alive signal

### Heartbeat Explained

The heartbeat (every 2.5 seconds) serves multiple purposes:
- Keeps connection alive through proxies
- Detects disconnections
- Prevents network timeouts
- Confirms server is responsive


### Heartbeat Explained

The heartbeat (every 2.5 seconds) serves multiple purposes:
- Keeps connection alive through proxies
- Detects disconnections
- Prevents network timeouts
- Confirms server is responsive

## 🎨 Customization

### Message History Limit

Edit `public/sse-server.php` to change the maximum number of stored messages:
```php
$maxMessages = 100; // Change this value
```

### Polling Interval

Edit `public/sse-server.php` to adjust check frequency:
```php
usleep(500000); // 0.5 seconds (500ms)
```

### Styling

Customize the appearance in `public/assets/styles.css`.
