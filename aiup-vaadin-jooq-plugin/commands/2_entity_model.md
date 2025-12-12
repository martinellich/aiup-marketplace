Create an entity model (docs/entity_model.md) based on docs/requirements.md as a Markdown file.

STRUCTURE REQUIREMENTS:

1. Start with a level-1 heading "# Entity Model"
2. Add a level-2 heading "## Entity Relationship Diagram"
3. Add a Mermaid erDiagram code block showing entity names and relationships only (no columns)
4. For each entity, add a level-3 heading with the entity name
5. Below each heading, add a short description paragraph
6. Below the description, add a table with columns: Attribute, Description, Data Type, Length/Precision, Validation
   Rules

TABLE REQUIREMENTS:

- By default, use sequences for primary keys (Long, 19 digits)
- Include validation rules like Not Null, unique constraints, allowed values
- Add notes for multi-column validation rules below the table

EXAMPLE TABLE FORMAT:
| Attribute | Description | Data Type | Length/Precision | Validation Rules |
|------------|---------------------------------|-----------|------------------|------------------|
| id | Unique identifier of the entity | Long | 19 | Primary Key |
| first_name | First name of the person | String | 50 | Not Null |