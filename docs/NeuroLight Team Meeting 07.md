---

Date: 05/01/2026

## Image Culling Overhaul

- Replace the current "exclude" click mechanism with a dual-handle scrollbar (bracket-style)
- Each handle represents a bracket on either end of the frame range
- Frame number displayed above each bracket handle
- Anything outside the brackets is automatically excluded

---

## Public Folder Support

- Users can set an experiment to be public
- Public experiments are accessible via a permanent "public user" account as read-only
- Header bar added to indicate whether the current experiment is shared or private

---

## CSV Export for Peaks and Troughs

- Add ability to export a CSV file containing only the peaks and troughs for each neuron

---

## Rayleigh Plot Per Day

- Generate one Rayleigh plot per day, measured from trough to trough

---

## Get Started Folder on GitHub

- Create a "Get Started" folder in the GitHub repository
- Include 50 sample images
- Include a simple how-to markdown file

---

## Open Questions / Action Items

- [ ] **Team:** Implement dual-handle bracket scrollbar for image culling with frame number labels
- [ ] **Team:** Add public folder support with read-only access under a permanent public user account and shared/private header indicator
- [ ] **Team:** Add CSV export for peaks and troughs only per neuron
- [ ] **Team:** Implement one Rayleigh plot per day (trough to trough)
- [ ] **Team:** Create "Get Started" folder in GitHub with 50 sample images and a how-to markdown file
