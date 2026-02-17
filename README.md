# Design-Technology-II---Assignment-Week-5
System Diagram for midterm, Pseudocode (Structured notes)

System functionality: A minimal and calming dashboard that helps users stay focused while they're studying or working 

Overview of product (open to adding additional functionalities eventually):
- Focus session (user starts/pause, provided with break suggestions depending on length of session)
- Note section (user can type in directly or paste from another doc)
- LLM structures/organizes users notes (turns raw notes to organized and summarized bullets)
- Emphasis on calm layout with subtle alerts (for breaks) -> light and dark mode toggle

System Diagram description (how to read):

This system diagram showcases the architecture and the data flow of CognitiveLens, a focus and note-structuring dashboard.
The diagram is layed out from top to bottom, showing how user input flows throughout the system and returns structured output to the interface.

1) User Layer
   - The system begins with the user: The user will start focus session by clicking on start button
   - Ability to note take in dashboard by typing or pasting from another doc
   - User can then click "structure my notes" button to turn raw notes into summarized and more organized set of notes they can refer back to at any point
  
2) Dashboard (Frontend)
This is the user interface featuring 3 panels
  - Focus Session (Start/Pause session, timer, break prompt)
  - Notes section (User types or pastes notes)
  - Structured/Organized Notes Output (Displays summary, notes in bullet form, display follow up question to confirm understanding)

Dashboard frontend communicates with backend via REST API

3) Backend
Role/Responsibilities
  - Receive notes from dashboard
  - Store notes and overall session data
  - Calls LLM to structure/organize users notes
  - Running a rules Engine to determine the break reminders

This connects directly to storage layer and LLM API (Machine Learning component of project)

4) Storage Layer (JSON files)
   - Storage layers saves session data, raw notes and structured notes (post llm processing)

5) LLM API (ML component turning raw notes to structured JSON)
   - Receives notes in text
   - structured prompt
  And it eventually returns a structured JSON output containing notes summary with bullet points

6) Rules Engine
   - Rules engine checks session times threshold to determine if conditions are met to trigger
   a break suggestion.
   - If condition is met then a signal is sent back to the Dashboard User Interface prompting
   the user to take a break (no set time determined yet)

7) Dashboard UI
   - Actively updating with break suggestions, structured notes summary and overall
   session duration

End of flow
