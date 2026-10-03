# Prescripto Appointment Platform

Prescripto is a doctor appointment booking platform with three applications: a patient-facing website, an administration dashboard, and an Express API. The API stores data in MongoDB, uses Cloudinary for image uploads, and supports payment integrations.

## Project Structure

- `frontend/` - React and Vite application for patients to find doctors, manage profiles, and book appointments.
- `admin/` - React and Vite dashboards for administrators and doctors to manage doctors, appointments, and profiles.
- `backend/` - Express API with MongoDB models, authentication, appointment management, image upload, and payment integrations.

## Requirements

- Node.js and npm
- A MongoDB connection string
- Cloudinary credentials for image upload features
- Payment provider credentials if using online payments

## Configuration

Create `backend/.env` from the example file and set your credentials:

```dotenv
cd backend
cp .env.example .env
```

Set `MONGODB_URI` to the MongoDB deployment base URI; the backend connects to the `prescripto` database. Keep secrets out of source control. Payment credentials are only needed for the corresponding payment flow.

Create `.env` in both `frontend/` and `admin/` from their example files:

```dotenv
cd frontend && cp .env.example .env
cd ../admin && cp .env.example .env
```

The Vite variables are exposed to the browser. Do not put private keys or secrets in either frontend environment file. Configure the backend URL and currency as needed for each app.

## Run Locally

Install dependencies and start the API:

```sh
cd backend
npm install
npm run server
```

In another terminal, start the patient website:

```sh
cd frontend
npm install
npm run dev
```

In a third terminal, start the admin and doctor dashboard:

```sh
cd admin
npm install
npm run dev
```

Vite prints the local URLs for the frontend applications. The API listens on port `4000` by default, or on the port configured with `PORT`.

## Production Builds

Build either frontend from its directory:

```sh
npm run build
```

Preview a production build with:

```sh
npm run preview
```

The backend can be started with `npm start` from `backend/`. Deploy the three applications separately and set their environment variables in the respective hosting environments.

## API Routes

The backend groups its routes under these prefixes:

- `/api/user` - patient registration, authentication, profile, and appointments.
- `/api/doctor` - doctor authentication, profile, appointments, and dashboard data.
- `/api/admin` - administrator authentication and platform management.
- `/` - API health response (`API Working`).

## Linting

Run the frontend lint checks from either `frontend/` or `admin/`:

```sh
npm run lint
```
