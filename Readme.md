# Rick and Morty GraphQL Character Queries

This project contains GraphQL queries to fetch character data from the Rick and Morty API using their GraphQL endpoint.

## API Endpoint

```
https://rickandmortyapi.com/graphql
```

## Project Structure

```
Character/
├── character-id-1.graphql          # GraphQL query for Rick Sanchez (ID: 1)
├── character-id-1-output.json      # Expected response for Rick Sanchez
├── character-id-2.graphql          # GraphQL query for Morty Smith (ID: 2)
├── character-id-2-output.json      # Expected response for Morty Smith
├── character-id-3.graphql          # GraphQL query for Summer Smith (ID: 3)
├── character-id-3-output.json      # Expected response for Summer Smith
├── character-id-4.graphql          # GraphQL query for Beth Smith (ID: 4)
├── character-id-4-output.json      # Expected response for Beth Smith
└── README.md                       # This file
```

## Character Information

| ID | Name | Status | Species | Gender |
|----|------|--------|---------|--------|
| 1  | Rick Sanchez | Alive | Human | Male |
| 2  | Morty Smith | Alive | Human | Male |
| 3  | Summer Smith | Alive | Human | Female |
| 4  | Beth Smith | Alive | Human | Female |

## Query Structure

Each GraphQL file contains a query fragment that fetches the following fields for a character:

- `id` - Character ID
- `name` - Character name
- `status` - Life status (Alive, Dead, Unknown)
- `species` - Character species
- `type` - Character subspecies or type
- `gender` - Character gender

### Example Query Format

```graphql
query GetCharacter {
  character1: character(id: 1) {
    id
    name
    status
    species
    type
    gender
  }
}
```

## How to Use

### 1. Using GraphQL Playground

1. Open [Rick and Morty GraphQL Playground](https://rickandmortyapi.com/graphql)
2. Copy the content from any `.graphql` file
3. Wrap it in a complete query (add `query GetCharacter { }` around the fragment)
4. Execute the query

### 2. Using curl

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{
    "query": "query GetCharacter { character1: character(id: 1) { id name status species type gender } }"
  }' \
  https://rickandmortyapi.com/graphql
```

### 3. Using Postman

1. Set method to `POST`
2. Set URL to `https://rickandmortyapi.com/graphql`
3. Set header `Content-Type: application/json`
4. In body, add:
```json
{
  "query": "query GetCharacter { character1: character(id: 1) { id name status species type gender } }"
}
```

### 4. Using JavaScript/Node.js

```javascript
const query = `
  query GetCharacter {
    character1: character(id: 1) {
      id
      name
      status
      species
      type
      gender
    }
  }
`;

fetch('https://rickandmortyapi.com/graphql', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({ query })
})
.then(response => response.json())
.then(data => console.log(data));
```

## Expected Response Format

All queries return data in the following JSON structure:

```json
{
  "data": {
    "character1": {
      "id": "1",
      "name": "Rick Sanchez",
      "status": "Alive",
      "species": "Human",
      "type": "",
      "gender": "Male"
    }
  }
}
```

## Available Tools

### GraphQL Clients
- [GraphQL Playground](https://rickandmortyapi.com/graphql)
- [Apollo Studio](https://studio.apollographql.com/)
- [Insomnia](https://insomnia.rest/)
- [Postman](https://www.postman.com/)

### Libraries
- JavaScript: `graphql-request`, `apollo-client`
- Python: `gql`, `requests`
- PHP: `lighthouse-php/lighthouse`
- Java: `graphql-java`

## Notes

- The `type` field is often empty for main characters
- All main family characters have "Human" as their species
- The API is read-only and doesn't require authentication
- Rate limiting may apply for excessive requests

## API Documentation

For complete API documentation, visit: [https://rickandmortyapi.com/documentation](https://rickandmortyapi.com/documentation)

## Contributing

To add more character queries:

1. Create a new `.graphql` file following the naming pattern `character-id-{ID}.graphql`
2. Create corresponding `-output.json` file with expected response
3. Update this README with character information
4. Test the query against the live API

## License

This project is for educational purposes. The Rick and Morty API is free to use and doesn't require attribution.