# Project Name : Sticky Notes (fullstack app)

## Table of Contents
1. [Introduction](#introduction)
2. [Basic Setup](#basic-setup)
3. [Draggable Cards](#draggable-cards)
4. [Connecting Backend](#connecting-backend)
5. [Saving Changes](#saving-changes)
6. [Deleting Notes](#deleting-notes)
7. [Context State](#context-state)
8. [Creating Notes](#creating-notes)
9. [Changing Colors](#changing-colors)

## Introduction

Welcome to the Note Taking App, a versatile tool designed to help you manage your notes efficiently. This application allows users to create, edit, and organize notes in a user-friendly interface with several powerful features.

### Key Features:

- **Draggable Cards:** Move notes around the screen with ease by clicking and dragging. The app ensures that your notes stay in place even after a page reload.
- **Dynamic Note Creation:** Quickly add new notes and customize their content. Notes are automatically saved and synchronized with the backend.
- **Customizable Colors:** Personalize your notes with a range of color options for backgrounds, headers, and text.
- **Persistent Storage:** All changes, including note positions and content, are saved to a backend database to ensure that your data is always available.
- **Context State Management:** Utilize context state to handle global settings such as themes or user preferences across the application.

This app is built with React for a smooth and responsive user experience, and leverages Appwrite for backend operations, providing a reliable and scalable solution for note management.

Explore the sections below to get started with setup, usage, and customization of the Note Taking App.


## Basic Setup


To get started with the Note Taking App, follow these steps to set up your development environment and run the application locally.

### Prerequisites

1. **Node.js and npm:** Ensure you have Node.js and npm (Node Package Manager) installed on your machine. You can download and install them from [Node.js official website](https://nodejs.org/).

2. **Appwrite Account:** Sign up for an Appwrite account at [Appwrite.io](https://appwrite.io/) and create a project. You will need the endpoint, project ID, and API keys for connecting to the backend.

### Clone the Repository

## Draggable Cards

The Draggable Cards feature allows users to move notes around the screen effortlessly, providing a dynamic and interactive experience. This section explains how the draggable functionality is implemented and how users can utilize it.

### How It Works

1. **Mouse Events:** The draggable functionality is achieved using mouse events. When a user clicks and holds the mouse button on a note, the `onMouseDown` event is triggered. This event sets up the initial position of the mouse and begins tracking movement.

2. **Dragging Logic:** As the user moves the mouse, the `onMouseMove` event updates the position of the note. The application calculates the change in mouse position (delta) and adjusts the position of the note accordingly. This allows the note to follow the mouse cursor in real-time.

3. **Release and Save Position:** When the user releases the mouse button, the `onMouseUp` event stops tracking mouse movement and saves the new position of the note. This position is then updated in the backend database to ensure that it persists even after a page reload.

### Implementation Details

1. **Event Handling:** 
   - **`onMouseDown`**: Initiates dragging by recording the starting mouse position and adding event listeners for mouse movement and release.
   - **`onMouseMove`**: Continuously updates the position of the note based on the current mouse coordinates.
   - **`onMouseUp`**: Ends the dragging operation and updates the note's position in the backend.

2. **Position Calculation:** The application calculates the difference between the current and starting mouse positions to determine how far the note has been moved. This delta is used to update the note's position.

3. **Persisting Position:**
   - After dragging is completed, the new position of the note is saved in the backend using an update operation. This ensures that the note's position is retained across page reloads and sessions.


## Connecting Backend

This section covers the integration of your application with the backend, focusing on how to set up and connect to the backend services that manage data for your application. For this project, we use Appwrite as our backend service, which provides a variety of features for managing databases, authentication, and more.

### Appwrite Setup

1. **Appwrite Client Configuration:**
   - **Initialization:** The Appwrite client is initialized with your project’s endpoint and project ID. This setup is crucial for connecting your frontend application to the Appwrite backend.
   - **Environment Variables:** The endpoint and project ID are stored in environment variables for security and flexibility. Ensure you have a `.env` file with the appropriate variables.

   ```javascript
   import { Client, Databases } from "appwrite";

   const client = new Client()
       .setEndpoint(import.meta.env.VITE_ENDPOINT)  // Your Appwrite endpoint
       .setProject(import.meta.env.VITE_PROJECT_ID); // Your Appwrite project ID

   const databases = new Databases(client);

   export { client, databases };


## Saving Changes

Saving changes in your application is crucial to ensure that user modifications, such as updates to notes, are preserved across sessions. This section outlines the process for saving changes to your notes, including updates to their content and position.

### Overview

Changes made to notes in your application, such as text updates or repositioning, need to be saved back to the backend. This ensures that data remains consistent and persistent even after a page reload or application restart.

### Saving Note Content

1. **Text Area Updates:**
   - **Auto Grow:** As users type in the text area, it automatically adjusts its height to fit the content. This is achieved through the `autoGrow` function, which updates the height based on the text area’s scroll height.

   ```javascript
   const autoGrow = (textarea) => {
       textarea.style.height = 'auto';
       textarea.style.height = textarea.scrollHeight + 'px';
   };


## Deleting Notes

Deleting notes is an essential feature for managing and organizing your content. This section outlines the process for deleting notes from both the frontend and backend, ensuring that unwanted or obsolete notes are removed efficiently.

### Overview

To delete a note, you need to handle both the user interface (UI) for initiating the deletion and the backend operations to remove the note from the database. The deletion process typically involves:

1. **User Confirmation:** Confirming the user's intention to delete a note to prevent accidental deletions.
2. **Backend Request:** Sending a request to the backend to remove the note from the database.
3. **UI Update:** Reflecting the deletion in the UI by removing the note from the list.

## Context State

Context State Management is a powerful technique in React for managing and sharing state across different components in an application. This approach simplifies state management by providing a way to share data and functions without passing props through every level of the component tree.


## Creating Notes

Creating notes is a key feature of our application, allowing users to add and manage their own notes. This section covers the process of adding a new note, including the UI components and backend integration.

### Overview

The note creation process involves the following steps:
1. Providing a user interface for inputting note details.
2. Handling user input and form submission.
3. Saving the new note to the backend database.

## Changing Colors

Customizing the appearance of notes by changing colors is an important feature that enhances user experience. This section explains how users can adjust the colors of their notes, including both the note body and header.

### Overview

The color customization feature allows users to:
1. Select colors for the note body and header.
2. Save these color preferences and apply them to the notes.