# SOP-Bot Knowledge Assistant

1. Project Purpose
SOP-Bot is a lightweight client-side chatbot designed to help users search internal Standard
Operating Procedures (SOPs). It uses fuzzy search to return relevant answers from structured
knowledge content built from markdown or documentation files.

2. Technology Stack
• HTML5 – chat interface structure
• CSS3 – UI styling
• Vanilla JavaScript – chatbot logic
• Fuse.js – fuzzy search engine
• DOMPurify – HTML sanitisation for safe rendering
• JSON – structured knowledge storage
• GitHub Actions – automated knowledge build pipeline
• Jekyll – static site generation support

3. System Architecture
• Static frontend chatbot UI
• Structured knowledge.json file
• Build pipeline converts documentation into search-ready JSON
• Client-side fuzzy search retrieves best matches
• Sanitised HTML rendered into chat interface

4. Knowledge Base Structure
Knowledge content is stored in data/knowledge.json. Each entry typically includes:
• content – formatted HTML answer
• keywords – searchable terms
• filename – source document reference

5. Search Logic
Fuse.js performs fuzzy matching across content and keyword fields. The search allows partial
matches, misspellings and flexible phrasing.
• threshold controls match tolerance
• ignoreLocation improves semantic matching
• top 3 matches returned
• stopwords removed before search

6. Query Preprocessing
• Convert query to lowercase
• Remove punctuation
• Remove common stopwords
• Expand synonyms (e.g. login = sign in)
• Rebuild enhanced query string

7. UI Rendering
Messages are dynamically inserted into the DOM using appendMessage(). HTML content is
sanitised using DOMPurify to prevent script injection.
• Supports formatted lists
• Supports tables
• Supports inline images
• Images expand via modal viewer

8. Modal Image Viewer
• Clicking image opens fullscreen overlay
• Improves readability of screenshots
• Modal closes on click

9. Conversation Flow
• User submits question
• Query preprocessed
• Fuse search executed
• Top results returned
• Refresh button appears after first question

10. Build Pipeline
GitHub Actions automates creation of knowledge.json when documentation changes.
• Triggered on push to main branch
• Node environment installs dependencies
• build-knowledge.js generates JSON knowledge file
• Updated file committed automatically
• Jekyll builds static site output

11. Security Considerations
• DOMPurify sanitises rendered HTML
• No server-side execution
• No user authentication
• Static hosting compatible
• No storage of personal information

12. Scalability Considerations
• Knowledge base easily extended
• Markdown documentation convertible to JSON
• Supports large SOP libraries
• Search performance configurable via Fuse settings

13. Potential Enhancements
• Semantic search embeddings
• Analytics tracking
• User feedback capture
• Role-based filtering
• Integration with document repositories
