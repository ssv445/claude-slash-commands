# Claude Commands Directory Specification

## Overview
A simple web directory where users can submit Claude commands (markdown files from public GitHub repositories) and discover commands shared by others. Users can browse, search, and copy commands to use in their Claude setup.

## Core Features

### 1. Command Submission
- Users submit URLs of markdown files or folders from public GitHub repositories
- Submission form requires:
  - GitHub URL (file or folder)
  - Command name
  - Description
  - Categories (select from predefined list)
  - Tags (free-form)
  - Author information
- All submissions are immediately published (no review process)
- Admin can unpublish malicious content if discovered later

### 2. Directory Browsing
- Single page directory listing all commands
- Default sort by install/copy count (popularity)
- Each command shows:
  - Name
  - Description
  - Author
  - Categories
  - Tags
  - Copy count
  - Last updated date
  - "Copy" button

### 3. Discovery Features
- **Categories**: Predefined categories for organization
- **Tags**: Free-form tags for detailed classification
- **Text Search**: Search across command names, descriptions, and content
- **Popularity Metrics**: Track and display copy count

### 4. Command Display
- Show formatted markdown (rendered)
- Prominent "Copy" button to copy entire command content
- Display metadata:
  - Name
  - Description
  - Author
  - Install/copy count
  - Last updated
  - Version
  - Claude version compatibility (if specified)
  - Dependencies on other commands (if any)
  - Source GitHub URL

### 5. Usage Flow
1. User browses/searches directory
2. User finds desired command
3. User clicks "Copy" button
4. User manually creates a new file in their Claude commands folder
5. User pastes the copied content
6. User saves with their preferred filename

## Technical Requirements

### MVP Approach
- Keep architecture simple
- Static site generation preferred for performance
- Minimal backend for:
  - Submission handling
  - Copy count tracking
  - Basic analytics

### Data Model

#### Command Entity
```json
{
  "id": "unique-id",
  "name": "command-name",
  "description": "Brief description",
  "content": "Full markdown content",
  "github_url": "https://github.com/...",
  "author": {
    "name": "Author Name",
    "github": "username",
    "email": "email@example.com"
  },
  "categories": ["category1", "category2"],
  "tags": ["tag1", "tag2", "tag3"],
  "copy_count": 0,
  "created_at": "2024-01-01T00:00:00Z",
  "updated_at": "2024-01-01T00:00:00Z",
  "version": "1.0.0",
  "claude_version": "any",
  "dependencies": [],
  "is_published": true
}
```

### Frontend Requirements
- Responsive design
- Fast load times
- Copy button functionality
- Markdown rendering
- Search/filter interface
- Clean, simple UI

### Backend Requirements
- Handle form submissions
- Fetch content from GitHub
- Track copy counts
- Simple admin interface for unpublishing
- No user authentication needed for MVP
- Email notifications optional

## Future Enhancements (Post-MVP)
- User accounts for tracking submissions
- Command versioning and update notifications
- Comments/ratings system
- AI-powered security scanning
- API for programmatic access
- Command collections/bundles
- Installation tracking vs just copy tracking

## Security Considerations
- Validate GitHub URLs
- Sanitize markdown content
- Rate limiting on submissions
- Admin ability to quickly unpublish
- Monitor for malicious patterns
- Clear reporting mechanism for users

## Success Metrics
- Number of commands submitted
- Copy count per command
- Search usage statistics
- User return rate
- Time to find desired command