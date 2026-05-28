# Sprint 5 AI Agents, Team Allocation, and 3-Week Plan

## 1. Client Requirement Summary
The client requested two new AI agents for the website.

### AI Agent 1: Listing Assistant for Sellers
When a seller uploads a product photo, the AI should help generate draft listing details such as:
- Title
- Description
- Category
- Condition
- Estimated price suggestion

The seller must still be able to review and edit everything before publishing the listing.

### AI Agent 2: Recommendation Agent for Logged-in Users
This AI agent should recommend relevant second-hand products based on:
- User interests
- Browsing activity
- Saved items
- Preferred categories
The purpose is to make the platform more personalized and improve the user experience.

### 3.1 AI Listing Assistant for Sellers
Proposed workflow:
1. User uploads one or more product images
2. The system sends image context and a prompt to an external AI API
3. The AI returns draft listing details
4. The seller reviews and edits the generated content
5. The final listing is saved only after the seller confirms it

Expected AI-generated draft fields:
- Suggested title
- Suggested description
- Suggested category
- Suggested item condition
- Suggested estimated price or price range

### 3.2 Recommendation Agent for Logged-in Users
Proposed workflow:
1. Logged-in user enters the platform
2. The system collects or reads preference signals
3. The backend generates ranked product recommendations
4. The frontend displays personalized items
5. The user can open recommended product pages directly

Possible recommendation input signals:
- Preferred categories
- Browsing history
- Saved or liked items
- Recently viewed products
- User profile interests

---

## 4. Non-Functional Requirements
- AI output must remain editable and should only be used as a draft
- Listing creation should still work even if the AI API is temporarily unavailable
- Recommendation responses should be reasonably fast
- API keys and external integration settings must be securely configured
- The system should support fallback logic when AI-generated results are unavailable
- Testing should cover API failures, invalid images, empty recommendations, and edge cases

---

## 5. Suggested Technical Approach

### 5.1 Current Backend Fit
The current backend is based on:
- Spring Boot
- MySQL
- MyBatis-Plus
- File upload support
- Existing item, category, user, and messaging modules

This allows the team to extend the current architecture instead of redesigning it from scratch.

### 5.2 Proposed Backend Additions
Suggested additions include:
- A dedicated AI service layer for external AI API integration
- A seller-side endpoint such as `/api/v1/items/ai-draft`
- A user recommendation endpoint such as `/api/v1/items/recommendations`
- Recommendation data tracking for viewed items, saved items, and category preferences
- Fallback logic when the AI API is unavailable

### 5.3 Proposed Frontend Additions
Suggested frontend work includes:
- An AI-assisted listing flow after product image upload
- A pre-filled editable listing form
- Personalized recommendation sections for logged-in users
- Loading, retry, empty-state, and error-state UI support

---

## 6. Team Allocation for 7 Members
Since actual names were not provided, placeholder roles are used below. These can be replaced later with real names.

| Member | Role | Primary Responsibility | Main Deliverables |
|---|---|---|---|
| Member A | Frontend Lead | AI listing assistant UI flow | Upload-to-draft flow, editable listing form, loading and error states |
| Member B | Frontend Developer | Recommendation UI | Recommendation section, item cards, logged-in user display |
| Member C | Frontend / Integration | Shared integration and UI polish | Cross-page consistency, API connection fixes, demo support |
| Member D | Backend Lead | AI listing assistant backend | AI API client, prompt design, draft endpoint, validation |
| Member E | Backend Developer | Recommendation service | User-signal handling, ranking logic, recommendation API |
| Member F | Backend / Database | Data support and tracking | Schema changes, browsing history or saved item support, test data |
| Member G | QA / PM / Full-stack Support | Testing and coordination | Test plan, regression checks, documentation, final demo recording |

Recommended coordination model:
- 3 frontend-focused members
- 3 backend-focused members
- 1 QA/PM/integration owner

---

## 7. Weekly Plan (3 Weeks)

| Week | Focus | Frontend Tasks | Backend Tasks | Team Output |
|---|---|---|---|---|
| Week 1 | Planning and setup | Design AI listing flow, recommendation UI layout, wireframes, UI states | Choose AI API, design backend endpoints, define prompt strategy, design DB changes | Confirmed architecture, task split, API contract, risk list |
| Week 2 | Core implementation | Build listing draft UI and recommendation components, connect APIs | Implement AI draft API, recommendation API, tracking logic, fallback logic | End-to-end working prototype |
| Week 3 | Testing and polishing | Improve UX, loading states, mobile support, final UI polish | Fix bugs, secure config, optimize logic, finalize test data | Stable sprint build, tested release, demo-ready version |

---

## 8. Detailed Work Breakdown

### Frontend Team Tasks
- Design the seller journey from image upload to AI-generated draft
- Build editable form fields for title, description, category, condition, and price
- Design personalized recommendation components for logged-in users
- Handle empty, loading, retry, and API failure states
- Prepare polished UI for the final screen recording demo

### Backend Team Tasks
- Integrate the external AI API for image-based draft generation
- Parse and validate AI output into internal DTOs
- Capture or infer recommendation signals from user activity
- Build ranked recommendation logic and API response structure
- Secure API keys and support fallback behavior

### QA / PM / Documentation Tasks
- Track sprint progress and task completion
- Prepare test checklist and regression plan
- Verify integration between frontend and backend
- Organize and record the final demo video
- Prepare sprint report and documentation

---

## 9. Expected Deliverables
By the end of Sprint 5, the team is expected to deliver:
- AI Listing Assistant for sellers
- Recommendation Agent for logged-in users
- External AI API integration in the backend
- Recommendation-related data support or tracking logic
- Test results and regression verification
- Screen recording demo of current and new features
- Sprint planning and task allocation document

---

## 10. Risks and Mitigation

| Risk | Impact | Mitigation |
|---|---|---|
| AI API output is inconsistent | Draft quality may vary | Use strict prompt format, validation logic, and editable user review |
| Recommendation data is incomplete | Recommendation quality may be weak at first | Use category preference fallback and saved items as baseline |
| External API downtime or quota issue | Demo risk and feature interruption | Prepare fallback demo data and non-AI backup responses |
| Integration delay near deadline | End-to-end feature may fail late | Integrate early during Week 2 and assign one integration owner |
| Uneven workload distribution | Some members may become blockers | Split work clearly by ownership and sync frequently |

---

## 11. Screen Recording Demo Suggestion
Recommended demo order:
1. Briefly introduce the project and the marketplace purpose
2. Show current app features such as registration/login, item browsing, category filtering, item details, messaging, and listing creation
3. Show the AI Listing Assistant flow from image upload to draft generation and editing
4. Show the Recommendation Agent flow for a logged-in user
5. End with a short summary of how AI improves both the seller and buyer experience

---

## 12. Submission Note
This document is prepared in a standardized format suitable for academic sprint planning and reporting.

Before submission, it is recommended to:
- Replace `Member A` to `Member G` with real team member names
- Add course name and student IDs if required
- Add the final demo recording link if available
- Mention the actual AI provider chosen by the team if your teacher expects that detail
