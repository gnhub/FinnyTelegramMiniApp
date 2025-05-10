# Finny - Telegram Mini App Gaming Platform

Finny is a feature-rich Telegram Mini App gaming platform built with Next.js that allows users to play multiple mini-games, earn points, participate in daily rewards, and manage a virtual wallet. This app is fully customizable and designed to provide an engaging gaming experience within the Telegram platform.

## Project Overview

Finny includes:
- Multiple mini-games (Spin The Wheel, Snake Game, Slot Machine, etc.)
- User profile management
- Points system with farming capabilities
- Daily login rewards and combos
- Referral system
- Wallet functionality
- Admin dashboard
- Firebase backend integration

## Table of Contents
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Firebase Setup](#firebase-setup)
  - [Environment Variables](#environment-variables)
- [Customization Guide](#customization-guide)
  - [Changing App Content](#changing-app-content)
  - [Modifying Games](#modifying-games)
  - [Customizing UI Elements](#customizing-ui-elements)
- [Deployment](#deployment)
- [Project Structure](#project-structure)

## Getting Started

### Prerequisites
- Node.js (v16 or later)
- npm or yarn
- Firebase account
- Telegram Bot Token

### Installation

1. Clone the repository
```bash
git clone <repository-url>
cd finny-gaming-bot
```

2. Install dependencies
```bash
npm install
# or
yarn
```

3. Run the development server
```bash
npm run dev
# or
yarn dev
```

The app will be available at [http://localhost:3000](http://localhost:3000).

### Firebase Setup

1. Create a new Firebase project at [Firebase Console](https://console.firebase.google.com/)
2. Enable Firestore Database
3. Set up Firebase Authentication (if needed)
4. Get your Firebase configuration credentials
5. Update the environment variables with your Firebase credentials

### Environment Variables

Create a `.env.local` file in the root directory with the following variables:

```
NEXT_PUBLIC_API_KEY=your-firebase-api-key
NEXT_PUBLIC_AUTH_DOMAIN=your-firebase-auth-domain
NEXT_PUBLIC_PROJECT_ID=your-firebase-project-id
NEXT_PUBLIC_STORAGE_BUCKET=your-firebase-storage-bucket
NEXT_PUBLIC_MESSAGING_SENDER_ID=your-firebase-messaging-sender-id
NEXT_PUBLIC_APP_ID=your-firebase-app-id
NEXT_PUBLIC_MEASUREMENT_ID=your-firebase-measurement-id
NEXT_PUBLIC_TELEGRAM_BOT_TOKEN=your-telegram-bot-token
```

## Customization Guide

### Changing App Content

Most of the app's content can be modified through files in the `src/data` directory:

#### Home Page (`src/data/homePage.js`)

This file contains:
- Main menu card items (Games, Wallet, Upgrade, Daily Login)
- Farming button text and animations

Example modification:
```javascript
// Change menu items
export const cardItems = [
  {
    href: "/app/games",
    icon: Gamepad2,
    label: "My Games", // Changed from "Games"
  },
  // Add more menu items as needed
];
```

#### Games List (`src/data/games.js`)

This file contains the list of available games with their details:
- Title
- Description
- Image path
- Link to the game

Example modification:
```javascript
export const games = [
  {
    title: "Super Spin Wheel", // Changed name
    description: "Win up to 200 points", // Changed description
    imageSrc: "/image/games/my-custom-image.png", // Changed image
    href: "/app/games/spin-the-wheel",
  },
  // Add more games or modify existing ones
];
```

#### Profile Settings (`src/data/profileSettings.js`)

This file contains the settings menu items with icons and routes.

Example modification:
```javascript
export const profileSettingsItems = [
  {
    name: "Power Boost", // Changed from "Booster"
    icon: <Rocket size={20} className="text-blue-600" />, // Changed icon color
    route: "/app/settings/farmingupgrade",
  },
  // Modify other settings or add new ones
];
```

#### Farming Upgrades (`src/data/farmingupgrades.json`)

This file contains the configuration for farming upgrades, including:
- Upgrade levels
- Costs
- Rewards
- Time periods

#### Stakes Configuration (`src/data/stakes.js` and `src/data/stakes.json`)

These files contain the staking options and configurations.

#### Daily Rewards (`src/data/dailylogin.json` and `src/data/dailycombo.json`)

These files control the daily login rewards and combo system.

### Modifying Games

Each game is located in its own directory under `src/app/games/`. To modify game mechanics, rewards, or appearance:

1. Navigate to the specific game directory
2. Modify the game component files
3. Update the rewards and game logic as needed

### Customizing UI Elements

#### Colors and Styling

The project uses Tailwind CSS for styling. To change the color scheme:

1. Edit the `tailwind.config.mjs` file to update the theme colors
2. Update component styles in their respective files

#### Images and Assets

Replace images in the `public/image` directory with your own assets while keeping the same file names or update the references in the data files.

### Visual Guide: Changing Theme and Character

You can easily change the app's color theme and character from the **Settings** menu. Follow these steps:

#### 1. Go to Settings
Click the **Settings** icon in the bottom navigation bar.

![Settings Navigation](public/image/readme/settings-nav.png)

#### 2. Open Color and Theme Change Settings
Select **Settings** from the menu, then choose **Color And Theme Change Settings**.

![Color and Theme Change Settings](public/image/readme/settings-nav.png)

#### 3. Change Color Theme
Choose your preferred color theme from the available options.

![Change Color Here](public/image/readme/change-color.png)

#### 4. Change Character
Select your favorite character from the list.

![Change Character Here](public/image/readme/change-character.png)

#### 5. See the Result
Here are examples of the four available theme and character combinations:

| Whale | Bird | Rocket | Cow |
|---------|-------|--------|-----|
| ![Whale](public/image/readme/theme-default.png) | ![Bird](public/image/readme/theme-ocean.png) | ![Rocket](public/image/readme/theme-sunset.png) | ![Cow](public/image/readme/theme-cow.png) |

## Deployment

### Telegram Bot Setup

1. Create a Telegram bot using [BotFather](https://t.me/botfather)
2. Configure your bot as a Mini App
3. Set up your webhook

### Telegram Analytics Setup

1. Go to [DataChief_bot](@DataChief_bot) on Telegram.
2. Create a Token and Give Name of the App.
3. Paste the SDK Auth Token and Name in the src/data/TGAnalytics.js 

For more info visit https://docs.tganalytics.xyz/

### Deploying to Production

The easiest way to deploy your Next.js app is using the [Vercel Platform](https://vercel.com):

1. Push your repository to GitHub, GitLab, or Bitbucket
2. Import the project to Vercel
3. Configure your environment variables
4. Deploy

For other deployment methods, refer to the [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying).

## Project Structure

```
finny-gaming-bot/
├── public/            # Static assets
├── src/
│   ├── app/           # Next.js app router pages
│   ├── components/    # Reusable components
│   ├── data/          # Customizable data files
│   ├── Firebase/      # Firebase configuration
│   ├── lib/           # Utility libraries
│   ├── redux/         # Redux store configuration
│   ├── services/      # API and service functions
│   ├── styles/        # Global styles
│   ├── utils/         # Helper utilities
├── .env.local         # Environment variables (create this)
├── package.json       # Dependencies and scripts
└── tailwind.config.mjs # Tailwind configuration
```

## Support and Documentation

For more detailed information about specific components or functionality, please refer to:

- [Next.js Documentation](https://nextjs.org/docs)
- [Firebase Documentation](https://firebase.google.com/docs)
- [Telegram Mini Apps Documentation](https://core.telegram.org/bots/webapps)


