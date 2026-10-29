# 🚀 SparkleLab — AI Image Editing SaaS (Learning Project)

> An educational Next.js SaaS application for learning real-world software engineering workflows including authentication, cloud image processing, API architecture, and production builds.

⚠️ **Credit Notice**: This project is based on educational material from **Adrian Hajdin** at [JavaScript Mastery](https://github.com/adrianhajdin). It has been adapted, debugged, and deployed as part of a hands-on learning journey focused on solving real engineering challenges.

**Repository**: [taiyeba-software/SparkleLab](https://github.com/taiyeba-software/SparkleLab)
**Live Demo**: [add your Vercel link here]

---

## 📋 Table of Contents

1. 🤖 [About](#about)
2. ✨ [Features](#features)
3. 🧠 [Engineering Challenges Solved](#engineering-challenges-solved)
4. ⚙️ [Tech Stack](#tech-stack)
5. 🚀 [Quick Start](#quick-start)
6. 🎯 [Learning Goals](#learning-goals)
7. 🔮 [Roadmap](#roadmap)
8. 📚 [What I Learned](#what-i-learned)
9. 🧾 [What Came From the Tutorial vs. My Work](#tutorial-vs-my-work)
10. ⚠️ [Known Limitations](#known-limitations)

---

## <a name="about">🤖 About</a>

SparkleLab is an MVP (Minimum Viable Product) for an AI-powered image editing SaaS platform. It demonstrates:

- **End-to-end user workflows** from authentication → upload → processing → result
- **Cloud-based image processing** using Cloudinary
- **TypeScript full-stack development** with Next.js (App Router, server actions, API routes)
- **A verified production build** (`npm run build`) with environment configuration
- **Auth-protected routes** using Clerk middleware

### Current Capabilities (MVP):

✅ User authentication via Clerk  
✅ Image upload & storage  
✅ Background removal (Cloudinary AI)  
✅ Community image gallery with pagination  
✅ Image search  
✅ User profile management  

### Planned Features (Locked UI):

🔒 Stripe payment integration  
🔒 Image restoration  
🔒 Generative fill  
🔒 Object removal & recoloring  
🔒 Usage credits system  

---

## ✨ <a name="features">Features</a>

### 📦 Core MVP Features

👉 **Authentication**: Clerk-powered sign-up, sign-in, and session management with protected routes

👉 **Image Upload & Processing**: Drag-drop upload with Cloudinary integration for storage and transformation

👉 **Background Removal**: AI-powered background removal using Cloudinary's transformation capabilities

👉 **Community Gallery**: Browse user transformations with pagination

👉 **Search**: Search images by title or metadata using MongoDB queries

👉 **User Profile**: View user transformation history and account details

👉 **Responsive Design**: Mobile-first UI built with Shadcn/UI + Tailwind CSS

👉 **TypeScript & Validation**: Strict TypeScript with Zod validation for external input

### 🔒 Upcoming (MVP+ Phase)

- Stripe checkout flow
- Image restoration
- Generative fill with AI
- Object removal/recoloring tools
- Credit-based usage system

---

## 🧠 <a name="engineering-challenges-solved">Engineering Challenges Solved</a>

During development, this project ran into real-world engineering issues, which I diagnosed and fixed:

### 🔴 Challenge 1: Environment Configuration

**Problem**: Environment variables not loading correctly, causing `MONGODB_URI === undefined` errors at runtime.

**Solution**:
- Verified `.env.local` naming and key format
- Restarted dev server to reload environment context
- Added fallback env variable handling
- Kept sensitive keys server-only (no `NEXT_PUBLIC_` prefix for secrets)

### 🔴 Challenge 2: MongoDB Connection Pipeline

**Problem**: `querySrv ECONNREFUSED` and DNS resolution failures with MongoDB Atlas.

**Solution**:
- Diagnosed DNS SRV record resolution issues
- Verified MongoDB Atlas IP allowlist configuration
- Tested both SRV and non-SRV connection strings
- Added connection error logging for debugging

### 🔴 Challenge 3: TypeScript Build Failures

**Problem**: Global type discovery failures in `next build` despite development working.

**Solution**:
- Updated `tsconfig.json` to include a proper `types` array
- Created proper `.d.ts` declaration files
- Fixed `next-env.d.ts` auto-generation
- Validated type imports and exports

### 🔴 Challenge 4: API Pipeline Architecture

**Problem**: Initial reliance on external APIs created fragile pipelines; needed abstraction.

**Solution**:
- Integrated Cloudinary directly for image processing
- Used typed server actions for client-server communication
- Added error handling with `handleError` utilities
- Added environment validation at startup

### 📊 Final Result

```bash
✅ npm run build      → Successful production build
✅ npm run dev        → Clean development environment
✅ Auth routes        → Protected with Clerk middleware
✅ Database connect   → Verified at startup
```

---

## <a name="tech-stack">⚙️ Tech Stack</a>

### Frontend
- **Next.js 15.5** - React framework with App Router
- **TypeScript** - Static type safety
- **React Hook Form** - Form management
- **Shadcn/UI** - Accessible component library
- **Tailwind CSS** - Utility-first styling

### Backend
- **Next.js Server Actions & API Routes** - Server-side logic
- **Mongoose** - MongoDB object modeling
- **Zod** - Runtime schema validation

### Infrastructure
- **MongoDB** - NoSQL document database
- **Cloudinary** - Image storage, transformation, and AI
- **Clerk** - Authentication and user management
- **Stripe** - Payment processing (upcoming, locked in the UI)

### Developer Tools
- **ESLint** - Code quality
- **TypeScript** - Type checking
- **Tailwind CSS** - Responsive design system

---

## <a name="quick-start">🚀 Quick Start</a>

### Prerequisites

Ensure you have installed:
- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/en) (v18+)
- [npm](https://www.npmjs.com/)

### Installation

```bash
# Clone repository
git clone https://github.com/taiyeba-software/SparkleLab.git
cd SparkleLab

# Install dependencies
npm install

# Start development server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to see the app.

### Environment Variables

Create `.env.local` in the project root:

```env
# MongoDB
MONGODB_URI=your_mongodb_connection_string

# Cloudinary
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name

# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key

# Server Configuration
NEXT_PUBLIC_SERVER_URL=http://localhost:3000

# Stripe (upcoming)
STRIPE_SECRET_KEY=your_stripe_secret_key
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
```

Never commit `.env.local` or real keys to the repository.

### Running a Production Build

```bash
# Build the application
npm run build

# Start production server
npm start
```

---

## 🎯 <a name="learning-goals">Learning Goals</a>

This project was built to learn and practice:

✅ **Environment configuration** - Managing secrets and build configuration  
✅ **Real-world debugging** - Diagnosing and solving deployment issues  
✅ **TypeScript** - Full-stack type safety from client to server  
✅ **API architecture** - Designing typed server actions and API routes  
✅ **Cloud integration** - Working with Cloudinary, MongoDB, and Clerk  
✅ **Authentication flows** - Implementing user sessions with Clerk  
✅ **Database modeling** - Designing MongoDB schemas with Mongoose  
✅ **Responsive UI** - Building mobile-first interfaces with Tailwind  
✅ **Deployment** - Taking an app from local development to a hosted build  

---

## 🔮 <a name="roadmap">Roadmap</a>

### Phase 1: MVP ✅ (Current)
- [x] User authentication
- [x] Image upload & storage
- [x] Background removal
- [x] Community gallery
- [x] Search functionality
- [x] User profiles

### Phase 2: Payments 🔒 (Locked in the UI)
- [ ] Stripe checkout integration
- [ ] Credit system
- [ ] Transaction tracking
- [ ] Webhook handling

### Phase 3: Advanced Features 📋
- [ ] Image restoration
- [ ] Generative fill
- [ ] Object removal/recoloring
- [ ] Batch processing
- [ ] Export options (PNG, SVG, WebP)

### Phase 4: Optimization 📈
- [ ] Image caching strategy
- [ ] Search indexing
- [ ] Performance monitoring
- [ ] Analytics dashboard

---

## 📚 <a name="what-i-learned">What I Learned</a>

- **Debugging systematically:** change one thing at a time, and check configuration (environment variables, network access, connection strings) before touching code.
- **Environment safety:** which values can be public (`NEXT_PUBLIC_`) and which must stay server-only.
- **Next.js App Router:** how server actions, API routes, layouts and middleware fit together.
- **Build vs. dev differences:** why something can work in `npm run dev` and still fail in `npm run build`, especially with TypeScript.
- **Third-party services:** connecting Clerk (auth), Cloudinary (image processing) and MongoDB Atlas (data) in one app.
- **Working from existing code:** reading a codebase I did not write, finding why it failed, and fixing it layer by layer.

---

## <a name="tutorial-vs-my-work">🧾 What Came From the Tutorial vs. My Work</a>

**From the tutorial (Adrian Hajdin / JavaScript Mastery):** the original application idea, project structure, UI design and core feature set.

**My work:** setting the project up and getting it running, diagnosing and fixing the environment, MongoDB connection and TypeScript build failures described above, deploying it to Vercel, and documenting what broke and how I fixed it.

---

## <a name="known-limitations">⚠️ Known Limitations</a>

- **Stripe/credits are not working yet.** The UI for payments is locked; the schema and structure exist, but I have not completed or tested the payment flow end to end.
- **A few `any` types remain** in the codebase. I plan to replace them with proper types.
- **No automated tests** in this project yet.
- Advanced editing features (restoration, generative fill, object removal) are planned, not built.

---

## 🙏 Credits

This project is based on educational material and architectural guidance from:

**Adrian Hajdin**  
- GitHub: [@adrianhajdin](https://github.com/adrianhajdin)
- YouTube: [JavaScript Mastery](https://www.youtube.com/@javascriptmastery)

All architectural patterns, design decisions, and the initial codebase belong to the original creator. This version includes debugging, adaptation, environment fixes, and deployment practice.

---

## 📝 License

This project is for educational purposes. Please respect the original creator's work.

---

## 🤝 Support

For questions about how the project works or debugging tips:

1. Check the [todo.md](./todo.md) file for known issues and solutions
2. Review environment configuration carefully (most issues are env-related)
3. Verify Cloudinary, MongoDB, and Clerk credentials

---

## 🚀 Deploy

This project is deployed on **Vercel** — [add your live link here].

Environment variables must be set in the deployment platform's secrets manager.
