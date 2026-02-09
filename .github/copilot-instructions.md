# Copilot Instructions: Basketball Stats Tracker Lab

## Project Overview
This is a Flatiron School foundational JavaScript lab focused on **object and array iteration** patterns. The goal is implementing functions that query nested game data without modifying the data structure.

## Data Structure Pattern
The `gameObject()` returns a two-level nested structure:
```javascript
{
  home: { teamName: "...", colors: [...], players: { "Name": { points, shoe, ... } } },
  away: { teamName: "...", colors: [...], players: { "Name": { points, shoe, ... } } }
}
```

## Core Implementation Pattern
All functions follow these constraints:
1. **Search through both teams**: Use `Object.values(gameObject())` to iterate both `home` and `away` teams
2. **Find players by name**: Access `team.players[playerName]` to get player objects
3. **Extract nested properties**: Return specific stats (points, shoe, etc.) from player objects
4. **No data mutation**: Functions are read-only queries

## Key Function Implementations

### Search Functions (search by player name across all teams)
- `numPointsScored(playerName)` - Use `reduce()` or nested loops to find player's `points` property
- `shoeSize(playerName)` - Find player's `shoe` property across teams
- `playerStats(playerName)` - Return entire player object with all stats

### Filter Functions (extract team data)
- `teamColors(teamName)` - Match team by `teamName` property, return `colors` array
- `teamNames()` - Extract `teamName` from both teams into array
- `playerNumbers(teamName)` - Extract `number` from each player in matching team

### Aggregation Function (comparison across players)
- `bigShoeRebounds()` - Find player with max `shoe` value using `Math.max()` or sorting, return their `rebounds`

## Testing & Validation
Run tests with: `npm test`
Tests use Mocha with Chai assertions - check `test/indexTest.js` for expected outputs and edge cases.

## Common Pitfall: Finding Players vs Teams
- **Player lookup**: `Object.values(gameObject()).forEach(team => { ... team.players[playerName] ... })`
- **Team lookup**: `Object.values(gameObject()).find(team => team.teamName === teamName)`
