# Lucid Architecture for Cortex Code

Turn the architecture discussed or built in a Cortex Code session into a Snowflake-branded diagram. The skill creates a **native, editable Lucidchart document through the Lucidchart MCP**, or a local **draw.io file** when precise typography is the priority.

This repository contains skill instructions, reference material, and templates. It is not a standalone application or an MCP server.

## What it does

- Identifies Snowflake components and external dependencies from the conversation.
- Recommends an architecture layout based on the use case.
- Asks you to confirm the layout and component inventory before drawing.
- Distinguishes Snowflake components, external systems, and core processing with consistent colors.
- Creates the diagram and, for Lucidchart output, exports a PNG for visual inspection before handoff.

Typical uses include demo wrap-ups, solution architecture discussions, and visual summaries of data pipelines or AI applications. The starting point is session context, not an automatic inventory of an entire Snowflake account.

## Prerequisites

- **Cortex Code** with this skill available.
- **For Lucidchart:** a configured and authenticated Lucidchart MCP connection with permission to create documents and export PNGs.
- **For draw.io:** an editor capable of opening `.drawio` files.
- Enough conversation context to identify the components and their relationships.

The Lucidchart connection is configured separately; cloning this repository does not install or authenticate the MCP server. Snowflake access is needed only for additional account queries, not to draw an architecture already described in the conversation.

## Local setup

For a local setup using `~/.snowflake/cortex/skills/`, clone the repository into a directory named `lucid-architecture`:

```bash
git clone https://github.com/sfc-gh-ereitberger/lucid-architecture.git \
  "$HOME/.snowflake/cortex/skills/lucid-architecture"
```

Use this command only if the destination does not already exist. If you already have the skill installed, inspect its repository and local changes before updating it; do not overwrite your existing copy.

Keep `SKILL.md`, `references/`, and `templates/` together. Confirm that Cortex Code can load the `lucid-architecture` skill before using it.

## Usage

Invoke the skill in Cortex Code and describe the desired diagram:

```text
/lucid-architecture
Create a Lucidchart architecture diagram of what we built in this session.
```

Other example prompts:

```text
Create a technical architecture diagram showing our sources, ingestion,
storage, processing, and consumption layers. Use Lucidchart.
```

```text
Summarize this AI demo as Data -> Tools -> Agent -> Interface.
Ask me to confirm the component list before generating the diagram.
```

```text
Create a draw.io architecture file from this session and save it as
architecture.drawio. Use the service-focused layout.
```

Lucidchart is the default output. Request draw.io explicitly when you want a local file instead.

## Workflow

1. **Analyze context.** Identify relevant tables, stages, pipelines, AI services, applications, integrations, and external systems.
2. **Choose a layout.** Review the recommended layout and confirm or change it.
3. **Approve components.** Review the proposed title and internal/external component mapping.
4. **Generate.** Create a native Lucidchart document through MCP, or populate a draw.io template.
5. **Verify and refine.** For Lucidchart, inspect the PNG export for overlaps, text overflow, and connector problems. For draw.io, validate the XML. Adjust the result as needed.

### Layout options

| Layout | Best suited to |
| --- | --- |
| Use Case Architecture | Data, tools, agent, and interface in an end-to-end use case |
| Technical Architecture | Sources, ingestion, storage, processing, and consumption |
| Service Focused | Grouping by Snowflake service category |
| End User Led | Personas and interfaces leading into processing and data |

For native Lucidchart output, the skill also applies a horizontal-band geometry recipe to reduce connector crossings and layout collisions.

## Lucidchart MCP integration

The workflow uses these tools and resource:

- `mcp_lucidcharts_get_mcp_resource` to read `lucid://diagram-specification` before document creation.
- `mcp_lucidcharts_lucid_create_diagram_from_specification` to create a native Lucidchart document.
- `mcp_lucidcharts_lucid_export_document_as_PNG` to obtain a rendering for visual verification.

The skill disables assisted layout for its manually positioned containers and uses separate text shapes for individual detail lines. See the [Lucid import reference](references/lucid-standard-import.md) for the documented geometry and rendering workarounds.

**Data handling:** Native diagram generation sends the diagram's labels, object names, and architecture details to Lucidchart through the configured MCP connection. Include only information you are authorized to send there. Never put credentials or secrets in diagram content. A local draw.io file is the alternative when you do not want to create a Lucid document.

## Visual conventions

- **Snowflake blue (`#29B5E8`):** Snowflake components and internal flows.
- **Orange (`#FF9F36`):** External systems and external flows.
- **Dark blue (`#11567F`):** Core agents or processing and structural accents.
- **Purple (`#7254A3`):** Occasional highlights.

Diagrams include layer grouping, component cards, labeled connections, and a color legend. See the [style guide](references/style-guide.md) for details.

## Rendering caveats

The bundled Lucid import reference records constraints and workarounds from the workflow's development, including text auto-fitting, line-break handling, and limited typography control. These notes describe this skill's import workflow, not a guarantee about every current Lucid API or editor feature.

The current instructions anticipate a manual font-size pass in the Lucid editor if text sizes are uneven. Inspect the exported image rather than assuming a successful API response means the diagram is presentation-ready. Choose draw.io when exact font sizes and typography are required in the generated artifact.

## Repository contents

- [SKILL.md](SKILL.md): Entry point, output selection, approval checkpoints, and generation workflow.
- [references/style-guide.md](references/style-guide.md): Colors, typography, and layout conventions.
- [references/lucid-standard-import.md](references/lucid-standard-import.md): Lucid import constraints, geometry, and verification guidance.
- [references/drawio-components.md](references/drawio-components.md): Reusable draw.io XML components.
- [references/icon-mapping.md](references/icon-mapping.md): Icon guidance for draw.io output.
- [templates/](templates/): Four draw.io architecture templates.

## Attribution

This repository is a fork of [sfc-gh-lbandini/lucid-architecture](https://github.com/sfc-gh-lbandini/lucid-architecture). The fork extends the original draw.io workflow with native Lucidchart MCP generation, import guidance, and a PNG-based visual verification step.
