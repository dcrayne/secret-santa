# Secret Santa Randomizer and Mailer

This is a simple console application which is intended to be used for 
[Secret Santa](https://en.wikipedia.org/wiki/Secret_Santa) events -
though it could be easily modified to work for similar event types (e.g. Yankee
Swap). The script takes a list of people and email addresses, and randomly
generates a giver-receiver pair for each person (as per Secret Santa rules,
each person is assigned to exactly one other person).

Once the results are generated, there are two ways for them to be discovered:
1. Each person is automatically emailed their assigned participant - if email 
addresses are given in _people.csv_ (see _Participants File_ section below 
for details).
2. A text file in the root directory (secret-santa) contains all results
(although this would ruin the suprise for whoever views it :)

## Configuration

The configuration file (_config.py_) is used to setup the email server which
will send the results. This file also allows you to customize the _from_ address
and email _subject_, as well as set the script to a testing mode (results are not
sent to the provided email addresses).

## Participants File
The event participants are contained in _people.csv_, which has the following
format:

```
participant1Name, participant1Email  
participant2Name, participant2Email  
participant3Name, participant3Email  
```

If you are not familiar with the format of Comma Separated Values (CSV) files, 
then the following should help:

Say we have a small get together with some of the characters from 
_Back to the Future_: Marty, Jennifer, Emmett, George, Lorraine, Griff, 
and Biff. We would create a file named '_people.csv_' in the root
(secret-santa) directory, and enter both the names and email addresses
of each participant as follows:

```
Marty,mcfly227@example.com
Jennifer,jparker@example.com
Emmett,docbrown@example.com
George,georgefly@example.com
Lorraine,lmcfly@example.com
Griff,tannen9738@example.com
Biff,btannen808@example.com
```

This csv file would represent the following table:

|Name    |Email                  |
|--------|-----------------------|
|Marty   |mcfly227@example.com   |
|Jennifer|jparker@example.com    |
|Emmett  |docbrown@example.com   |
|George  |georgefly@example.com  |
|Lorraine|lmcfly@example.com     |
|Griff   |tannen9738@example.com |
|Biff    |btannen808@example.com |

## Excluding Certain Pairs of Participants

Sometimes you may want to exclude pairs of participants, for example friends or
couples who will already be getting each other a gift. These pairs are 
defined in the _exclusions.csv_ file.

For example, if we don't want the following people to purchase each other gifts:
Emmet and Marty, Jennifer and Marty, George and Lorraine, Griff and Biff;
then we can add the following line to _exclusions.csv_:

```
Emmett,Marty
Jennifer,Marty
George,Lorraine
Griff,Biff
```

_Note: these exclusions can be entered in either direction, so "Emmett,Marty" is
 the same as "Marty,Emmett"._

## Usage

Once _people.csv_ and _config.py_ (and optionally _exclusions.csv_) are 
setup, the script is envoked with:

```
python secret_santa.py
```

You should see a line of output for each person in _people.csv_, indicating 
that the result has been sent to that person.

Enjoy!
