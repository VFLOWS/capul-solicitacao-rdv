# AI Agent Instructions for the capul-solicitacao-rdv Project

## 1. Project Overview & Architecture

This project is built on a **Business Process Management (BPM)** platform, likely **Fluig**. The architecture is centered around workflows that orchestrate business processes, with distinct components for UI, data, and logic.

- **`workflow/`**: The core of the application. It contains the business process definitions and the scripts that execute automated tasks.
- **`prototype/`**: Contains HTML files that serve as the user interface templates for workflow forms and other views. These are not standalone web pages but are rendered within the BPM platform.
- **`forms/`**: Defines the structure and fields of forms used in the workflows. These are linked to the HTML prototypes.
- **`datasets/`**: Manages data sources and structures, acting as the data layer for the forms and workflows.
- **`wcm/`**: "Web Content Management" components, such as custom layouts and widgets used across the platform.

The typical data flow is:
1. A user interacts with an HTML view from `prototype/`.
2. The associated form in `forms/` captures the data.
3. Submitting the form initiates or advances a workflow defined in `workflow/diagrams/`.
4. The workflow executes tasks, some of which are automated scripts located in `workflow/scripts/`.

## 2. Key Conventions & Patterns

- **Workflow Scripts**: The most important convention is the naming of service task scripts: `workflow/scripts/{process_name}.servicetask{task_id}.js`.
  - **Example**: `solicitacao_viagem.servicetask25.js` contains the JavaScript logic for the service task with ID `25` inside the `solicitacao_viagem.process` workflow.
- **No Standard Build Process**: This project does not use `npm`, `maven`, or other common build tools. Development consists of editing files and uploading them directly to the BPM platform. Do not look for or try to add files like `package.json`.
- **Component-Based Structure**: Each top-level directory (`forms`, `datasets`, `workflow`, etc.) represents a specific type of component within the platform. When adding a new feature, you will likely need to create or modify files in several of these directories.

## 3. How to Approach Common Tasks

- **Modifying a Workflow**:
  1. Analyze the process diagram in `workflow/diagrams/` to understand the flow.
  2. Identify the specific task to modify.
  3. Locate the corresponding JavaScript file in `workflow/scripts/` using the naming convention described above and apply the logic changes there.

- **Creating a New Form/Process**:
  1. Create the new dataset in `datasets/`.
  2. Define the new form in `forms/`.
  3. Build the UI template in `prototype/`.
  4. If it involves a new process, create the diagram in `workflow/diagrams/` and add any required service task scripts in `workflow/scripts/`.

- **Updating the UI**:
  1. Modify the relevant HTML file in `prototype/`.
  2. Ensure any changes to form fields are reflected in the corresponding form definition in `forms/` and dataset in `datasets/`.
