# Contributing to Pasteboard Poison Protection

Thank you for your interest in contributing to Pasteboard Poison Protection! This document provides guidelines and information for contributors.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [How to Contribute](#how-to-contribute)
- [Coding Standards](#coding-standards)
- [Testing Guidelines](#testing-guidelines)
- [Security Considerations](#security-considerations)
- [Submitting Changes](#submitting-changes)

## Code of Conduct

This project adheres to a code of conduct that we expect all contributors to follow:

- Be respectful and inclusive in all interactions
- Focus on constructive feedback and discussions
- Respect differing viewpoints and experiences
- Show empathy towards other community members
- Accept responsibility and apologize for mistakes

## Getting Started

### Prerequisites

- Firefox 57+ (Firefox Quantum)
- Basic knowledge of JavaScript, HTML, and CSS
- Understanding of WebExtensions API
- Familiarity with Git and GitHub workflows

### Development Environment

1. **Fork the Repository**
   ```bash
   git clone https://github.com/yourusername/pasteboard-poison-protection-firefox.git
   cd pasteboard-poison-protection-firefox
   ```

2. **Load Extension in Firefox**
   - Open Firefox and navigate to `about:debugging`
   - Click "This Firefox" in the left sidebar
   - Click "Load Temporary Add-on..."
   - Select the `manifest.json` file

3. **Enable Developer Tools**
   - Browser Console: `Ctrl+Shift+J` (Windows/Linux) or `Cmd+Option+J` (Mac)
   - Extension Debugging: Available in `about:debugging`

## Development Setup

### File Structure Understanding

```
pasteboard-poison-protection-firefox/
├── manifest.json          # Extension configuration
├── background.js          # Background service worker
├── content.js            # Content script for page interaction
├── levenshtein.js        # String similarity algorithm
├── popup.html            # Extension popup interface
├── popup.css             # Popup styling
├── popup.js              # Popup functionality
├── icons/                # Extension icons (if added)
└── docs/                 # Documentation files
```

### Key Components

1. **Background Script** (`background.js`)
   - Manages clipboard hash storage
   - Handles cross-tab communication
   - Processes threat detection logic

2. **Content Script** (`content.js`)
   - Monitors copy/paste events
   - Displays threat notifications
   - Communicates with background script

3. **Popup Interface** (`popup.html`, `popup.js`, `popup.css`)
   - User settings and configuration
   - Statistics display
   - Enable/disable functionality

## How to Contribute

### Types of Contributions

We welcome various types of contributions:

- **Bug Reports**: Report issues you encounter
- **Feature Requests**: Suggest new functionality
- **Code Contributions**: Submit bug fixes or new features
- **Documentation**: Improve or expand documentation
- **Testing**: Help test the extension on different systems
- **Security Reviews**: Audit code for security vulnerabilities

### Finding Issues to Work On

- Check the [Issues](https://github.com/yourusername/pasteboard-poison-protection-firefox/issues) page
- Look for issues labeled `good first issue` or `help wanted`
- Review the project roadmap for planned features

## Coding Standards

### JavaScript Style Guide

- Use ES6+ features where supported
- Follow consistent indentation (2 spaces)
- Use meaningful variable and function names
- Add comments for complex logic
- Avoid global variables

### Example Code Style

```javascript
// Good: Clear, descriptive function name
async function calculateContentSimilarity(original, current) {
  if (!original || !current) {
    return 0;
  }
  
  const distance = levenshteinDistance(original, current);
  const maxLength = Math.max(original.length, current.length);
  
  return ((maxLength - distance) / maxLength) * 100;
}

// Good: Proper error handling
try {
  const result = await browser.storage.local.get(['settings']);
  return result.settings || defaultSettings;
} catch (error) {
  console.error('Failed to load settings:', error);
  return defaultSettings;
}
```

### HTML/CSS Guidelines

- Use semantic HTML elements
- Follow BEM methodology for CSS classes
- Ensure accessibility with proper ARIA labels
- Use responsive design principles

### Commit Message Format

Follow conventional commit format:

```
type(scope): description

[optional body]

[optional footer]
```

Types:
- `feat`: New features
- `fix`: Bug fixes
- `docs`: Documentation changes
- `style`: Code formatting changes
- `refactor`: Code restructuring
- `test`: Adding or updating tests
- `security`: Security-related changes

Examples:
```
feat(detection): add support for rich text clipboard content
fix(popup): resolve settings not saving properly
docs(readme): update installation instructions
security(hash): implement secure hash comparison
```

## Testing Guidelines

### Manual Testing Checklist

Before submitting changes, test the following scenarios:

#### Basic Functionality
- [ ] Extension loads without errors
- [ ] Copy operation creates hash
- [ ] Paste operation compares content
- [ ] Settings are saved and loaded correctly
- [ ] Statistics are updated properly

#### Threat Detection
- [ ] Detects significant content changes
- [ ] Shows appropriate notifications
- [ ] Configurable sensitivity works
- [ ] No false positives for identical content

#### Cross-Browser Testing
- [ ] Firefox 57+ compatibility
- [ ] Different operating systems (Windows, macOS, Linux)
- [ ] Various website contexts

#### Security Testing
- [ ] No sensitive data stored in clear text
- [ ] Hashes expire as configured
- [ ] No memory leaks from long-term usage

### Automated Testing

Currently, the project uses manual testing. We welcome contributions to add:
- Unit tests for core functions
- Integration tests for extension APIs
- Performance tests for large clipboard content

## Security Considerations

### Security-First Development

This is a security-focused extension. All contributions must consider:

1. **Data Privacy**
   - Never store actual clipboard content
   - Use secure hashing algorithms
   - Implement proper data cleanup

2. **Threat Model**
   - Consider attack vectors
   - Validate all inputs
   - Handle edge cases securely

3. **Code Review Focus**
   - Review all clipboard access
   - Verify hash implementations
   - Check for timing attacks

### Reporting Security Issues

If you discover security vulnerabilities:

1. **DO NOT** create a public issue
2. Email security concerns to: [security@yourproject.com]
3. Include detailed reproduction steps
4. Allow time for assessment and patching

## Submitting Changes

### Pull Request Process

1. **Create Feature Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make Changes**
   - Follow coding standards
   - Add appropriate tests
   - Update documentation if needed

3. **Test Thoroughly**
   - Manual testing checklist
   - Cross-browser validation
   - Security review

4. **Commit Changes**
   ```bash
   git add .
   git commit -m "feat(scope): your descriptive message"
   ```

5. **Push and Create PR**
   ```bash
   git push origin feature/your-feature-name
   ```

6. **PR Description Template**
   ```markdown
   ## Description
   Brief description of changes
   
   ## Type of Change
   - [ ] Bug fix
   - [ ] New feature
   - [ ] Documentation update
   - [ ] Security improvement
   
   ## Testing
   - [ ] Manual testing completed
   - [ ] Cross-browser testing done
   - [ ] Security review performed
   
   ## Screenshots/Demos
   (If applicable)
   ```

### Review Process

1. **Automated Checks**: Basic linting and compatibility
2. **Code Review**: Maintainer review for quality and security
3. **Testing**: Additional testing by maintainers
4. **Approval**: Final approval and merge

### After Submission

- Respond to review feedback promptly
- Make requested changes in the same branch
- Be patient during the review process
- Thank reviewers for their time

## Development Resources

### Useful Links

- [WebExtensions API Documentation](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions)
- [Firefox Extension Workshop](https://extensionworkshop.com/)
- [Clipboard API Documentation](https://developer.mozilla.org/en-US/docs/Web/API/Clipboard_API)
- [SHA-256 Implementation Guide](https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto)

### Community

- GitHub Discussions: For questions and general discussion
- Issues: For bug reports and feature requests
- Pull Requests: For code contributions

## Recognition

Contributors will be acknowledged in:
- CONTRIBUTORS.md file
- Release notes for significant contributions
- Special recognition for security improvements

Thank you for contributing to Pasteboard Poison Protection! Together, we can make clipboard security accessible to everyone.
