# Packages Directory

This directory contains all the slash command packages available in the Claude Slash Commands Registry.

## Structure

Each command package is stored in its own subdirectory with the following structure:
```
command-name/
├── command.json     # Package metadata
├── command.js       # Main command implementation
├── README.md        # Command documentation
└── tests/          # Optional test files
```

## Contributing

To contribute a new command package:
1. Fork this repository
2. Create a new directory under `packages/` with your command name
3. Add the required files following our package format
4. Submit a Pull Request
5. Our AI analysis system will automatically review your submission

For detailed guidelines, see the [Contributing Guide](../docs/CONTRIBUTING.md).