# Blackjack

A command-line implementation of the classic card game Blackjack (21) written in Go.

## Overview

This Blackjack game is a simple yet complete implementation of the popular casino card game. It allows users to play against a computer dealer following standard Blackjack rules. The game demonstrates practical usage of Go programming concepts and serves as an educational example of game logic implementation.

## Features

- Complete Blackjack game logic
- Command-line interface
- Computer dealer with configurable AI
- Betting system
- Game statistics tracking
- Multiple player support
- Configurable rule variations

## Installation

```bash
go get github.com/laureanorios95/blackjack
```

## Usage

### Running the Game

```bash
# Install and run
go install github.com/laureanorios95/blackjack
blackjack

# Or run directly
go run github.com/laureanorios95/blackjack
```

### Command-line Flags

```bash
blackjack -decks=3       # Play with 3 decks
blackjack -players=2     # Play with 2 players
blackjack -stand=17      # Dealer stands on 17
blackjack -blackjack=3:2 # Blackjack pays 3:2
```

## Game Rules

- The goal is to have a hand value closer to 21 than the dealer without going over
- Number cards are worth their face value
- Face cards (Jack, Queen, King) are worth 10
- Aces are worth 1 or 11, whichever is more favorable
- Dealer must hit until they have at least 17
- Blackjack (an Ace and a 10-value card) pays 3:2

## Example Game

```
Welcome to Blackjack!
Starting with $100

Your cards: [♥10 ♦5]
Dealer shows: [♣K]

[H]it, [S]tand, or [Q]uit: h

Your cards: [♥10 ♦5 ♠4]
Dealer shows: [♣K]

[H]it, [S]tand, or [Q]uit: s

Your final hand: [♥10 ♦5 ♠4] (Value: 19)
Dealer's hand: [♣K ♠7] (Value: 17)

You win! +$10
Current balance: $110

Deal again? (y/n): 
```

## Project Structure

```
blackjack/
├── main.go              # Entry point
├── game/                # Game logic
│   ├── game.go          # Core game functionality
│   ├── player.go        # Player implementation
│   └── dealer.go        # Dealer AI implementation
├── ui/                  # User interface
│   └── terminal.go      # Terminal UI implementation
├── rules/               # Game rules
│   └── rules.go         # Rule variations and configurations
└── util/                # Utility functions
    └── util.go          # Helper functions
```

## Dependencies

This project uses:
- [github.com/laureanorios95/deck](https://github.com/laureanorios95/deck) - Card deck manipulation library

## Advanced Usage

### Custom Rule Sets

```go
import "github.com/laureanorios95/blackjack/rules"

// Create a European Blackjack ruleset
europeanRules := rules.New(
    rules.WithDealerPeek(false),
    rules.WithSurrender(false),
    rules.WithBlackjackPayout(3, 2),
)

game := blackjack.NewGame(europeanRules)
```

### Creating a Custom UI

```go
import "github.com/laureanorios95/blackjack/ui"

// Implement the UI interface
type MyCustomUI struct {
    // Custom fields
}

// Implement required methods
func (ui *MyCustomUI) DisplayHand(hand []deck.Card) {
    // Custom display logic
}

// Use your custom UI
game := blackjack.NewGame(rules.Default(), &MyCustomUI{})
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Author

Jon Calhoun - [gophercises.com](https://gophercises.com/)

## Acknowledgments

- Inspired by the Blackjack exercise from Gophercises
- Thanks to all contributors and testers
