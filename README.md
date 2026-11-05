
# SmartIntern

SmartIntern is an AI-powered internship recommendation and management platform. It helps students maintain their profiles and resumes, discover relevant internships, track applications, and communicate with recruiters.

## Features

- **Authentication:** Student and recruiter registration, login, and logout.
- **Profile Management:** Create and update student profiles and skills.
- **Resume Management:** Upload PDF resumes, extract resume text, and support resume tailoring.
- **Internship Recommendations:** Recommend internships based on student profiles and skills.
- **Application Tracking:** View and manage internship applications.
- **Recruiter Job Management:** Manage internship and job listings.
- **Inbox and Messaging:** Retrieve contacts and messages and mark messages as read.
- **Recommendation History:** View recommendation activity and history.
- **Database Integration:** PostgreSQL stores relational application data, while MongoDB stores recommendation activity logs.

## Tech Stack

- **Frontend:** Next.js, React, TypeScript, Tailwind CSS
- **Backend:** Next.js API Routes
- **Database:** PostgreSQL and MongoDB
- **Authentication:** JWT-based sessions
- **Resume Processing:** PDF text extraction
- **Development Tools:** Node.js, npm, pgAdmin

## Project Structure

```text
SmartIntern/
├── app/
│   ├── api/
│   │   ├── admin/
│   │   │   └── jobs/
│   │   │       └── route.ts
│   │   ├── applications/
│   │   │   └── route.ts
│   │   ├── auth/
│   │   │   ├── login/
│   │   │   │   └── route.ts
│   │   │   ├── logout/
│   │   │   │   └── route.ts
│   │   │   └── register/
│   │   │       └── route.ts
│   │   ├── inbox/
│   │   │   ├── route.ts
│   │   │   ├── contacts/
│   │   │   │   └── route.ts
│   │   │   └── [id]/
│   │   │       └── read/
│   │   │           └── route.ts
│   │   ├── profile/
│   │   │   └── route.ts
│   │   ├── recommendation-history/
│   │   │   └── route.ts
│   │   ├── recommendations/
│   │   │   └── route.ts
│   │   └── resume/
│   │       ├── tailor/
│   │       │   └── route.ts
│   │       └── upload/
│   │           └── route.ts
│   ├── favicon.ico
│   ├── globals.css
│   ├── layout.tsx
│   └── page.tsx
├── database/
│   ├── advanced_queries.sql
│   ├── feature-upgrade.sql
│   ├── indexes.sql
│   ├── mongodb_aggregation.js
│   ├── smartintern_complete.sql
│   └── views.sql
├── docs/
│   ├── DATABASE_DOCUMENTATION.md
│   ├── ER_DIAGRAM.png
│   └── RELATIONAL_SCHEMA.md
├── lib/
│   ├── db.ts
│   ├── mongodb.ts
│   └── session.ts
├── reprocess-resume.cjs
├── seed-jobs.cjs
├── seed-skills.cjs
├── README-FEATURE-PATCH.md
├── README.md
├── package.json
├── package-lock.json
├── next.config.ts
├── tsconfig.json
└── eslint.config.mjs
```

## Database Design

### PostgreSQL

Database Name: `smartintern_db`

The following tables are used in the relational database:

| Table | Description |
|---|---|
| users | User accounts and roles |
| student_profiles | Student profile information |
| resumes | Uploaded resume details and extracted content |
| skills | Skill master data |
| student_skills | Skills associated with students |
| companies | Company and recruiter information |
| jobs | Internship and job postings |
| job_skills | Skills required for jobs |
| applications | Student internship applications |
| recommendation_runs | Recommendation execution records |
| inbox_messages | Messages between users |

### MongoDB

- **Database:** `smartintern`
- **Collection:** `recommendation_activity_logs`
- **Purpose:** Stores recommendation activity logs.

## Database Files

| File | Description |
|---|---|
| `database/smartintern_complete.sql` | Complete SQL setup script |
| `database/advanced_queries.sql` | Advanced SQL queries |
| `database/indexes.sql` | Database indexes |
| `database/views.sql` | SQL views |
| `database/feature-upgrade.sql` | Database feature upgrade script |
| `database/mongodb_aggregation.js` | MongoDB aggregation queries |
| `docs/ER_DIAGRAM.png` | Entity Relationship Diagram |
| `docs/RELATIONAL_SCHEMA.md` | Relational schema documentation |
| `docs/DATABASE_DOCUMENTATION.md` | Database documentation |

## API Routes

| API Endpoint | Description |
|---|---|
| `/api/auth/register` | Register a user |
| `/api/auth/login` | User login |
| `/api/auth/logout` | User logout |
| `/api/profile` | Manage profile information |
| `/api/resume/upload` | Upload and process resumes |
| `/api/resume/tailor` | Resume tailoring |
| `/api/recommendations` | Get internship recommendations |
| `/api/recommendation-history` | Retrieve recommendation history |
| `/api/applications` | Manage applications |
| `/api/admin/jobs` | Manage internship/job listings |
| `/api/inbox` | Access inbox messages |
| `/api/inbox/contacts` | Retrieve messaging contacts |
| `/api/inbox/[id]/read` | Mark a message as read |

## Getting Started

### Prerequisites

Install the following software:

- Node.js
- npm
- PostgreSQL
- MongoDB or MongoDB Atlas

### 1. Clone the Repository

```bash
git clone https://github.com/pallenenisloka07-lang/SmartIntern.git
cd SmartIntern
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Create a `.env.local` file in the project root.

Add the database and authentication environment variables required by the application.

Example:

```env
DATABASE_URL=postgresql://USER:PASSWORD@HOST:5432/smartintern_db
MONGODB_URI=mongodb+srv://USER:PASSWORD@CLUSTER/smartintern
JWT_SECRET=your_secure_secret
```

**Note:** These are example variable names. Check `lib/db.ts`, `lib/mongodb.ts`, and `lib/session.ts` for the exact environment variable names used by the project.

Never commit `.env.local` or database credentials to GitHub.

### 4. Set Up Databases

1. Create the PostgreSQL database `smartintern_db`.
2. Execute the required SQL scripts from the `database/` folder.
3. Configure the MongoDB database `smartintern`.
4. Ensure the `recommendation_activity_logs` collection is available.
5. Verify database connection settings in `.env.local`.

### 5. Run the Application

Start the development server:

```bash
npm run dev
```

Open the application in your browser:

```text
http://localhost:3000
```

## Useful Commands

```bash
# Start development server
npm run dev

# Build the application
npm run build

# Start production server
npm run start

# Run lint checks
npm run lint
```

Use commands supported by the scripts defined in `package.json`.

## Security

- Never commit `.env.local` or sensitive credentials.
- Use strong and unique JWT secrets.
- Validate and authorize API requests.
- Protect sensitive student and resume information.
- Use secure database credentials.
- Avoid exposing private information in public repositories.

## Future Enhancements

- Improved recommendation accuracy.
- Better recruiter and student dashboards.
- Notification functionality.
- Automated testing.
- Deployment monitoring and optimization.

## Repository

GitHub Repository: [SmartIntern](https://github.com/pallenenisloka07-lang/SmartIntern)
