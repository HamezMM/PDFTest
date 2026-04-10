# PDGB01 - Automations

**Last Updated:** 2026-04-09 21:53:00  

## Overview

This document tracks all automations configured in this base.

### How to Update

1. Open the Automations tab in Airtable
2. For each automation, document it below using the template
3. Include trigger conditions and all actions

---

## Automation Template

```markdown
### Automation Name: [Name]

**Status:** Active/Inactive  
**Trigger:** [When a record is created/updated/matches conditions/scheduled time]  
**Table:** [Table Name]  
**Conditions:** [Describe any conditions]  

**Actions:**
1. [Action type] - [Description]
2. [Action type] - [Description]

**Purpose:** [Why this automation exists]

**Script (if applicable):**
```javascript
// Paste any automation scripts here
```
```

---

## Documented Automations

### Example: New Contact Notification

**Status:** Active  
**Trigger:** When a record is created  
**Table:** Contacts  
**Conditions:** None  

**Actions:**
1. Send email - Notify sales team of new contact
2. Update record - Set 'Notified' field to true

**Purpose:** Ensure sales team is immediately aware of new contacts

