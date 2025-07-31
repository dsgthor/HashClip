# Changelog

All notable changes to Pasteboard Poison Protection will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Initial project setup and documentation

### Changed
- Nothing yet

### Deprecated
- Nothing yet

### Removed
- Nothing yet

### Fixed
- Nothing yet

### Security
- Nothing yet

## [1.0.0] - 2024-XX-XX

### Added
- 🛡️ **Core Protection Features**
  - Real-time clipboard monitoring across all websites
  - SHA-256 hash-based content change detection
  - Levenshtein distance algorithm for similarity analysis
  - Visual threat notifications with page overlays
  - Browser notification system for alerts

- 🔧 **User Interface & Settings**
  - Extension popup with statistics dashboard
  - Configurable sensitivity threshold (50-99%)
  - Adjustable hash expiry time (1-30 minutes)  
  - Enable/disable protection toggle
  - Copy and threat detection counters

- 🔒 **Security & Privacy**
  - Hash-only storage (never stores actual clipboard content)
  - Automatic hash cleanup and expiry
  - Local-only processing (no external requests)
  - Minimal permissions model
  - WebCrypto API for secure hashing

- 📱 **Browser Compatibility**
  - Firefox 57+ (Quantum) support
  - WebExtensions API implementation
  - Cross-platform compatibility (Windows, macOS, Linux)
  - Modern JavaScript (ES6+) features

- 🧪 **Detection Capabilities**
  - Cryptocurrency wallet address hijacking
  - Banking information manipulation
  - URL and link modification
  - Password and sensitive text changes
  - Any copied text content alterations

- 📚 **Documentation**
  - Comprehensive README with setup instructions
  - Security-focused architecture documentation
  - Privacy policy and data handling details
  - Threat detection examples and use cases
  - Development and debugging guidelines

### Security
- **Hash Security**: Implemented cryptographically secure SHA-256 hashing
- **Memory Protection**: Automatic cleanup prevents long-term data storage
- **Input Validation**: All clipboard content properly validated
- **Timing Attack Prevention**: Constant-time hash comparisons
- **Minimal Attack Surface**: Limited permissions and local-only operation

---

## Version History Format

Each version entry should follow this structure:

### [Version] - YYYY-MM-DD

#### Added
- New features and capabilities

#### Changed  
- Changes in existing functionality

#### Deprecated
- Soon-to-be removed features

#### Removed
- Now removed features

#### Fixed
- Bug fixes

#### Security
- Security improvements and vulnerability fixes

---

## Release Guidelines

### Version Numbering
- **MAJOR** version: Incompatible API changes
- **MINOR** version: Backwards-compatible functionality additions
- **PATCH** version: Backwards-compatible bug fixes

### Security Releases
Security-related releases will be clearly marked and may include:
- 🔒 **Critical**: Immediate security vulnerabilities
- ⚠️ **High**: Important security improvements  
- 🛡️ **Medium**: Security enhancements
- 📋 **Low**: Security-related maintenance

### Breaking Changes
Breaking changes will be:
- Clearly documented in the changelog
- Announced in advance when possible
- Include migration guidelines
- Provide deprecation warnings in prior versions

---

## Links

- [Unreleased]: https://github.com/yourusername/pasteboard-poison-protection-firefox/compare/v1.0.0...HEAD
- [1.0.0]: https://github.com/yourusername/pasteboard-poison-protection-firefox/releases/tag/v1.0.0

## Contributing

When contributing changes, please:
1. Add entries to the "Unreleased" section
2. Follow the format guidelines above
3. Include issue/PR references where applicable
4. Highlight security-related changes
5. Use clear, user-friendly language

Thank you for helping make Pasteboard Poison Protection better! 🚀