# Two Monks Consulting - Task Management App

A modern, feature-rich task management application built for Two Monks Consulting, integrated with Supabase for real-time data persistence.

## Features

- **Multi-Column Task Organization**: Create custom categories (e.g., Household, Work, Family)
- **Task Assignment**: Assign tasks to specific people
- **Due Dates**: Set and track due dates for each task
- **Completion Tracking**: Mark tasks as complete with separate completed tasks view
- **Auto-Expanding Text Fields**: Task titles expand as you type
- **Real-time Sync**: All data syncs with Supabase database
- **Responsive Design**: Works on desktop and mobile devices
- **Two Monks Consulting Branding**: Clean white/blue theme matching the company website

## Tech Stack

- **Frontend**: HTML, CSS, JavaScript (Vanilla)
- **Database**: Supabase (PostgreSQL)
- **Typography**: Poppins font family
- **Design**: Custom CSS with Two Monks Consulting brand colors

## Database Schema

### Tables

**columns** (categories)
- `id`: bigint (primary key)
- `name`: text
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

## Setup

1. Clone this repository
2. Open `index.html` in a web browser
3. The app will automatically connect to the Supabase database

## Usage

### Managing Categories
- Add a new category using the input field in the header
- Rename a category by clicking the edit (✏️) button
- Delete a category by clicking the delete (🗑️) button

### Managing Tasks
- Add tasks by filling out the form in each category column
- Enter task title, assignee, and due date
- Press Enter or click "Add Task" to save
- Check the checkbox to mark a task as complete
- Delete tasks using the delete button

### Completed Tasks
- Completed tasks appear in the "Completed Tasks" section at the bottom
- Restore tasks by clicking the restore (↩️) button
- Permanently delete completed tasks individually or clear all at once

## Supabase Configuration

The app is pre-configured to connect to the Two Monks Consulting Supabase project. The connection details are embedded in `index.html`.

## License

© 2025 Two Monks Consulting LLC

## Contact

For questions or support, visit [Two Monks Consulting](https://www.twomonksconsulting.com)
