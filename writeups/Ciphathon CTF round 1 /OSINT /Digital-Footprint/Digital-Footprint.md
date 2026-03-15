The Digital Footprint

CTF: Cipathon'26 round 1 

Category: OSINT

Difficulty: Easy

Solved by: Hector1516 & imsaksham24

Challenge Description

"I am the man who hacked the world's most secure network in 1983 from my bedroom. My nickname was inspired by a movie released the same year."
During the early days of hacking culture, one individual became famous for breaking into highly secure computer systems from his bedroom. His exploits in the 1980s made him one of the most well-known hackers in history. This hacker used a nickname inspired by a movie with a similar title. Your job is to identify this hacker's alias.
Flag Format: CIPH{ALIAS}


Approach
Started broad and narrowed down using two parallel search threads:

Famous hackers from the 1980s — pulled up a list of notable figures from early hacking culture
Movies released in 1983 — cross-referenced to find one that could inspire a hacker alias

Also searched for what was considered the most secure network in 1983 to further anchor the target.

Solving
The combination of clues — bedroom hacking, 1983, highly secure network — pointed strongly to Kevin Mitnick, one of the most infamous hackers in history.
Mitnick's well-documented alias was "The Condor", taken from the 1975 Robert Redford film Three Days of the Condor. The alias fit the 1983 timeframe of his early exploits and matched the movie-inspired nickname hint in the description.

Flag
CIPH{CONDOR}

Key Takeaway
Classic OSINT methodology — start with a broad search, identify overlapping criteria (era + movie + alias), and triangulate to a single answer. Kevin Mitnick is a well-documented figure, so cross-referencing a few sources was enough to confirm the alias confidently.
