
# Next - A simple but complete authentication service
<!-- Table of Contents -->
<details>

<summary>

# :notebook_with_decorative_cover: Table of Contents

</summary>

- [Folder Structure](#file_folder-folder-structure)
- [Getting Started](#toolbox-getting-started)
- [Tech Stack](#gear-tech-stack)
- [Learn More](#books-learn-more)
- [Deploy on Vercel](#page_with_curl-deploy-on-vercel)

</details>

## :file_folder: Folder Structure
<details>

<summary>Here is the folder structure of this app.</summary>

```bash
auth-next
├── components.json
├── LICENSE
├── next.config.mjs
├── next-env.d.ts
├── package.json
├── pnpm-lock.yaml
├── postcss.config.mjs
├── prisma
│   └── schema.prisma
├── public
├── README.md
├── src
│   ├── actions
│   │   ├── admin.ts
│   │   ├── login.ts
│   │   ├── logout.ts
│   │   ├── new-password.ts
│   │   ├── new-verification.ts
│   │   ├── register.ts
│   │   ├── reset.ts
│   │   └── settings.ts
│   ├── app
│   │   ├── api
│   │   │   ├── admin
│   │   │   │   └── route.ts
│   │   │   └── auth
│   │   │       └── [...nextauth]
│   │   │           └── route.ts
│   │   ├── auth
│   │   │   ├── error
│   │   │   │   └── page.tsx
│   │   │   ├── layout.tsx
│   │   │   ├── login
│   │   │   │   └── page.tsx
│   │   │   ├── new-password
│   │   │   │   └── page.tsx
│   │   │   ├── new-verification
│   │   │   │   └── page.tsx
│   │   │   ├── register
│   │   │   │   └── page.tsx
│   │   │   └── reset
│   │   │       └── page.tsx
│   │   ├── favicon.ico
│   │   ├── globals.css
│   │   ├── layout.tsx
│   │   ├── page.tsx
│   │   └── (protected)
│   │       ├── admin
│   │       │   └── page.tsx
│   │       ├── client
│   │       │   └── page.tsx
│   │       ├── layout.tsx
│   │       ├── server
│   │       │   └── page.tsx
│   │       └── settings
│   │           ├── navbar.tsx
│   │           └── page.tsx
│   ├── auth.config.ts
│   ├── auth.ts
│   ├── components
│   │   ├── auth
│   │   │   ├── back-button.tsx
│   │   │   ├── card-wrapper.tsx
│   │   │   ├── error-card.tsx
│   │   │   ├── header.tsx
│   │   │   ├── login-button.tsx
│   │   │   ├── login-form.tsx
│   │   │   ├── logout-button.tsx
│   │   │   ├── new-password-form.tsx
│   │   │   ├── new-verificaiton-form.tsx
│   │   │   ├── register-form.tsx
│   │   │   ├── reset-form.tsx
│   │   │   ├── role-gate.tsx
│   │   │   ├── social.tsx
│   │   │   └── user-button.tsx
│   │   ├── form-error.tsx
│   │   ├── form-success.tsx
│   │   ├── ui
│   │   │   ├── avatar.tsx
│   │   │   ├── badge.tsx
│   │   │   ├── button.tsx
│   │   │   ├── card.tsx
│   │   │   ├── dialog.tsx
│   │   │   ├── dropdown-menu.tsx
│   │   │   ├── form.tsx
│   │   │   ├── input.tsx
│   │   │   ├── label.tsx
│   │   │   ├── select.tsx
│   │   │   ├── sonner.tsx
│   │   │   └── switch.tsx
│   │   └── user-info.tsx
│   ├── data
│   │   ├── account.ts
│   │   ├── password-reset-token.ts
│   │   ├── tokens.ts
│   │   ├── two-factor-confirmation.ts
│   │   ├── two-factor-token.ts
│   │   ├── user.ts
│   │   └── verification-token.ts
│   ├── hooks
│   │   ├── use-current-role.ts
│   │   └── use-current-user.ts
│   ├── lib
│   │   ├── auth.ts
│   │   ├── mail.ts
│   │   ├── prisma.ts
│   │   └── utils.ts
│   ├── middleware.ts
│   ├── next-auth.d.ts
│   ├── routes.ts
│   └── schemas
│       └── index.ts
├── tailwind.config.ts
└── tsconfig.json
```
</details>

## :toolbox: Getting Started

1. Make sure **Git** and **NodeJS** is installed.
2. Clone this repository to your local computer.
3. Create `.env` file in root directory.
4. Contents of `.env`:
```bash
# .env

# neon postgresql db
DATABASE_URL="postgresql://<username>:<password>@<host>:<port>/auth-next?sslmode=require&pgbouncer=true"

# random auth secret (https://generate-secret.vercel.app/32)
AUTH_SECRET="xxxxxxxxxxxxxxxxxxxxxxxxxx"

# next auth base url
NEXT_PUBLIC_APP_URL=http://localhost:3000

# github auth keys
GITHUB_CLIENT_ID=xxxxxxxxxxxxxx
GITHUB_CLIENT_SECRET=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

# google auth keys
GOOGLE_CLIENT_ID=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.apps.googleusercontent.com
GOOGLE_CLIENT_SECRET=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

# resend api key
RESEND_API_KEY=re_XXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```

5. Set up a Neon PostgreSQL Database

  1. **Obtain PostgreSQL Database URL:**

   - If you don't have a Neon PostgreSQL database, create one.
   - Obtain the database URL, which typically looks like `postgresql://<username>:<password>@<host>:<port>/<database-name>`.

1. **Update `.env` with Database Configuration:**

   - Open your `.env` file.
   - Update the following variables with your Neon PostgreSQL database information:

     ```bash
     # .env

     # Neon PostgreSQL db
     DATABASE_URL="postgresql://<your-neondb-username>:<your-neondb-password>@<your-neondb-host>:<your-neondb-port>/auth-next?sslmode=require&pgbouncer=true"
     ```

1. Generate Authentication Secret

1. **Generate Random Authentication Secret:**

   - Visit [generate-secret.vercel.app](https://generate-secret.vercel.app/32).
   - Copy the generated secret.

1. **Update `.env` with Authentication Secret:**

   - Open your `.env` file.
   - Update the `AUTH_SECRET` variable with the generated secret:

     ```bash
     # .env

     # Random auth secret
     AUTH_SECRET="xxxxxxxxxxxxxxxxxxxxxxxxxx"
     ```

1. Configure NextAuth Base URL

1. **Set NextAuth Base URL:**

   - Open your `.env` file.
   - Set the `NEXT_PUBLIC_APP_URL` variable to the base URL of your Next.js application:

     ```bash
     # .env

     # NextAuth base URL
     NEXT_PUBLIC_APP_URL=http://localhost:3000
     ```

1. Obtain GitHub Authentication Keys

1. **Register Application on GitHub:**

   - Go to the [GitHub Developer Settings](https://github.com/settings/developers) and register a new OAuth application.
   - Obtain the client ID and client secret.

1. **Update `.env` with GitHub Keys:**

   - Open your `.env` file.
   - Update the following variables with the obtained GitHub keys:

     ```bash
     # .env

     # GitHub auth keys
     GITHUB_CLIENT_ID=xxxxxxxxxxxxxx
     GITHUB_CLIENT_SECRET=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
     ```

1. Obtain Google Authentication Keys

1. **Register Application on Google Cloud Console:**

   - Go to the [Google Cloud Console](https://console.cloud.google.com/) and create a new project.
   - Enable the "Google+ API" for your project and create credentials to obtain the client ID and client secret.

1. **Update `.env` with Google Keys:**

   - Open your `.env` file.
   - Update the following variables with the obtained Google keys:

     ```bash
     # .env

     # Google auth keys
     GOOGLE_CLIENT_ID=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.apps.googleusercontent.com
     GOOGLE_CLIENT_SECRET=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
     ```

1. Set Up Resend API Key

1. **Obtain Resend API Key and Email:**

   - Obtain an API key and email from Resend for onboarding purposes.

1. **Update `.env` with Resend API Key and Email:**

   - Open your `.env` file.
   - Update the following variables with the obtained Resend API key and email:

     ```bash
     # .env

     # Resend API key and email
     RESEND_API_KEY=re_XXXXXXXXXXXXXXXXXXXXXXXXXXXXX
     ```

1. Open terminal in root directory. Run `npm install --legacy-peer-deps` or `yarn install --legacy-peer-deps`.

1. Now app is fully configured 👍 and you can start using this app using `npm run dev` or `yarn dev`.

**NOTE:** Please make sure to keep your API keys and configuration values secure and do not expose them publicly. <br />
**❗ WARN:** Resend will only works with the email registered. 

## :gear: Tech Stack

[![React JS](https://skillicons.dev/icons?i=react "React JS")](https://react.dev/ "React JS") [![Next JS](https://skillicons.dev/icons?i=next "Next JS")](https://nextjs.org/ "Next JS") [![Typescript](https://skillicons.dev/icons?i=ts "Typescript")](https://www.typescriptlang.org/ "Typescript") [![Tailwind CSS](https://skillicons.dev/icons?i=tailwind "Tailwind CSS")](https://tailwindcss.com/ "Tailwind CSS") [![Vercel](https://skillicons.dev/icons?i=vercel "Vercel")](https://vercel.app/ "Vercel") [![Prisma](https://skillicons.dev/icons?i=prisma "Prisma")](https://prisma.io/ "Prisma")

## :wrench: Stats

[![Stats for Next](/.github/stats.svg "Stats for Next")](https://pagespeed-insights-svg.glitch.me/?url=https://auth-next-sooty.vercel.app/ "Stats for Next")

## :books: Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## :page_with_curl: Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.



<br />
<p align="right">(<a href="#readme-top">back to top</a>)</p>
```
