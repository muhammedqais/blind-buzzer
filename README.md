# Blind Buzzer

A party game about feeling time. Each round names a target, say **20 seconds**.
You tap to start a hidden clock and tap again when you think the time is up.
Nothing on screen moves while it runs. Whoever stops closest to the target
takes the round; most rounds won takes the game (ties broken by total error).

## Play it

Open `index.html` from any web host (GitHub Pages works as is). No build
step, no server, no accounts.

**Online room.** One person taps *Online room*, picks the number of players,
rounds and the longest target (a dial from 10s to 60s), and gets a 4-letter
code. Friends open the same link, type a name and the code, and the game
starts the moment the room is full. Everyone plays each round on their own
phone; a round is revealed once every time is in. Rooms are peer to peer over
WebRTC (PeerJS): the creator's browser runs the room, so the host keeps the
page open until the game ends. If a player drops, anyone can tap *Skip* next
to their name, and a player who rejoins with the same code picks up where
they were.

**One device.** Pass a phone around. Players take turns on the same target;
every time stays sealed until the last player in the round has gone.

**Solo.** Play alone. Every round scores at once and the game keeps your best
average error on the device.

A reload never loses a game: hosts reopen their room, guests rejoin it, and
one-device and solo games pick up where they were.

## Rules

- Target style is chosen per game: **Whole seconds** (1 up to the dial),
  **Fractions** (under a second, 0.05 to 0.99) or **Mixed** (two in three whole,
  one in three fractions). None repeats in a game.
- Every player in a round gets the same target.
- Closest absolute error wins the round. Equal errors share the point.
- Final order: round points, then lowest total error.

## Files

- `index.html` – the whole game. PeerJS loads from a CDN; everything else
  is inline.

## Running locally

Open `index.html` in a browser. For a phone on the same Wi-Fi, serve the
folder (`python3 -m http.server`) and open the computer's address on the
phone.
