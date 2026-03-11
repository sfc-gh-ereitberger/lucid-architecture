# Snowflake Icon Mapping

Maps Snowflake products and concepts to icons for draw.io diagrams.

## Default Icons (Emoji)

These render natively in draw.io with zero external dependencies.

| Snowflake Concept | Emoji | Unicode |
|-------------------|-------|---------|
| **Data / Storage** | | |
| Database | 🗄️ | `&#128452;` |
| Table | 📋 | `&#128203;` |
| View / Dynamic Table | 📊 | `&#128202;` |
| Stage (Internal) | 📦 | `&#128230;` |
| Stage (External) | ☁️ | `&#9729;` |
| Iceberg Table | 🧊 | `&#129482;` |
| Data Share | 🤝 | `&#129309;` |
| **Cortex AI** | | |
| Cortex Agent | ❄ | `&#10052;` |
| Cortex Analyst | 📊 | `&#128202;` |
| Cortex Search | 🔍 | `&#128269;` |
| Cortex LLM | 🧠 | `&#129504;` |
| Cortex Functions | ⚡ | `&#9889;` |
| Semantic View | 📐 | `&#128208;` |
| **Data Engineering** | | |
| Snowpipe | 🔄 | `&#128260;` |
| Stream | 〰️ | `&#12336;` |
| Task | ⏱️ | `&#9201;` |
| Pipe | ⬇️ | `&#11015;` |
| Notebook | 📓 | `&#128211;` |
| **Integration** | | |
| External Access | 🌐 | `&#127760;` |
| MCP Integration | 🔌 | `&#128268;` |
| API Integration | 🔗 | `&#128279;` |
| Native App | 📱 | `&#128241;` |
| **Interface / Users** | | |
| Chat Interface | 💬 | `&#128172;` |
| Streamlit App | 🖥️ | `&#128421;` |
| Snowsight | 📈 | `&#128200;` |
| Business User | 👤 | `&#128100;` |
| Data Engineer | 👨‍💻 | `&#128104;` |
| Admin / DBA | 🔧 | `&#128295;` |
| **External Sources** | | |
| Web / Internet | 🌐 | `&#127760;` |
| Cloud Storage (S3/GCS/Azure) | ☁️ | `&#9729;` |
| Kafka / Streaming | 📡 | `&#128225;` |
| REST API | 🔗 | `&#128279;` |
| File Upload | 📁 | `&#128193;` |
| **Governance** | | |
| Masking Policy | 🔒 | `&#128274;` |
| Row Access Policy | 🛡️ | `&#128737;` |
| Tag | 🏷️ | `&#127991;` |
| Network Policy | 🔐 | `&#128272;` |

## Enhanced Icons (Snowflake Assets Repo)

For higher-fidelity diagrams, use PNG icons from the `snowflake-assets` repo.
To embed in draw.io, convert to base64 and use the `shape=image` style.

### Recommended Asset Mappings

| Concept | Asset File | Category |
|---------|-----------|----------|
| Database objects | `icon_database_*.png` | 54 icons |
| Data operations | `icon_data_*.png` | 117 icons |
| File types | `icon_filetype_*.png` | 21 icons |
| Actions/verbs | `icon_action_*.png` | 56 icons |
| Business domains | `icon_business_*.png` | 34 icons |
| Snowflake logo | `logo_logo_snowflake_blue.png` | Logos |
| Snowflake logo (SVG) | `graphic_snowflake_logo_blue.svg` | SVGs |

### How to Embed PNG Icons

1. Convert to base64: `base64 -i icon_file.png`
2. Use in draw.io style:
```
shape=image;verticalLabelPosition=bottom;labelBackgroundColor=default;
verticalAlign=top;aspect=fixed;imageAspect=0;
image=data:image/png;base64,{{BASE64_DATA}}
```

### Asset Repo Location

If the user has extracted the snowflake-assets repo, icons are at:
- PNG: `snowflake-assets-main/png/`
- SVG: `snowflake-assets-main/svg/`
- SVG (converted from PNG): `snowflake-assets-main/svg (converted)/`

## Color Assignment Rules

| Component Category | Border/Stroke | Fill Accent | Icon BG |
|-------------------|---------------|-------------|---------|
| Snowflake internal | `#29B5E8` | `#E8F6FC` | `#E8F6FC` |
| External / third-party | `#FF9F36` | `#FFF8ED` | `#FFF8ED` |
| Core agent / processing | `#11567F` | `#1A6B94` | `#11567F` |
| Accent / special | `#7254A3` | `#E8DCFF` | `#E8DCFF` |
| User / consumer | `#29B5E8` | `#E8F6FC` | `#E8F6FC` |
