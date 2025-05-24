# For You Section Data

This directory contains the data used in the "For You" section of DevBase. The data is stored in a structured JSON format to make it easy to add, update, or remove content.

## File Structure

- `forYouData.json`: The main data file containing all events, announcements, and filter options.

## Data Structure

The `forYouData.json` file contains the following sections:

### Metadata

```json
"metadata": {
  "lastUpdated": "YYYY-MM-DD",
  "version": "1.0.0"
}
```

- `lastUpdated`: Date when the data was last updated (YYYY-MM-DD format)
- `version`: Version number of the data structure

### Featured Events

```json
"featuredEvents": [
  {
    "id": "event-001",
    "title": "Event Title",
    "description": "Event description...",
    "date": "YYYY-MM-DD",
    "location": "Location",
    "imageUrl": "URL to event image",
    "registrationUrl": "URL to registration page",
    "tags": ["tag1", "tag2"],
    "isFeatured": true,
    "organizer": "Organizer name",
    "attendees": 1500
  }
]
```

Featured events are displayed prominently at the top of the "For You" page. Each featured event should have:

- `id`: Unique identifier for the event (format: "event-XXX")
- `title`: Event title (max 60 characters)
- `description`: Brief description of the event (max 200 characters)
- `date`: Event date in YYYY-MM-DD format
- `location`: Physical location or "Online"
- `imageUrl`: URL to a high-quality image (recommended: 1200×630px)
- `registrationUrl`: URL to the registration or information page
- `tags`: Array of relevant tags (lowercase, hyphenated for multi-word tags)
- `isFeatured`: Should always be `true` for featured events
- `organizer`: Name of the organizing entity
- `attendees`: Expected or past number of attendees

### Regular Events

```json
"events": [
  {
    "id": "event-002",
    "title": "Event Title",
    "description": "Event description...",
    "date": "YYYY-MM-DD",
    "location": "Location",
    "imageUrl": "URL to event image",
    "registrationUrl": "URL to registration page",
    "tags": ["tag1", "tag2"],
    "isFeatured": false,
    "organizer": "Organizer name",
    "attendees": 500
  }
]
```

Regular events are displayed in the events grid. They have the same structure as featured events, but with `isFeatured` set to `false`.

### Announcements

```json
"announcements": [
  {
    "id": "announcement-001",
    "title": "Announcement Title",
    "content": "Announcement content...",
    "date": "YYYY-MM-DD",
    "type": "feature",
    "link": "/some-link",
    "isHighlighted": true
  }
]
```

Announcements are displayed in the announcements section. Each announcement should have:

- `id`: Unique identifier for the announcement (format: "announcement-XXX")
- `title`: Announcement title (max 60 characters)
- `content`: Announcement content (max 150 characters)
- `date`: Publication date in YYYY-MM-DD format
- `type`: Type of announcement (one of: "feature", "community", "maintenance", "update")
- `link`: URL or path to more information
- `isHighlighted`: Whether the announcement should be highlighted (true/false)

### Filters

```json
"filters": [
  {
    "id": "filter-id",
    "label": "Filter Label",
    "icon": "IconName"
  }
]
```

Filters are used to categorize and filter events. Each filter should have:

- `id`: Unique identifier for the filter (lowercase, hyphenated)
- `label`: Display name for the filter
- `icon`: Name of the Lucide icon to use (must match an icon name from lucide-react)

## Adding New Content

### To add a new event:

1. Create a new event object with a unique `id`
2. Add all required fields as described above
3. Set `isFeatured` to `true` if it should be a featured event, or `false` for a regular event
4. Add the event to either the `featuredEvents` or `events` array

### To add a new announcement:

1. Create a new announcement object with a unique `id`
2. Add all required fields as described above
3. Add the announcement to the `announcements` array

### To add a new filter:

1. Create a new filter object with a unique `id`
2. Add the `label` and `icon` fields
3. Add the filter to the `filters` array

## Best Practices

1. Always update the `lastUpdated` field in the metadata when making changes
2. Ensure all IDs are unique across the entire file
3. Use high-quality images for events (optimize for web)
4. Keep descriptions concise and informative
5. Use consistent formatting for dates (YYYY-MM-DD)
6. Test the UI after making significant changes to ensure proper display

## Icon Reference

The `icon` field in filters should use names from the [Lucide React](https://lucide.dev/) icon library. Common icons include:

- `Globe` - For global or general events
- `Blocks` - For Web3/blockchain events
- `Brain` - For AI/ML events
- `Users` - For community or conference events
- `Laptop` - For workshops or hackathons
- `Calendar` - For scheduled events
- `Award` - For competitions or awards
- `BookOpen` - For educational events
