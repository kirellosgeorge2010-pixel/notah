# Notah Talmatha 2026 (نوته تلمذه) - Kirellos George

## Overview
Notah Talmatha is a modern, responsive single-page web application designed for students to submit their daily and weekly spiritual tracking reports. The app features a beautiful premium aesthetic utilizing a dark brown, gold, and cream color palette, ensuring a seamless and visually pleasing user experience.

## Features
- **Daily & Weekly Reports:** Users can toggle between daily and weekly report types, which dynamically updates the date selection UI (single date picker vs. week date range).
- **Auto-Fill Name:** Automatically remembers and fills the user's name using `localStorage` for quicker submissions on subsequent visits.
- **Comprehensive Tracking:** Contains intuitive form fields for tracking Gospel reading, Confession, Communion, Mass Attendance, Prayer times (Morning, Sunset, Sleep), and Meeting Attendance.
- **Conditional Field Display:** "Meeting Type" (Prep/Sec) options automatically appear with a smooth slide-down animation only when "Meeting Attendance" is marked as "Yes".
- **Seamless Submission System:** Sends data securely to a Google Apps Script (GAS) backend using a hidden `iframe` technique, avoiding CORS errors and preventing page redirects.
- **Interactive UI Feedback:** Displays a full-screen loading spinner overlay and a dynamic SVG success checkmark animation upon successful form submission.

## How it is Coded
The application is built entirely using vanilla web technologies without any heavy frameworks:
- **HTML5:** Provides the semantic structure and RTL (Right-to-Left) direction tailored for Arabic content.
- **CSS3:** Handles advanced styling, theming, Flexbox layouts, and custom interactive animations. Both embedded styles and an external `style.css` file are utilized.
- **JavaScript (Vanilla JS):** Manages DOM manipulation, complex date calculations (e.g., auto-calculating week bounds), conditional visibility of fields, strict form validation, and the background form submission mechanism.
- **Data Integration:** Dynamically generates a hidden `<form>` element injected into the DOM, targeting a hidden `<iframe>` to POST data directly to a Google Sheet via Google Apps Script.

## CSS Properties & Design System
The visual aesthetics are driven by a robust, reusable design system established using CSS custom properties:

### Color Palette (CSS Variables)
- **`--primary`: `#4a2225` (Dark Brown)** - Used for the header, form section backgrounds, and main text colors.
- **`--gold`: `#cf9f3e` (Gold)** - Used for accents, badges, row containers, button borders, and active states.
- **`--cream`: `#fdfaf1` (Cream)** - Used for the main body background, creating a soft contrast against the primary colors.

### Typography
- **Font Family:** `'Cairo', sans-serif` (imported via Google Fonts) utilizing weights 400, 700, and 900 for distinct visual hierarchy.

### Key Styling Techniques
- **Sticky Header:** Stays fixed at the top (`position: sticky; top: 0; z-index: 100;`), featuring a bottom curve (`border-radius: 0 0 30px 30px`) and gold borders.
- **Curved Form Container:** The main interactive form area uses `border-radius: 40px 40px 0 0` to create a modern, sleek arch effect.
- **Flexbox Architecture:** Extensive use of `display: flex; justify-content: space-between; align-items: center;` within the `.row` classes for perfect responsive alignment.
- **Custom Interactive Toggles:** Native radio buttons and checkboxes are hidden (`display: none;`). Their `<label>` tags are heavily styled with background opacities (`rgba(255,255,255,0.4)`) and transitions to act as modern interactive buttons.
- **Animations:**
  - **`@keyframes slideDown`**: Provides a smooth entrance (`opacity` and `transform: translateY`) for conditional sub-choices.
  - **`@keyframes spin`**: Drives the loading spinner in the submission overlay.
- **Overlay & Popups:** A full-screen overlay uses `visibility: hidden; opacity: 0; transition: 0.3s;` to smoothly fade in (`.overlay.show`) during form submission, disabling underlying page interactions.
