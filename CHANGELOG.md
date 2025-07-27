# Changelog

All notable changes to Claude Self-Reflect will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.3.0] - Unreleased

### Added
- **Setup Wizard Command-Line Arguments** - Non-interactive installation support
  - `--voyage-key=<key>` for direct API key configuration
  - `--local` flag for local-only mode without semantic search
  - Automatic detection of non-interactive environments (no TTY)
- **Watcher Integration** - Continuous conversation monitoring built into setup
  - Automatic file watching after initial import
  - Real-time conversation indexing
  - Configurable watch intervals
- **System Health Dashboard** - Comprehensive health monitoring (`health-check.sh`)
  - Qdrant status with vector and collection counts
  - MCP server connection status
  - Import queue and last import timing
  - Docker container resource usage
  - Automatic update checking
  - Search performance metrics
- **Enhanced Docker Support**
  - Isolated importer container (`Dockerfile.importer-isolated`)
  - Streaming importer with progress updates (`Dockerfile.streaming-importer`)
  - Watcher container for continuous monitoring (`Dockerfile.watcher`)
  - Optimized docker-compose configurations
- **Python SSL Support** - Improved handling of Python installations
  - Automatic detection of pyenv SSL issues
  - Fallback to Homebrew Python on macOS
  - Clear error messages and remediation steps

### Changed
- **Setup Wizard Improvements**
  - Better error handling for missing dependencies
  - Clearer prompts and user feedback
  - Support for both interactive and non-interactive modes
  - Automatic Python path detection and configuration
- **Documentation Structure**
  - Reorganized docs into logical categories
  - Added troubleshooting guides for common issues
  - Improved installation instructions with platform-specific notes
  - Better examples and use cases
- **Import Process**
  - Streaming import with real-time progress
  - Better handling of large conversation files
  - Improved error recovery and retry logic
  - More efficient vector embedding batch processing

### Fixed
- **Reddit User Feedback Issues**
  - Python SSL module errors with pyenv installations
  - Non-interactive installation failures in CI/CD environments
  - Qdrant health check endpoint (changed from `/health` to `/`)
  - Docker container permission issues on Linux
  - Memory leaks in long-running import processes
- **CI/CD Pipeline**
  - Updated workflows for Python-based structure
  - Fixed test paths and dependencies
  - Added Python version matrix testing (3.10, 3.11, 3.12)
- **Setup Wizard Bugs**
  - Fixed readline interface errors in non-TTY environments
  - Corrected Python path detection on various platforms
  - Improved error messages for missing dependencies

### Security
- Better isolation of import processes using Docker
- Improved handling of API keys and sensitive configuration

## [2.2.1] - 2025-01-25

### Fixed
- NPM package installation issues
- Missing dependencies in package.json

## [2.2.0] - 2025-01-24

### Added
- Voyage AI streaming embeddings support
- Improved import performance (2x faster)
- Better error handling in setup wizard

### Changed
- Default to Voyage AI for better search accuracy
- Simplified installation process

## [2.1.0] - 2025-01-23

### Added
- Support for multiple embedding providers
- Local embedding model option
- Cross-project search functionality

### Fixed
- Memory usage optimization for large conversation sets
- Import speed improvements

## [2.0.1] - 2025-01-22

### Fixed
- CI/CD workflow for Python-based structure
- Updated test configurations
- Fixed directory references in workflows

## [2.0.0] - 2025-01-22

### Changed
- **BREAKING**: Complete restructure from TypeScript to Python MCP server
- **BREAKING**: NPM package now serves as installation wizard only
- **BREAKING**: Renamed MCP from `claude-self-reflection` to `claude-self-reflect`
- Archived TypeScript implementation to `archived/typescript-mcp/`
- Renamed directories for clarity:
  - `claude-reflect` → `mcp-server`
  - `claude_reflect` → `src`
- Simplified configuration structure

### Added
- New installation CLI with interactive setup wizard
- `claude-self-reflect doctor` command for diagnostics
- Python wheel distribution for MCP server
- Comprehensive migration guide

### Removed
- TypeScript MCP server implementation (archived)
- Direct MCP functionality from NPM package

### Migration Guide
Users upgrading from v1.x need to:
1. Uninstall the old package: `npm uninstall -g claude-self-reflection`
2. Install the new package: `npm install -g claude-self-reflect`
3. Run setup wizard: `claude-self-reflect setup`
4. Update Claude Desktop configuration to use `claude-self-reflect` instead of `claude-self-reflection`

## [1.0.0] - 2025-01-14

### 🎉 Initial Release

#### Added
- **One-command installation** - Get up and running in under 5 minutes
- **Semantic search** across all Claude Desktop conversations
- **Continuous import** - Automatically watches for new conversations
- **Multiple embedding providers** - Support for OpenAI, Voyage AI, and local models
- **Cross-project search** - Search across all your Claude projects simultaneously
- **Privacy-first design** - All data stays local, no cloud dependencies
- **MCP-native integration** - Built specifically for Claude Desktop
- **Comprehensive documentation** - Full setup guide and troubleshooting
- **Health monitoring** - Built-in health check and status commands
- **Backup/restore** functionality for data safety
- **Docker-based deployment** for easy setup and isolation

#### Performance
- 66.1% search accuracy with Voyage AI embeddings
- <100ms search latency for 100K+ conversations
- ~1,000 conversations/minute import speed
- ~1GB memory usage per million conversations

#### Supported Platforms
- macOS (Apple Silicon and Intel)
- Linux (Ubuntu 20.04+, Debian 11+)
- Windows (via WSL2)

#### Known Issues
- Large conversation files (>10MB) may slow down initial import
- Search accuracy varies by embedding model choice
- Windows native support requires WSL2

### Migration from Neo4j
If you're migrating from the original Neo4j-based memento-stack:
1. Export your data using the old system's export function
2. Install Claude Self-Reflect
3. Import will automatically process your conversation history
4. All conversation data is preserved with improved search capabilities

---

## Contributing

We welcome contributions! See our [Contributing Guide](CONTRIBUTING.md) for details.

To add to this changelog:
1. Add your changes under the [Unreleased] section
2. Use the appropriate category: Added, Changed, Deprecated, Removed, Fixed, Security
3. Include PR numbers and contributor credits

Example:
```
### Added
- New feature description (#123) - @contributor
```