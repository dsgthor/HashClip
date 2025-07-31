# Pasteboard Poison Protection - Firefox Extension

A Firefox extension that detects when copied data is silently changed by malware before pasting. Protects crypto wallets, banking info, and sensitive data from clipboard hijacking attacks.

## Features

- **Real-time Clipboard Monitoring**: Monitors all copy/paste operations across all websites
- **Hash-based Detection**: Uses SHA-256 hashing to detect content changes
- **Similarity Analysis**: Uses Levenshtein distance algorithm to avoid false positives
- **Visual Alerts**: Shows browser notifications and page overlays when threats are detected
- **Privacy Focused**: Only stores hashes, never actual clipboard content
- **Configurable Sensitivity**: Adjustable detection threshold for different use cases
- **Security Statistics**: Track copies monitored and threats detected

## How It Works

1. **Copy Detection**: When you copy text (Ctrl+C), the content script captures the copy event and creates a SHA-256 hash
2. **Hash Storage**: The background script stores the hash with a timestamp for short-term comparison
3. **Paste Analysis**: When you paste text (Ctrl+V), the content script compares the pasted content with stored hashes
4. **Threat Detection**: If content differs significantly (using Levenshtein distance), the extension alerts you
5. **Visual Feedback**: Threat notifications appear as page overlays and browser notifications

## Installation

### Loading the Extension in Firefox

1. Download and extract the extension files
2. Open Firefox and navigate to `about:debugging`
3. Click "This Firefox" in the left sidebar
4. Click "Load Temporary Add-on..."
5. Select the `manifest.json` file from the extracted folder
6. The extension is now active and will appear in your browser toolbar

### Permanent Installation

To install permanently:
1. Package the extension files into a `.zip` file
2. Sign the extension with Mozilla's Add-on signing service
3. Install the signed `.xpi` file

## Usage

### Basic Operation
- The extension works automatically once installed
- Copy any text and the extension will monitor it
- Paste the text - if it has been modified, you'll see an alert
- Click the extension icon to view statistics and settings

### Settings
- **Sensitivity Threshold**: Adjust how similar content must be (50-99%)
- **Hash Expiry**: How long to store clipboard hashes (1-30 minutes)
- **Protection Toggle**: Enable/disable clipboard monitoring

### What Gets Protected
- Cryptocurrency wallet addresses
- Bank account numbers
- Passwords and sensitive text
- URLs and links
- Any copied text content

## Security Features

- **Hash-Only Storage**: Never stores actual clipboard content, only SHA-256 hashes
- **Automatic Cleanup**: Hashes expire automatically after set time period
- **No External Requests**: All processing happens locally in your browser
- **Minimal Permissions**: Only requests necessary clipboard and notification permissions

## Technical Details

### Architecture
- **Content Script**: Monitors copy/paste events on web pages
- **Background Script**: Manages hash storage and threat detection
- **Popup Interface**: Provides user controls and statistics
- **Levenshtein Algorithm**: Calculates string similarity to reduce false positives

### Permissions Required
- `clipboardRead`: Read clipboard content for comparison
- `clipboardWrite`: Clear clipboard as security measure when threats detected
- `notifications`: Show threat alerts to user
- `activeTab`: Monitor clipboard events on current tab
- `storage`: Store settings and statistics locally

### Browser Compatibility
- Firefox 57+ (Quantum)
- Based on WebExtensions API
- Uses modern JavaScript (ES6+)
- WebCrypto API for secure hashing

## Development

### File Structure
```
pasteboard-poison-protection-firefox/
├── manifest.json          # Extension manifest
├── background.js          # Background script for hash management
├── content.js            # Content script for clipboard monitoring
├── levenshtein.js        # String similarity algorithm
├── popup.html            # Popup interface HTML
├── popup.css             # Popup interface styles
├── popup.js              # Popup interface logic
└── README.md             # This file
```

### Building from Source
1. Clone or download the source files
2. Ensure all files are in the same directory
3. Load the extension in Firefox using `about:debugging`
4. Test functionality on various websites

### Debugging
- Open browser console to see clipboard monitoring logs
- Background script logs appear in the extension debugging console
- Content script logs appear in the page console

## Threat Detection Examples

### Cryptocurrency Wallet Hijacking
```
Original: 1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa
Hijacked: 1BvBMSEYstWetqTFn5Au4m4GFg7xJaNVN2
Result: 🚨 Clipboard hijack detected (2.4% similarity)
```

### Banking Information
```
Original: Account: 1234567890
Hijacked: Account: 0987654321
Result: 🚨 Clipboard hijack detected (60% similarity)
```

### URL Manipulation
```
Original: https://mybank.com/login
Hijacked: https://mybank-secure.com/login
Result: 🚨 Clipboard hijack detected (85% similarity)
```

## Known Limitations

- Cannot detect clipboard changes made by system-level malware before the copy event
- Browser security policies limit clipboard access in some contexts
- May show false positives with rich text formatting changes
- Requires active tab focus for some clipboard operations

## Privacy Policy

This extension:
- **Does NOT** send any data to external servers
- **Does NOT** store actual clipboard content
- **Only stores** SHA-256 hashes temporarily (max 30 minutes)
- **Operates** entirely within your browser
- **Respects** user privacy and data security

## Security Considerations

- Hashes are automatically cleaned up to prevent long-term storage
- Extension works offline - no network requests required
- Uses cryptographically secure SHA-256 hashing
- Minimal attack surface with limited permissions

## Contributing

This extension is provided as-is for educational and security purposes. Feel free to:
- Report bugs and security issues
- Suggest improvements
- Fork and modify for your needs
- Submit pull requests with enhancements

## License

This project is released under the MIT License. See the license terms for full details.

## Disclaimer

This extension provides additional security but should not be your only defense against malware. Always:
- Use reputable antivirus software
- Keep your browser and extensions updated
- Verify sensitive information before pasting
- Use multi-factor authentication where possible

---

**Stay safe and protect your clipboard!** 🛡️
