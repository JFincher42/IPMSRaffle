# IPMS Seattle Raffle
---------------------

# Raffle Story #

The IPMS Seattle Raffle selection has historically been down manually, using the following procedure:

- Tickets are sold from one or more ticket rolls.
	- Tickets are "bursted", or split into individual tickets for later draws.
	- Ticket bundles are usually pre-made before the show - single, five-packs, ten-packs, and twenty-packs are pre-made and ready to burst. 
- When tickets are sold, the bursted tickets are put in a central location for pulling.

When the raffle starts:

- Every 30 minutes, anywhere from 15-45 of all sold tickets are randomly pulled from the set.
	- The number of tickets pulled depends on the number of prizes to be awarded.
	- One ticket is a special "big prize winner" and is set aside.
	- The remaining tickets are the normal prize winners.
- The tickets are arranged in numerical order.
- Ticket numbers are copied onto a large notepad for people to see.
	- The big winner ticket is also copied and attached to the big prize for that draw.
- Anyone turning in a winning ticket is awarded a prize of their choosing, and the ticket number is removed from play.
	- Anyone turning in the winning ticket for a big prize gets that prize.
- Unclaimed winning tickets for the morning are wiped out after 1pm.

Throughout the day, a number of "for sale" items are also on display, which require someone to monitor, sell, and handle money.

This process of pulling and arranging tickets can take 10-15 minutes, and awarding prizes consumes the remaining time between pulls.  Selling tickets takes two people to run throughout the morning, and the raffle table requires at least three people at any time to handle ticket pulls, prize distribution, and table sales.


## Goals #
- Minimize the time it takes to:
	- Sell tickets by removing the bursting process.
	- Draw tickets by automating the process.
	- Show the winning tickets by automating the process.
	- Removing turned in winning tickets from play.
- Minimize the work involved in selling tickets, drawing winning tickets, and managing the prize distribution.

## Non-Goals #
- Decrease the cost of tickets.
- Increase the odds of winning.
- Handle the auctions.
- Replace tickets entirely

## New Process #
### Ticket Sales

At the point of sale, whenever a ticket is sold, the ticket number is entered into a central system.

- If a single ticket is sold, that single ticket number is entered.
- If a set of tickets are sold, the first and last ticket numbers are entered
	- This assumes that all tickets in a set are sequential.

Tickets can be bursted or not - no physical tickets will be pulled.  The buyer gets the tickets they purchased.

### Regular Ticket Draws

At regular intervals, a process is kicked off which will retrieve:

- A random set of tickets given a count of tickets required.
- Any special tickets ("big prize" items) required for that draw.

The set of tickets drawn are displayed on a large screen for contestants to view.

### Winning ticket processing

As winning tickets are turned in, raffle workers verify the ticket number with the winning number shown.  The winning number is removed from the board (perhaps by a single person, perhaps after the initial rush is over), and a prize is awarded.

### Winning Ticket number checks

The list of winning tickets is perpetual on the screen - winners from previous draws are shown throughout the day, until wiped clean.

*Optional*: People who purchased tickets can check to ensure their tickets are still live in the system, or have been won

## Scenarios

**Bundled Ticket Sale**: Jake is selling tickets for the IPMS Raffle.  A customer approaches and wants to purchase $10 worth of tickets.  Jake takes a ready-made bundle of tickets, and notes the first and last ticket number of the bundle in his IPMS Raffle system.  He takes the money and hands over the ticket bundle to the customer.

**Single Ticket Sale**: Susannah is selling tickets for the IPMS Raffle.  A customer approaches and wants a single raffle ticket.  Susannah takes a single ticket, and notes the ticket number in her IPMS Raffle system.  She takes the money and hands over the the single ticket to the customer.

**Regular Raffle Draw**: Roland is running the IPMS Raffle, and notes it is time for another raffle draw.  He asks ticket sales to hold while he starts the draw.  He goes to his IPMS Raffle system, and indicates he wants to draw 50 normal numbers, and one special number.  The process takes less than 10 seconds, and displays the winning numbers on the big screen for the current draw time, including the big prize winner.  Roland notes the big prize winning number and attaches it to the big prize, then he and his helpers begin processing winning tickets.

**Winning Ticket Processing**: Delta is helping at the IPMS Raffle.  A customer approaches with a winning ticket.  Delta checks the number on her IPMS Raffle system, and notes that it is a winner.  She marks it as turned in, disposes of the physical ticket, and helps the customer pick his prize.

**Non-winning Ticket Processing**: Eddie is helping at the IPMS Raffle.  A customer approaches with a winning ticket.  Eddie checks the number on his IPMS Raffle system, and notes that the number is not indicated as a winner.  He returns the ticket to the customer explaining that the ticket is not a winner.

**Customer Ticket check**: Henry purchased a set of IPMS Raffle tickets, and wonders if his tickets have won anything.  He goes to an IPMS Raffle system, and enters the first and last ticket number of his set.  The system informs him that his tickets are in the system, and that he has two winning tickets.  Henry goes to the raffle table to claim his prizes.

**Winning Ticket Wipe**: Roland notes that it's almost 1pm, and before the ticket draw, he needs to wipe the remaining winning numbers from the board.  He makes sure no customers are waiting to claim prizes, and when done, goes to the IPMS Raffle system to clear the current set of winners.  He notes that the winning tickets for the previous draws are now gone, but the special "big prize" numbers remain.  He is now set to begin the next draw.

## Features

- **Central data system**
	- Required to hold the ticket numbers which have been sold
	- Ticket operations must be atomic
- **Multiple access points**
	- Ticket sellers need an input interface to add ticket numbers.
	- Raffle draw needs an input interface to specify the number of tickets to draw, any specials, and start the draw.
	- Ticket processing needs a query interface to check for winning tickets and an input interface remove them from the customer display
	- Customers need a query-only interface to check their tickets are in play and whether they have any winners.
- **Multiple devices**
	- Ticket sales will need a device for ticket number entry.
	- Raffle draw need a device to kick off the draw.
	- Ticket processing needs a device to check tickets and remove winners.
	- Customers need a device to check ticket winners. 
- **Authentication**
	- Raffle workers need to be authenticated to add/remove ticket numbers from the central system.
	- Customers need to have only limited query capabilities.
- **Large display surface**
	- Customers will need to see the outstanding winning tickets for each draw. 

## Requirements

Web-based back-end data storage, with web pages for the various access points.  Hosting on Azure with proper authentication will allow any personal device to act as an input/query device.  A single device connected to the large screen can be kept running to show the current winning ticket backlog.