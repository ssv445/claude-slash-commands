# **Claude Slash Commands Directory - MVP PRD**

## **1. Product Overview**

### **Vision**
A simple directory where users can submit Claude commands via GitHub URLs and others can discover and install them.

### **MVP Success Criteria**
- Users can submit GitHub URLs for commands
- Commands get validated and published
- Users can search and install commands
- Basic admin moderation works

## **2. Core User Stories**

### **UC-1: Submit Command**
- **As a** command creator
- **I want to** submit my Claude command GitHub URL
- **So that** others can use it

**Acceptance Criteria:**
- Paste GitHub URL, system validates markdown
- AI checks for safety, auto-approves or flags for review
- Rate limit: 10 submissions/day per user

### **UC-2: Discover & Install Commands**
- **As a** Claude user
- **I want to** find and install commands
- **So that** I can enhance my Claude workflow

**Acceptance Criteria:**
- Browse command list with basic search
- Copy install command: `curl [url] -o ~/.claude-commands/[file].md`
- See command description and usage

### **UC-3: Moderate Content**
- **As an** admin
- **I want to** review flagged commands
- **So that** only safe commands are published

**Acceptance Criteria:**
- View pending commands queue
- Approve/reject with one click
- See AI analysis results

## **3. Minimal Feature Set**

### **3.1 Authentication**
- GitHub OAuth login only
- User profile with basic info
- Admin role for moderation

### **3.2 Command Submission**
- Submit any GitHub URL (auto-convert to raw)
- Markdown validation
- AI safety check (OpenAI integration)
- Auto-approve clean commands, flag suspicious ones

### **3.3 Command Directory**
- List all approved commands
- Basic text search (title + description)
- Command detail page with install instructions
- Install command generation

### **3.4 Admin Interface**
- Pending commands queue
- Approve/reject actions
- User list view
- Basic platform stats

### **3.5 Core Data**
```typescript
// Minimal PayloadCMS Collections
interface User {
  githubId: string
  username: string
  email: string
  role: 'user' | 'admin'
  dailySubmissions: number
}

interface Command {
  title: string
  description: string
  githubUrl: string
  rawUrl: string
  content: string
  submittedBy: User
  status: 'pending' | 'approved' | 'rejected'
  aiSummary: string
  aiFlags?: string[]
}
```

## **4. Technical Requirements**

### **4.1 Stack**
- Next.js + PayloadCMS + MongoDB
- VPS deployment with Docker
- OpenAI for validation

### **4.2 Core APIs**
- `POST /api/commands` - Submit command
- `GET /api/commands` - List approved commands  
- `GET /api/search?q=` - Search commands
- `GET /api/install/:id` - Get install command
- `POST /api/admin/validate/:id` - Approve/reject

## **5. MVP Scope**

### **✅ In Scope**
- Command submission via GitHub URL
- AI validation with manual fallback
- Basic search and discovery
- Simple install command generation
- Admin moderation interface
- GitHub OAuth authentication

### **❌ Out of Scope (Future)**
- Command versioning and auto-sync
- Package/bundle system
- User actions (likes, favorites, reports)
- Advanced search with tags
- User dashboards and analytics
- Complex permission system

## **6. Implementation Plan**

### **Week 1: Foundation**
- VPS setup with Docker
- Next.js + PayloadCMS + MongoDB
- GitHub OAuth integration
- Basic collections and auth

### **Week 2: Core Features**
- Command submission workflow
- AI validation integration
- Admin approval interface
- Command listing and search

### **Week 3: Polish & Launch**
- UI improvements and responsive design
- Install command generation
- Testing and bug fixes
- Production deployment

## **7. Launch Criteria**

### **Functional Requirements**
- [ ] Users can submit GitHub URLs
- [ ] Commands get AI validated automatically
- [ ] Admins can approve/reject flagged commands
- [ ] Users can search and find commands
- [ ] Install commands work correctly
- [ ] All core user flows functional

### **Quality Requirements**
- [ ] No critical bugs in submission flow
- [ ] Search returns relevant results
- [ ] Admin interface fully operational
- [ ] Mobile-responsive design
- [ ] Basic error handling

**Total Timeline: 3 weeks**
**Minimal Viable Product: Ready for community testing**

This MVP focuses on the essential workflow: submit → validate → discover → install. Everything else can be added in future iterations based on user feedback.