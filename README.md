LHL Node Skeleton
=========

## Project Setup

1. Create your own empty repo on GitHub, ideally using the name of your project
2. Clone this repository (<mark>do not fork!</mark>)
  - When cloning, specify a different folder name that is relevant to your project
3. Remove the git remote: `git remote rm origin`
4. Add a remote for your origin: `git remote add origin <your github repo URL>`
5. Push to the new origin: `git push -u origin master`
6. Verify that the skeleton code now shows up in your repo on GitHub

## Getting Started

1. Create the `.env` by using `.env.example` as a reference: `cp .env.example .env`
2. Update the .env file with your correct local information 
  - username: `labber` 
  - password: `labber` 
  - database: `midterm`
3. Install dependencies: `npm i`
4. Fix to binaries for sass: `npm rebuild node-sass`
5. Reset database: `npm run db:reset`
  - Check the db folder to see what gets created and seeded in the SDB
7. Run the server: `npm run local`
  - Note: nodemon is used, so you should not have to restart your server
8. Visit `http://localhost:8080/`

## Warnings & Tips

- Do not edit the `layout.css` file directly, it is auto-generated by `layout.scss`
- Split routes into their own resource-based file names, as demonstrated with `users.js` and `widgets.js`
- Split database schema (table definitions) and seeds (inserts) into separate files, one per table. See `db` folder for pre-populated examples. 
- Use the `npm run db:reset` command each time there is a change to the database schema or seeds. 
  - It runs through each of the files, in order, and executes them against the database. 
  - Note: you will lose all newly created (test) data each time this is run, since the schema files will tend to `DROP` the tables and recreate them.

## Dependencies

- Node 10.x or above
- NPM 5.x or above
- PG 6.x

2 player game

The objective of the game is to accumulate the most value in prizes by strategically bidding on them.

Each player has 13 tokens valued from 1 to 13 respectively. Each round, the players use one of their tokens to make a secret bid on a randomly chosen prize, each valued from 1 to 13 and shown to all players. After each player has made their secret bid, the bids are revealed with the highest value token winning the prize and the tokens used to bid discarded. No one wins the prize if the bids are tied.

The game continues with the next round revealing another randomly chosen prize from the remaining prize pool until there are no more tokens (or prizes) left.

The winner is the player with the highest value of prizes won.

Each suit is ranked A (low), 2, ..., 10, J, Q, K (high).
One suit is singled out as the "prizes"; each of the remaining suits becomes a hand for one player, with one suit discarded if there are only two players, or taken from additional decks if there are four or more. The prizes are shuffled and placed between the players with one card turned up.
Play proceeds in a series of rounds. The players make "closed bids" for the top (face up) prize by selecting a card from their hand (keeping their choice secret from their opponent). Once these cards are selected, they are simultaneously revealed, and the player making the highest bid takes the competition card. Rules for ties in the bidding vary, possibilities including the competition card being discarded, or its value split between the tied players (possibly resulting in fractional scores). Some play that the current prize may "roll over" to the next round, so that two or more cards are competed for at once with a single bid card.
The cards used for bidding are discarded, and play continues with a new upturned prize card.
After 13 rounds, there are no remaining cards and the game ends. Typically, players earn points equal to sum of the ranks of cards won (i.e. ace is worth one point, 2 is two points, etc., jack 11, queen 12, and king 13 points). Players may agree upon other scoring schemes.
