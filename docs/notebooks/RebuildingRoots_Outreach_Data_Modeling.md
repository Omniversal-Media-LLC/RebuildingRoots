# Rebuilding Roots Outreach Data Modeling

*Supporting the EM.B.R.A.C.E. Networking Web*

This notebook is a planning and prototyping space to define, model, and export data about our partner network. Our goal is to create a clear, consistent, and trauma-informed format for partner profiles that can be used throughout the repo.

Theme: Regeneration. Clarity. Real-world readiness.  
Soundtrack: Nahko - *Take Your Power Back* 🎶

## 🌱 Purpose

- Define the data model for partner profiles
- Test and refine categories and fields
- Generate example data
- Prepare for export to CSV or JSON for use in the repo

## ✨ Goals

✅ Build consistent partner records  
✅ Support category-based organization  
✅ Enable easy Markdown generation later  
✅ Ensure trauma-informed, sustainable language and framing

```python
# Basic imports
import pandas as pd
import json

print("Environment ready for data modeling ✨")

```
## 📜 Draft Partner Profile Fields

Let's brainstorm the initial set of fields for each partner.

**Required fields**:
- name
- contact_email
- category
- mission_statement
- trauma_informed_practices
- partnership_vision
- notes

**Optional fields**:
- phone
- website
- social_links
- address
- active_projects

```python
# Define the partner schema as a list of fields
partner_fields = [
    "name",
    "contact_email",
    "category",
    "mission_statement",
    "trauma_informed_practices",
    "partnership_vision",
    "notes",
    "phone",
    "website",
    "social_links",
    "address",
    "active_projects"
]

print("Partner schema fields defined:")
for field in partner_fields:
    print(f"- {field}")

```
```python
# Create a sample DataFrame with one example partner
example_data = [{
    "name": "Hotbox Outreach",
    "contact_email": "contact@hotboxoutreach.org",
    "category": "Outreach / Harm Reduction",
    "mission_statement": "Reducing harm through direct outreach and mutual aid.",
    "trauma_informed_practices": "Consent-based service, active listening, peer leadership.",
    "partnership_vision": "Collaborate on regenerative community projects.",
    "notes": "High priority partner for pilot model.",
    "phone": "555-555-1234",
    "website": "https://hotboxoutreach.org",
    "social_links": "https://instagram.com/hotboxoutreach",
    "address": "N/A",
    "active_projects": "Mobile outreach, safe use kits."
}]

df_partners = pd.DataFrame(example_data)
df_partners

```
```python
# Export example data
df_partners.to_csv("example_partners.csv", index=False)
with open("example_partners.json", "w") as f:
    json.dump(example_data, f, indent=2)

print("Example data saved as CSV and JSON ✅")

```
## 🪷 Reflections & Next Steps

- Review schema with Renee and Sage
- Add categories for grouping partners
- Create bulk import templates
- Build Markdown generator using this data

*“Take Your Power Back.” - Remember the vision. Stay aligned.* 🎶

```python
# Add a few more sample partners
more_example_data = [
    {
        "name": "Rebuilding Roots Sanctuary",
        "contact_email": "hello@rebuildingroots.org",
        "category": "Land-based Regeneration",
        "mission_statement": "Providing a trauma-informed, sustainable refuge and teaching site.",
        "trauma_informed_practices": "Consensus decision-making, healing circles, reciprocal care.",
        "partnership_vision": "Co-develop training and land projects with allied orgs.",
        "notes": "Foundational partner.",
        "phone": "",
        "website": "https://rebuildingroots.org",
        "social_links": "",
        "address": "",
        "active_projects": "Sanctuary site planning, outreach pilot."
    },
    {
        "name": "Omniversal Media",
        "contact_email": "contact@omniversalmedia.org",
        "category": "Media / Storytelling",
        "mission_statement": "Supporting authentic narrative and regenerative communication.",
        "trauma_informed_practices": "Consent-based interviews, participant review.",
        "partnership_vision": "Share stories of partner work and amplify outreach.",
        "notes": "Handles podcast + documentary planning.",
        "phone": "",
        "website": "https://omniversalmedia.org",
        "social_links": "",
        "address": "",
        "active_projects": "Podcast series, partner video profiles."
    }
]

# Append to the existing example
example_data.extend(more_example_data)
df_partners = pd.DataFrame(example_data)
df_partners

```
```python
# Group partners by category
df_partners.groupby("category").size()

```
```python
# Filter by a category
outreach_partners = df_partners[df_partners["category"].str.contains("Outreach", case=False)]
outreach_partners

```
## 🗂️ Partner Categories

Let's clarify categories for consistent use:

- Outreach / Harm Reduction
- Land-based Regeneration
- Media / Storytelling
- Education / Training
- Mutual Aid / Direct Support
- Art / Culture
- Policy / Advocacy

```python
# Check for missing categories
df_partners[df_partners["category"].isnull() | (df_partners["category"] == "")]

```
```python
# Add a tags column to support multiple labels
df_partners["tags"] = [
    "harm reduction, mutual aid",
    "regeneration, land, sanctuary",
    "media, storytelling, outreach"
]

df_partners

```
```python
# Save updated multi-partner dataset
df_partners.to_csv("partners_dataset.csv", index=False)
with open("partners_dataset.json", "w") as f:
    json.dump(example_data, f, indent=2)

print("Full partner dataset saved ✅")

```
