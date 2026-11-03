
# The Gents Cut – Premium Barber Shop Website

## Project Overview

The Gents Cut is a modern, responsive website developed for a fictional premium barber shop based in Pretoria, South Africa.

The purpose of the website is to provide customers with an easy way to explore barbering services, view prices, learn more about the business, and book appointments online without having to phone or visit the shop.

The website focuses on a clean, professional design, simple navigation, and a functional online booking system that helps manage appointments and prevent double bookings.

## Features

### 1. Home Page
- Professional landing page introducing The Gents Cut.
- Clear branding and business information.
- Book Now buttons that direct customers to the booking section.
- Responsive layout for desktop, tablet, and mobile devices.

### 2. Services and Pricing
Customers can view the available barbering services and their prices.

| Service | Price |
|---|---:|
| Classic Haircut | R180 |
| Skin Fade | R220 |
| Beard Trim | R120 |
| Kids Cut | R140 |
| Cut & Beard | R300 |
| The Full Package | R380 |

### 3. About Section
Provides information about The Gents Cut, its approach to barbering, and its commitment to professional grooming and customer service.

### 4. Gallery
Displays images representing the barber shop, hairstyles, and grooming services.

### 5. Online Booking System
The website includes an online appointment booking system that allows customers to:
- Enter their personal details.
- Select a barbering service.
- Choose an appointment date.
- View available appointment times.
- Select an available time slot.
- Submit an appointment request.
- Receive a booking confirmation with a unique booking ID.
- Add their appointment to Google Calendar or Apple Calendar.

### 6. Contact Information
Customers can access the business contact details, opening hours, location, and social media links.

### 7. Terms and Conditions
The website includes a dedicated Terms & Conditions section explaining booking policies, cancellations, appointment requirements, pricing, and customer information.

---

## Technologies Used

The project uses the following technologies:

| Technology | Purpose |
|---|---|
| HTML5 | Provides the structure and content of the website. |
| CSS3 | Handles styling, layout, animations, and responsiveness. |
| JavaScript | Handles website interactions, form validation, and booking functionality. |
| Google Apps Script | Acts as the backend for processing and managing bookings. |
| Google Sheets | Stores customer booking information. |
| Google Calendar | Stores confirmed appointments and checks calendar availability. |
| Apple Calendar (ICS) | Allows customers to add appointments to Apple Calendar. |
| Google Fonts | Provides professional typography. |

---

## How the Booking System Works

The booking system connects the website to Google Apps Script, Google Sheets, and Google Calendar.

It uses these services to manage appointments and prevent customers from booking the same time slot.

### Booking Process

**Step 1: Customer selects a date**

The customer opens the booking section and selects their preferred appointment date.

**Step 2: Available times are checked**

JavaScript sends a request to the Google Apps Script web application.

The backend checks:
- Existing bookings stored in Google Sheets.
- Existing appointments in Google Calendar.
- Whether the selected date is a Sunday.
- Whether the appointment time has already passed.

The system then returns the available appointment times to the website.

**Step 3: Customer selects a time**

Only available time slots are displayed for the selected date. Already-booked times are disabled or excluded from the available options.

**Step 4: Customer submits the booking**

After completing the booking form, the customer submits their details.

Google Apps Script validates the booking again to ensure that the selected time has not already been booked.

A locking mechanism is also used to reduce the risk of two customers booking the same time simultaneously.

**Step 5: Booking is saved**

Once the booking is accepted:

1. A unique booking ID is generated.
2. A Google Calendar event is created.
3. The booking details are saved in Google Sheets.
4. The booking is marked as confirmed.
5. The website receives a confirmation response.

**Step 6: Customer receives confirmation**

The website displays the booking details and provides options to:
- Add the appointment to Google Calendar.
- Add the appointment to Apple Calendar.

### Booking System Architecture

```text
Customer
   |
   v
Website (HTML, CSS, JavaScript)
   |
   v
Google Apps Script
   |
   +----------------------+
   |                      |
   v                      v
Google Sheets        Google Calendar
   |                      |
   v                      v
Booking Records      Appointments
   |
   v
Booking Confirmation
   |
   v
Customer can add appointment
to Google or Apple Calendar
```

### How Double Booking Is Prevented

The system checks both Google Sheets and Google Calendar before displaying available times.

When a customer submits a booking, the backend checks availability again before confirming it.

This is important because another customer could book the same time while someone is completing the booking form.

Google Apps Script's LockService is used during booking processing to help prevent simultaneous booking requests from claiming the same time slot.

---

## Google Sheets Structure

The Google Sheets document acts as the booking database.

Each booking is stored as a separate row.

The spreadsheet contains the following columns:

| Column | Description |
|---|---|
| Booking ID | Unique identifier for the appointment. |
| Timestamp | Date and time the booking was created. |
| Name | Customer's full name. |
| Phone | Customer's contact number. |
| Email | Customer's email address. |
| Service | Selected barbering service. |
| Date | Appointment date. |
| Time | Appointment time. |
| Message | Additional customer information. |
| Start | Appointment start time. |
| End | Appointment end time. |
| Status | Booking status. |
| Calendar Event ID | Google Calendar event reference. |

---

## Project File Structure

```text
The-Gents-Cut/
│
├── index.html
│   └── Main website structure and content.
│
├── style.css
│   └── Website styling and responsive design.
│
├── script.js
│   └── Website interactions and booking functionality.
│
└── README.md
    └── Project documentation.
```

The Google Apps Script backend is maintained separately in Google Apps Script as `Code.gs`.

---

## Setup and Installation

### 1. Clone the Repository

```bash
https://github.com/farentino/web-demo/
```

### 2. Open the Project

Open the project folder in Visual Studio Code.

### 3. Configure Google Sheets

Create a Google Spreadsheet and add a worksheet named:

```text
Bookings
```

Add the required booking columns listed in the Google Sheets Structure section.

### 4. Configure Google Apps Script

1. Open Google Apps Script.
2. Create a new project.
3. Copy the backend code into `Code.gs`.
4. Add your Google Spreadsheet ID.
5. Configure your Google Calendar ID.
6. Set the project timezone to `Africa/Johannesburg`.
7. Deploy the project as a Web App.
8. Set execution to **Me** and access to **Anyone**.
9. Copy the deployed Web App URL.

### 5. Connect the Website

Open `script.js` and replace the placeholder URL:

```javascript
const GOOGLE_SCRIPT_URL =
    "PASTE_YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE";
```

with your deployed Google Apps Script Web App URL.

### 6. Run the Website

Open `index.html` in your browser or use the Live Server extension in Visual Studio Code.

---

## Business Information

**Business Name:** The Gents Cut

**Location:** Pretoria, Gauteng, South Africa

**Opening Hours:**
- Monday – Saturday: 09:00 – 18:00
- Sunday: Closed

---

## Future Improvements

Possible future improvements include:

- An administrator dashboard for managing appointments.
- Ability to cancel or reschedule bookings.
- Automated email and SMS booking notifications.
- Different appointment durations depending on the selected service.
- Customer booking history.
- Improved security and backend validation.
- Online payment integration.

---

## Developer

Developed as a web development project to demonstrate front-end development, JavaScript functionality, backend integration, and online appointment management.

**Project:** The Gents Cut – Premium Barber Shop Website

**Technologies:** HTML5, CSS3, JavaScript, Google Apps Script, Google Sheets and Google Calendar.
