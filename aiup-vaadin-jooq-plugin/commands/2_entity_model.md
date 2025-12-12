Create an entity model (docs/entity_model.md) based on docs/requirements.md as a Markdown file.

DOCUMENT STRUCTURE:

1. Start with "# Entity Model"
2. Add "## Entity Relationship Diagram" with a Mermaid erDiagram code block
3. For each entity, add a level-3 heading, a description, and an attribute table

MERMAID DIAGRAM REQUIREMENTS:

- Show entity names and relationships only
- Do NOT add columns/attributes to the diagram
- Use this syntax style:
  ROOM_TYPE ||--o{ ROOM : "categorizes"
  GUEST ||--o{ RESERVATION : "makes"

CRITICAL - ATTRIBUTE TABLES ARE REQUIRED:
For EACH entity, you MUST create a Markdown table listing ALL attributes.
Do NOT write prose descriptions only.
Do NOT skip the attribute tables.
Do NOT use a "Primary Key:" line - put it in the table instead.

Each entity section MUST contain:

1. A level-3 heading with the entity name (e.g., ### ROOM_TYPE)
2. One sentence describing the entity's purpose
3. An attribute table with EXACTLY these columns:
   | Attribute | Description | Data Type | Length/Precision | Validation Rules |

VALIDATION RULES REQUIREMENTS:
The Validation Rules column must NEVER be empty. For each attribute, determine:

- Primary Key, Sequence: For id columns
- Not Null: For required fields
- Unique: For fields that must be unique
- Length constraints: Max length for strings
- Value constraints: Allowed values (e.g., "Values: Active, Inactive")
- Range constraints: Min/max for numbers (e.g., "Min: 0, Max: 100")
- Format constraints: Patterns for emails, phone numbers
- Foreign Key: References to other entities
- Optional: For nullable fields with no other rules

If requirements.md does not state validation rules explicitly, derive sensible defaults from the attribute name and
domain context.

MULTI-COLUMN VALIDATION:
After each entity table, add a "**Constraints:**" line if validation rules span multiple columns.
Example: "**Constraints:** Check-out date must be after check-in date."

PRIMARY KEYS:
By default, use sequences for primary keys (Long, 19 digits).

EXAMPLE - This is the REQUIRED format:

### ROOM_TYPE

Defines categories of rooms with shared characteristics.

| Attribute   | Description              | Data Type | Length/Precision | Validation Rules          |
|-------------|--------------------------|-----------|------------------|---------------------------|
| id          | Unique identifier        | Long      | 19               | Primary Key, Sequence     |
| name        | Name of the room type    | String    | 50               | Not Null, Unique          |
| description | Detailed description     | String    | 500              | Optional                  |
| capacity    | Maximum number of guests | Integer   | 10               | Not Null, Min: 1, Max: 10 |
| price       | Price per night in CHF   | Decimal   | 10,2             | Not Null, Min: 0          |

YOU MUST create a similar table for EVERY entity found in the requirements.
Derive the attributes from the requirements document.