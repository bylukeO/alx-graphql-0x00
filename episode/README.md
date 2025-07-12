# Rick and Morty Episode 1 (Pilot) GraphQL Query

This folder contains GraphQL query to fetch Episode 1 data from the Rick and Morty API using their GraphQL endpoint.

## API Endpoint

```
https://rickandmortyapi.com/graphql
```

## Files

```
├── episode-id-1.graphql         # GraphQL query for Pilot episode
├── episode-id-1-output.json     # Expected response for Pilot episode
└── README.md                    # This file
```

## Episode Information

| Field | Value |
|-------|-------|
| **ID** | 1 |
| **Name** | Pilot |
| **Air Date** | December 2, 2013 |
| **Episode Code** | S01E01 |
| **Season** | 1 |

## Query Structure

The GraphQL query fetches the following fields for Episode 1:

- `id` - Episode ID (1)
- `name` - Episode title ("Pilot")
- `air_date` - Original broadcast date
- `episode` - Season and episode code (S01E01)

### GraphQL Query

```graphql
query GetEpisode1 {
  episode(id: 1) {
    id
    name
    air_date
    episode
  }
}
```

## How to Use

### 1. Using GraphQL Playground

1. Open [Rick and Morty GraphQL Playground](https://rickandmortyapi.com/graphql)
2. Copy the query from `episode-id-1.graphql`
3. Execute the query

### 2. Using curl

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{
    "query": "query GetEpisode1 { episode(id: 1) { id name air_date episode } }"
  }' \
  https://rickandmortyapi.com/graphql
```

### 3. Using JavaScript

```javascript
const query = `
  query GetEpisode1 {
    episode(id: 1) {
      id
      name
      air_date
      episode
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

## Expected Response

```json
{
  "data": {
    "episode": {
      "id": "1",
      "name": "Pilot",
      "air_date": "December 2, 2013",
      "episode": "S01E01"
    }
  }
}
```

## About the Pilot Episode

The **Pilot** episode is the series premiere of Rick and Morty that aired on December 2, 2013. In this episode:

- Rick Sanchez moves in with his daughter Beth's family
- Rick takes his grandson Morty on his first interdimensional adventure
- The family dynamics and Rick's chaotic influence are established
- Morty's legs are broken in an alternate dimension
- The series' tone and style are introduced

This episode sets up the core premise of the show and introduces viewers to the main characters and the concept of interdimensional travel.

## Extended Query Options

If you want more information about the pilot episode, you can extend the query to include:

```graphql
query GetEpisode1Extended {
  episode(id: 1) {
    id
    name
    air_date
    episode
    characters {
      id
      name
    }
    url
    created
  }
}
```

## Notes

- This is the very first episode of Rick and Morty
- It established the show's unique animation style and dark humor
- The episode aired on Adult Swim's late-night programming block
- It introduced the portal gun concept that becomes central to the series

## License

This project is for educational purposes. The Rick and Morty API is free to use and doesn't require attribution.