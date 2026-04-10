# PDGB01 - Documentation

This directory contains comprehensive documentation for the Airtable base.

## Files

- **SCHEMA.md** - Complete database schema including all tables, fields, and relationships
- **AUTOMATIONS.md** - Documentation of all automation workflows
- **DESIGN_REVIEW.md** - Database design analysis and recommendations

## Updating Documentation

### Automated Updates (Schema)
Run the documentation script to automatically update schema:
```bash
python airtable_documenter.py
```

### Manual Updates (Automations)
Update AUTOMATIONS.md manually when you:
- Create new automations
- Modify existing automations
- Add or update automation scripts

## Best Practices

- Review DESIGN_REVIEW.md regularly for optimization opportunities
- Keep automation documentation in sync with actual automations
- Document the purpose and business logic behind automations
- Version control automation scripts separately if complex

