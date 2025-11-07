# Two Monks Consulting - Task Management App

A modern, secure task management application built for Two Monks Consulting, featuring passwordless email authentication and real-time data persistence with Supabase.

## Features

### Authentication & Security
- **Passwordless Magic Link Authentication**: Secure email-based login with no passwords to remember
- **User Isolation**: Each user's data is completely private and separated using Row Level Security (RLS)
- **Session Management**: Automatic session handling with secure token refresh

### Task Management
- **Multi-Column Organization**: Create custom categories (e.g., Household, Work, Family)
- **Task Assignment**: Assign tasks to specific people
- **Due Dates**: Set and track due dates for each task
- **Completion Tracking**: Mark tasks as complete with automatic timestamping
- **Auto-Expanding Text Fields**: Task titles expand as you type for better visibility
- **Real-time Sync**: All data syncs instantly with Supabase database

### User Experience
- **Responsive Design**: Works seamlessly on desktop and mobile devices
- **Two Monks Consulting Branding**: Clean white/blue theme matching the company website
- **Intuitive Interface**: Simple, elegant UI with smooth animations

## Tech Stack

- **Frontend**: HTML, CSS, JavaScript (Vanilla)
- **Database**: Supabase (PostgreSQL)
- **Authentication**: Supabase Auth with Magic Links
- **Typography**: Poppins font family
- **Design**: Custom CSS with Two Monks Consulting brand colors

## Security Features

### Row Level Security (RLS)
All database tables are protected with RLS policies that ensure:
- Users can only see their own categories and tasks
- Users can only create, update, and delete their own data
- No user can access another user's information

### Authentication Flow
1. User enters their email address
2. Supabase sends a secure magic link to their email
3. User clicks the link to authenticate
4. Session is established with automatic token refresh
5. User can sign out at any time

## Database Schema

### Tables

**columns** (categories)
- `id`: bigint (primary key)
- `name`: text
- `user_id`: uuid (foreign key to auth.users) - **NEW**
- `created_at`: timestamptz

**tasks**
- `id`: bigint (primary key)
- `column_id`: bigint (foreign key to columns)
- `title`: text
- `assigned_to`: text
- `due_date`: date
- `completed`: boolean
- `completed_at`: timestamptz
- `created_at`: timestamptz

### RLS Policies

**Columns Table**:
- Users can only view, insert, update, and delete their own columns
- Policy checks: `auth.uid() = user_id`

**Tasks Table**:
- Users can only access tasks that belong to their columns
- Policy checks: task's column belongs to authenticated user

## Setup

1. Clone this repository:
```bash
git clone https://github.com/karoonsuck/ToDo.git
cd ToDo
```

2. Open `index.html` in a web browser

3. The app will automatically connect to the Supabase database

## Usage

### First Time Users

1. **Sign In**:
   - Enter your email address in the welcome screen
   - Click "Send Magic Link"
   - Check your email for the magic link
   - Click the link to sign in (link expires after a short time for security)

2. **Start Managing Tasks**:
   - Once signed in, you'll see your personalized task dashboard
   - Your email appears in the header
   - All your data is private and secure

### Managing Categories

- **Add**: Enter a category name in the header input and click "+ Add Category"
- **Rename**: Click the edit (✏️) button on any category
- **Delete**: Click the delete (🗑️) button (confirms if tasks exist)

### Managing Tasks

- **Add**: Fill out the form in each category column:
  - Task title (expands as you type)
  - Assignee (optional)
  - Due date (optional)
- **Complete**: Check the checkbox to mark as complete
- **Delete**: Click the delete button (🗑️)
- **Quick Entry**: Press Enter to add a task (Shift+Enter for new line in title)

### Completed Tasks

- View all completed tasks in the "Completed Tasks" section
- **Restore**: Click the restore (↩️) button to move back to active
- **Delete Permanently**: Click the delete button
- **Clear All Completed**: Use the "Clear Completed" button

### Account Management

- **View Email**: Your email is displayed in the header
- **Sign Out**: Click the "Sign Out" button in the header
- **Clear All Data**: Remove all your categories and tasks (requires confirmation)

## Why Magic Links?

We chose passwordless authentication for several reasons:

1. **Better Security**:
   - No passwords to leak or steal
   - No password reuse across sites
   - Eliminates password-based attacks

2. **Better User Experience**:
   - No passwords to remember
   - No password reset flows
   - One-click authentication

3. **Modern Standard**:
   - Used by leading services like Slack, Medium, and Notion
   - Industry best practice for secure authentication

## Privacy & Data

- All user data is stored securely in Supabase
- Each user's tasks are completely isolated
- Data is encrypted in transit and at rest
- No user data is shared or sold
- Users can delete all their data at any time

## Supabase Configuration

The app connects to the Two Monks Consulting Supabase project with:
- Automatic authentication state management
- Row Level Security enforcement
- Real-time data synchronization

## Browser Compatibility

Works on all modern browsers:
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## License

© 2025 Two Monks Consulting LLC

## Contact

For questions or support, visit [Two Monks Consulting](https://www.twomonksconsulting.com)

## Changelog

### Version 2.0 (Current)
- ✅ Added passwordless email authentication
- ✅ Implemented Row Level Security (RLS)
- ✅ User-specific data isolation
- ✅ Session management and sign out
- ✅ Auth modal with loading states
- ✅ Secure magic link flow

### Version 1.0
- Initial release with basic task management
- Multi-column organization
- Task assignment and due dates
- Completion tracking
- Supabase integration
