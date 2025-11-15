# Product Requirements Document (PRD) - 10x-cards

## 1. Product Overview

10x-cards is a web application designed to help university students create educational flashcards efficiently. The core feature is an AI-powered tool that automatically generates flashcards from user-provided text, such as lecture notes or articles. This streamlines the creation process, making it easier for students to leverage the powerful spaced repetition learning technique. The Minimum Viable Product (MVP) will focus on AI generation, a simple review and editing workflow, manual creation, and integration with a pre-existing spaced repetition algorithm for study sessions.

## 2. User Problem

University students often need to learn and retain large amounts of information. While spaced repetition systems using flashcards are a proven and effective study method, the manual creation of high-quality flashcards is a significant barrier. The process is tedious and time-consuming, which often discourages students from adopting this technique, leading them to use less effective study methods. 10x-cards aims to solve this problem by automating the most labor-intensive part of the process.

## 3. Functional Requirements
### 3.1. User Account Management
3.1.1. Users must be able to register for a new account using an email address and a password.
3.1.2. Registered users must be able to log in to their accounts.
3.1.3. The system must securely store user credentials.
3.1.4. Logged-in users must be able to log out of their accounts.

### 3.2. AI-Powered Flashcard Generation
3.2.1. The application will use the Openrouter.ai for flashcard generation.
3.2.2. The user interface will feature a prominent text input area as the primary call-to-action for pasting notes.
3.2.3. Input text is limited to 10,000 characters per generation request.
3.2.4. A maximum of 10 flashcards can be generated from a single request.
3.2.5. User-submitted text will not be stored or used for any purpose after the generation process is complete.

### 3.3. Flashcard Review Workflow
3.3.1. AI-generated flashcards will be presented to the user as "candidates" in a review list.
3.3.2. From the review list, users can perform in-line edits to the front and back of each candidate flashcard.
3.3.3. Users can accept individual candidates, which saves them to their permanent flashcard collection.
3.3.4. Users can reject individual candidates, which discards them.
3.3.5. Only flashcards that are accepted (either immediately or after being edited) are saved.

### 3.4. Manual Flashcard Creation
3.4.1. A secondary option for manual flashcard creation must be easily accessible.
3.4.2. This option will open a simple modal with input fields for the "Front" and "Back" of the flashcard.
3.4.3. The "Front" field has a maximum length of 200 characters.
3.4.4. The "Back" field has a maximum length of 500 characters.
3.4.5. Flashcards will support plain text format only.

### 3.5. Flashcard Management
3.5.1. A central view will display a list of all the user's saved flashcards.
3.5.2. The list must support simple text-based search to filter flashcards.
3.5.3. The list must support pagination to handle a large number of flashcards.
3.5.4. Users can edit any saved flashcard via a modal.
3.5.5. Users can delete any saved flashcard.
3.5.6. For new users with no saved flashcards, the list area will display an "empty state" message with a clear call-to-action to generate or create their first flashcard.

### 3.6. Spaced Repetition Study Session
3.6.1. The application will integrate a ready-made, open-source spaced repetition algorithm (e.g., SM-2, FSRS).
3.6.2. Users can initiate a study session from their flashcard collection.
3.6.3. The study interface will be simple, presenting one side of a flashcard and allowing the user to reveal the other side.
3.6.4. The interface must include a mechanism for users to self-grade their recall (e.g., buttons for "Easy," "Good," "Hard").

## 4. Product Boundaries

### 4.1. In-Scope for MVP
- AI-powered flashcard generation from plain text.
- Manual flashcard creation.
- Basic flashcard management (view, edit, delete, search).
- Simple user authentication (email/password).
- Integration with a third-party spaced repetition algorithm.
- Web application only.

### 4.2. Out-of-Scope for MVP
- Developing a proprietary, advanced spaced repetition algorithm (like SuperMemo or Anki).
- Importing content from various file formats (e.g., PDF, DOCX, Markdown).
- Sharing flashcard sets or collaborating between users.
- Integrations with other educational platforms or Learning Management Systems (LMS).
- Native mobile applications for iOS or Android.
- Organizing flashcards into decks, folders, or categories.
- Support for rich text, images, or audio on flashcards.
- AI optimization for specific subjects or domains.
- Detailed user onboarding or tutorials.

### 4.3. Unresolved Issues
- The specific open-source spaced repetition algorithm has not yet been selected.
- The detailed UI and user flow for the "simple" study session, including self-grading mechanisms, need to be defined.

## 5. User Stories

### User Account Management

- ID: US-001
- Title: New User Registration
- Description: As a new user, I want to create an account using my email and password so I can save my flashcards and access them later.
- Acceptance Criteria:
  - 1. A registration form must be available with fields for email and password.
  - 2. The system validates that the email is in a correct format.
  - 3. The system checks if the email is already registered.
  - 4. The password must meet minimum security requirements.
  - 5. Upon successful registration, the user is logged in and redirected to the main application page.

- ID: US-002
- Title: User Login
- Description: As a registered user, I want to log in with my email and password to access my saved flashcards.
- Acceptance Criteria:
  - 1. A login form must be available with fields for email and password.
  - 2. The system validates the credentials against the user database.
  - 3. Upon successful login, the user is redirected to their flashcard list.
  - 4. An appropriate error message is shown for invalid credentials.

- ID: US-003
- Title: User Logout
- Description: As a logged-in user, I want to be able to log out of my account to ensure my session is secure.
- Acceptance Criteria:
  - 1. A logout button or link is available within the application.
  - 2. Clicking the logout button ends the user's session.
  - 3. The user is redirected to the login page or a public landing page after logging out.

### AI Flashcard Generation

- ID: US-004
- Title: Generate Flashcards from Text
- Description: As a student, I want to paste my study notes into the application so that the AI can automatically generate flashcards for me, saving me time.
- Acceptance Criteria:
  - 1. A text area is prominently displayed for pasting text.
  - 2. A "Generate" button initiates the AI generation process.
  - 3. After generation, the user is taken to a review screen displaying the candidate flashcards.
  - 4. The system provides feedback (e.g., a loading indicator) while the AI is processing the text.

- ID: US-005
- Title: Handle Input Limits for AI Generation
- Description: As a user, I want to be clearly informed about the input limitations so I know how much text I can submit at once.
- Acceptance Criteria:
  - 1. The UI displays the maximum character limit (10,000) near the text input area.
  - 2. The system prevents form submission if the text exceeds the character limit.
  - 3. A clear error message is displayed if the user tries to submit text that is too long.
  - 4. The UI indicates the maximum number of flashcards (10) that can be generated per request.

### Flashcard Review and Management

- ID: US-006
- Title: Review AI-Generated Flashcards
- Description: As a user, I want to review the AI-generated flashcards, make edits to them, and approve the ones I find useful, so my study set is accurate.
- Acceptance Criteria:
  - 1. AI-generated cards are displayed in a list format, each with a front and back.
  - 2. Each card in the review list has "Accept" and "Reject" buttons.
  - 3. Clicking "Accept" saves the card to my main flashcard list and removes it from the review list.
  - 4. Clicking "Reject" discards the card and removes it from the review list.
  - 5. I can edit the text of the front and back of each card directly in the review list before accepting it.

- ID: US-007
- Title: View Saved Flashcards
- Description: As a user, I want to view all my saved flashcards in a list so I can see my collection and decide what to do with them.
- Acceptance Criteria:
  - 1. A dedicated page or section lists all saved flashcards.
  - 2. Each list item displays the front and back of the flashcard.
  - 3. If there are more flashcards than fit on one page, pagination controls are available.

- ID: US-008
- Title: Handle Empty Flashcard List
- Description: As a new user with no flashcards, I want to see a helpful message that guides me on how to get started.
- Acceptance Criteria:
  - 1. When I view my flashcard list and it is empty, a message is displayed.
  - 2. The message encourages me to create my first flashcard.
  - 3. The message includes a clear call-to-action button or link to the AI generation or manual creation page.

- ID: US-009
- Title: Edit a Saved Flashcard
- Description: As a user, I want to edit a flashcard I have previously saved to correct a mistake or add more information.
- Acceptance Criteria:
  - 1. Each flashcard in my list has an "Edit" button.
  - 2. Clicking "Edit" opens a modal or form pre-filled with the flashcard's current front and back text.
  - 3. I can modify the text and save the changes.
  - 4. The flashcard list updates to show the new content.

- ID: US-010
- Title: Delete a Saved Flashcard
- Description: As a user, I want to delete a flashcard I no longer need to keep my collection relevant.
- Acceptance Criteria:
  - 1. Each flashcard in my list has a "Delete" button.
  - 2. Clicking "Delete" prompts me for confirmation to prevent accidental deletion.
  - 3. Upon confirmation, the flashcard is permanently removed from my collection.
  - 4. The flashcard list updates to reflect the removal.

- ID: US-011
- Title: Search for a Flashcard
- Description: As a user with many flashcards, I want to search for a specific one using keywords to find it quickly.
- Acceptance Criteria:
  - 1. A search bar is available on the flashcard list page.
  - 2. As I type in the search bar, the list filters in real-time to show only flashcards containing the search term in their front or back.
  - 3. The search is case-insensitive.
  - 4. Clearing the search bar restores the full list of flashcards.

### Manual Flashcard Creation

- ID: US-012
- Title: Manually Create a Flashcard
- Description: As a user, I want to create my own flashcards from scratch for specific concepts the AI might miss or for which I have my own wording.
- Acceptance Criteria:
  - 1. A "Create Manually" button is clearly visible and accessible.
  - 2. Clicking the button opens a modal with text fields for "Front" and "Back".
  - 3. The modal includes a "Save" button to add the new flashcard to my collection.
  - 4. The modal can be closed without saving.
  - 5. Character limits (200 for front, 500 for back) are enforced with user feedback.

### Study Session

- ID: US-013
- Title: Start a Study Session
- Description: As a learner, I want to start a study session where the application shows me flashcards based on a spaced repetition algorithm to optimize my learning.
- Acceptance Criteria:
  - 1. A "Start Study Session" button is available on the flashcard list page.
  - 2. Clicking the button begins a session, presenting the first flashcard selected by the algorithm.
  - 3. The session only includes flashcards that are due for review according to the algorithm.

- ID: US-014
- Title: Progress Through a Study Session
- Description: As a learner, I want to be shown one side of a flashcard, be able to reveal the answer, and then grade my recall to inform the spaced repetition algorithm.
- Acceptance Criteria:
  - 1. The study interface initially shows only the front of a flashcard.
  - 2. A "Show Answer" button or similar control reveals the back of the flashcard.
  - 3. After the answer is revealed, self-grading buttons (e.g., "Hard", "Good", "Easy") appear.
  - 4. Selecting a grade records the result and advances the session to the next card.
  - 5. When all due cards have been reviewed, a session summary screen is displayed.

## 6. Success Metrics

- 6.1. AI Quality: 75% of all AI-generated flashcards are accepted by the user (either directly or after editing). This will be measured via log analysis from a dedicated database table that tracks the lifecycle of the generated candidates.
- 6.2. AI Adoption: 75% of all user-saved flashcards (excluding deleted ones) originate from the AI generator. This indicates that the core feature is providing significant value and solving the primary user problem.
