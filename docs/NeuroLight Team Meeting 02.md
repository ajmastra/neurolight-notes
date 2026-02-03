---

Date: 02/02/2026

## Due Dates

- **Software Design Document Draft:** before Wednesday 02/04/26 meeting with Ogonna
- **Alpha Demo I Code:** before Monday 02/09/26 team meeting
- **Design Review 2**: before Wednesday 02/11/26 meeting with Ogonna

## Housekeeping To-Do List

- **Anthony**:
    - bring everything over from old folder into new drive folder for this semester
    - Fill out Task tracker for software design document
    - Fill out Task Tracker and Github issues with tasks for alpha demo 1 coding
    - Review Architectural overview's "why"
    - Create Design Review 2 slideshow
- **Andrew**:
    - Fill out Task Tracker and Github issues with tasks for alpha demo 1 coding
- **Franz**:
    - Fill out Task Tracker and Github issues with tasks for alpha demo 1 coding
- **Marcus**:
    - Fill out Task Tracker and Github issues with tasks for alpha demo 1 coding

## Alpha Demo Coding Assignments

### US2 - Image Alignment & Visual Property Adjustment (Anthony)

**User Story:** As a neuroscientist working with multi-day imaging sessions, I want to align image stacks and adjust visual properties (brightness, contrast, grayscale conversion), so that I can correct for motion artifacts and optimize images for ROI selection.

**Acceptance Criteria:**

- Image alignment uses PyStackReg for rigid body transformation
- Brightness and contrast sliders provide real-time visual feedback
- Grayscale conversion works for color images
- Alignment visibly corrects motion drift

**Suggested GitHub Issues:**

**Issue #1: Implement PyStackReg Integration for Image Stack Alignment**

- Set up PyStackReg dependency in requirements.txt
- Create ImageAlignmentService class to handle stack registration
- Implement rigid body transformation for image sequences
- Add reference frame selection (first frame, middle frame, or custom)
- Include progress reporting for multi-image alignment operations
- Write unit tests for alignment with synthetic shifted images
- Document alignment parameters and expected inputs/outputs

**Issue #2: Build Brightness/Contrast Adjustment UI Controls**

- Design slider widgets using PySide6 (QSlider)
- Implement real-time image adjustment preview using OpenCV
- Add reset button to restore original values
- Create histogram visualization to show pixel distribution changes
- Optimize for performance (debouncing, efficient array operations)
- Add keyboard shortcuts for fine-tuning adjustments
- Handle edge cases (all-black images, extreme values)

**Issue #3: Implement Grayscale Conversion Functionality**

- Add grayscale conversion button/checkbox to UI
- Implement OpenCV cv2.cvtColor for RGB to grayscale conversion
- Preserve original image and allow toggling between color/grayscale
- Update histogram and statistics displays for grayscale mode
- Ensure alignment works correctly with grayscale images
- Add preference saving for default conversion settings

**Issue #4: Create Alignment Validation and Quality Metrics**

- Implement alignment quality score (correlation coefficient, RMSE)
- Add visual overlay option to compare before/after alignment
- Create alignment report showing transformation parameters
- Add option to manually adjust alignment if automatic fails
- Implement undo/redo for alignment operations

---

### US3 - ROI Selection Tools (Andrew)

**User Story:** As a neuroscientist analyzing neuronal activity, I want to manually select and define regions of interest (ROIs) using multiple drawing tools, so that I can precisely identify neurons for time-series analysis.

**Acceptance Criteria:**

- Users can draw circular and freehand polygon ROIs
- ROIs display with visible outlines and labels
- ROI coordinates save to JSON
- Multiple ROIs can be created, edited, moved, and deleted

**Suggested GitHub Issues:**

**Issue #5: Implement Circular ROI Drawing Tool**

- Create ROI drawing mode with click-and-drag circle creation
- Display dynamic circle preview during drawing
- Show radius and center coordinates in real-time
- Add snap-to-grid option for precise placement
- Implement circle editing (resize by dragging edge, move by dragging center)
- Add validation to prevent zero-radius circles
- Write tests for circle coordinate calculations

**Issue #6: Implement Freehand Polygon ROI Drawing Tool**

- Create polygon drawing mode with click-to-add-vertex interaction
- Support closing polygon (double-click or click first vertex)
- Display temporary line preview between last vertex and cursor
- Add vertex editing mode (drag vertices to reposition)
- Implement vertex insertion (click on edge) and deletion (right-click vertex)
- Add polygon simplification for overly complex shapes
- Handle self-intersecting polygons gracefully

**Issue #7: Build ROI Management System**

- Create ROI data model (ID, type, coordinates, label, color, metadata)
- Implement ROI list/table view showing all defined ROIs
- Add ROI selection/highlighting (click on list selects on image)
- Create unique labeling system (ROI-001, ROI-002, etc.)
- Allow custom ROI naming and color assignment
- Implement ROI visibility toggle (show/hide individual or all)
- Add bulk operations (delete all, export selected, etc.)

**Issue #8: Implement ROI Persistence (JSON Serialization)**

- Design JSON schema for ROI storage
- Implement save functionality (ROI data → JSON file)
- Implement load functionality (JSON file → ROI objects)
- Handle backward compatibility for schema changes
- Add validation when loading ROIs (check for required fields)
- Support exporting ROIs to standard formats (CSV for coordinates)
- Include metadata (creation timestamp, creator, image dimensions)

**Issue #9: Add ROI Editing and Manipulation Tools**

- Implement drag-to-move functionality for any ROI type
- Add ROI deletion with confirmation dialog
- Create duplicate ROI feature
- Add ROI merging capability for adjacent regions
- Implement ROI statistics display (area, perimeter, centroid)
- Add undo/redo stack for ROI operations
- Create keyboard shortcuts for common ROI operations

---

### US4 - Workflow Enforcement & Error Handling (Franz)

**User Story:** As a neuroscientist learning the application, I want the system to enforce a logical workflow order and provide clear error messages, so that I don't accidentally skip critical steps or lose work.

**Acceptance Criteria:**

- Application prevents invalid operations (e.g., selecting ROI before loading images)
- Clear error messages guide users to correct actions
- Workflow enforces: create/load project → upload images → align/edit → select ROIs → save

**Suggested GitHub Issues:**

**Issue #10: Design Application State Machine**

- Define application states (NO_PROJECT, PROJECT_LOADED, IMAGES_LOADED, ALIGNED, ROIS_DEFINED)
- Create StateManager class to track current application state
- Implement state transition rules and validation
- Add state change event listeners for UI updates
- Document valid state transitions in flowchart/diagram
- Write unit tests for all state transitions

**Issue #11: Implement UI Component State Management**

- Disable buttons/menus when operations are invalid for current state
- Add tooltip explanations for disabled controls ("Load project first")
- Update menu item availability based on state
- Create visual indicators for current workflow step
- Add progress bar or step indicator showing workflow completion
- Ensure state persists correctly when loading saved projects

**Issue #12: Create Comprehensive Error Message System**

- Design user-friendly error message templates
- Implement ErrorHandler class with categorized error types
- Create modal dialogs for critical errors
- Add non-blocking notifications for warnings
- Include actionable suggestions in error messages
- Add "Learn More" links to documentation for complex errors
- Log all errors for debugging (with user consent)

**Issue #13: Implement Unsaved Changes Protection**

- Track modifications to project data (dirty flag)
- Show confirmation dialog before closing with unsaved changes
- Add autosave functionality (configurable interval)
- Create crash recovery mechanism (save state periodically)
- Display unsaved indicator in window title/status bar
- Implement "Save and Close" vs "Discard Changes" options

**Issue #14: Build Guided Workflow Tutorial/Wizard**

- Create first-run tutorial overlay highlighting key features
- Implement optional step-by-step workflow guide
- Add contextual help tooltips for each major operation
- Create sample project with test data for learning
- Add "What's Next?" suggestions after completing each step
- Include video demonstrations or animated guides

---

### US5 - Professional UI Design (Marcus)

**User Story:** As a neuroscientist who will use this tool regularly, I want a clean, professional, and intuitive user interface that follows modern design principles, so that I can work efficiently without distraction.

**Acceptance Criteria:**

- UI uses consistent color scheme and typography
- Controls are logically grouped and labeled
- Interface is responsive and provides visual feedback for all actions
- Design follows PySide6 best practices

**Suggested GitHub Issues:**

**Issue #15: Design and Implement UI Theme System**

- Research scientific software UI conventions and color schemes
- Create color palette (primary, secondary, accent, background, text colors)
- Define typography hierarchy (headers, body text, labels, monospace for data)
- Implement QSS (Qt Style Sheets) for consistent styling
- Add light/dark theme toggle capability
- Create high-contrast mode for accessibility
- Document design system in style guide

**Issue #16: Build Main Application Layout and Navigation**

- Design main window layout (menu bar, toolbar, central widget, side panels)
- Implement tabbed interface or dockable panels for different tools
- Create responsive layout that adapts to window resizing
- Add toolbar with commonly-used actions (save, undo, zoom, etc.)
- Implement status bar with relevant information (zoom level, cursor position, file info)
- Create keyboard navigation and shortcuts
- Ensure minimum window size maintains usability

**Issue #17: Design Control Panel for Image Adjustment Tools**

- Group related controls (alignment, brightness/contrast, ROI tools)
- Use collapsible sections (QGroupBox) to organize tools
- Add clear labels and units for all numeric inputs
- Implement spinboxes with appropriate min/max/step values
- Create icon system for tool buttons (custom or from icon library)
- Add tooltips for all controls explaining their function
- Ensure control panel can be hidden/shown to maximize workspace

**Issue #18: Implement Visual Feedback System**

- Add loading spinners/progress bars for long operations
- Create hover effects for interactive elements
- Implement status indicators (processing, ready, error states)
- Add animation for state transitions (smooth, not distracting)
- Create notification system for completed operations
- Show cursor changes for different tool modes (crosshair, pointer, move)
- Add visual confirmation for saved changes

**Issue #19: Build Image Viewer Widget with Interactive Controls**

- Implement high-performance image display using QGraphicsView
- Add pan (click-and-drag) and zoom (scroll wheel) controls
- Create zoom controls (fit to window, 100%, zoom in/out buttons)
- Display image information overlay (dimensions, zoom level, cursor coordinates)
- Implement smooth zoom centered on cursor position
- Add minimap/navigator for large images
- Optimize rendering for large image stacks

**Issue #20: Create Responsive and Accessible UI Components**

- Ensure all interactive elements have keyboard access
- Implement proper tab order for form controls
- Add screen reader support (ARIA labels, proper widget roles)
- Test UI with different screen sizes and resolutions
- Ensure minimum contrast ratios for readability
- Add font size scaling option
- Test with accessibility tools and make improvements

---

### US6 - CI/CD and Packaging (Andrew)

**User Story:** As a development team, we want automated packaging and continuous integration/deployment (CI/CD) for NeuroLight, so that we can reliably build and distribute the application across platforms.

**Acceptance Criteria:**

- CI/CD pipeline automatically builds applications on code commits
- Packaging creates distributable executables for target platforms
- Build process is documented and reproducible
- Version numbering is automated

**Suggested GitHub Issues:**

**Issue #21: Set Up GitHub Actions CI/CD Pipeline**

- Create `.github/workflows/ci.yml` for continuous integration
- Configure pipeline to run on pull requests and main branch pushes
- Set up testing stage (run pytest with coverage reporting)
- Add linting stage (flake8, black, mypy)
- Configure matrix builds for multiple Python versions
- Add build artifacts storage for successful builds
- Set up branch protection rules requiring CI passing

**Issue #22: Implement Automated Testing Infrastructure**

- Set up pytest configuration with appropriate fixtures
- Create test data fixtures (sample images, ROI files)
- Write integration tests for major workflows
- Implement GUI testing using pytest-qt
- Add code coverage reporting (aim for >80% coverage)
- Set up automated test execution in CI pipeline
- Create test report generation and archiving

**Issue #23: Configure PyInstaller for Cross-Platform Packaging**

- Create PyInstaller spec files for each platform (Windows, macOS, Linux)
- Configure bundling of all dependencies and assets
- Optimize executable size (exclude unnecessary packages)
- Test packaged application on target platforms
- Add code signing for Windows and macOS builds
- Create installer packages (NSIS for Windows, DMG for macOS, AppImage for Linux)
- Document packaging process and troubleshooting

**Issue #24: Implement Automated Version Management**

- Choose versioning scheme (semantic versioning: MAJOR.MINOR.PATCH)
- Set up version file or use git tags for version tracking
- Implement automatic version bumping in CI pipeline
- Add version display in application (About dialog, window title)
- Create changelog generation from commit messages
- Tag releases automatically when merging to main
- Add version checking and update notification feature

**Issue #25: Create Release Automation Workflow**

- Build GitHub Actions workflow for release creation
- Automatically generate release notes from changelog
- Upload packaged executables as release assets
- Create separate workflows for development builds vs releases
- Add pre-release/beta release support
- Implement release approval process
- Set up notifications for new releases

**Issue #26: Document Build and Deployment Process**

- Write comprehensive BUILD.md with setup instructions
- Document CI/CD pipeline configuration and customization
- Create troubleshooting guide for common build issues
- Add platform-specific build instructions
- Document dependency management strategy
- Create developer onboarding guide
- Add architecture diagrams for CI/CD flow


## Design Review 2 Assignments

**Anthony**
- Introduction and Context
- Alpha Demo Presentation Video and Voice over
- Conclusion

**Andrew**
- Problem Statement
- Challenges and Resolutions

**Franz**
- Software design Overview

**Marcus**
- Software Design Overview
