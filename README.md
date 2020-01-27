## The Game

Consider a points system that operates on time-based intervals with the following rules:

- Every interval, 1 new point is distributed among players that are active within that interval.
- Players are active within an interval if they have money spent in that interval. 
- If a player spends money in an interval, the amount is spread over N intervals.
- The player chooses how the amount gets spread over N intervals, the only requirement is that each amount is non-zero.
- N is fixed for all players of the game. 
- The 1 point for each interval is distributed proportional to the amount spent by each player in that interval.
- If a player is inactive for one or more interval, the number of points they have resets to zero. 

Suppose N=4 and Alice wishes to spend $1. The money could be spent across each interval in any of the following example ways:
- [ $0.25, $0.25, $0.25, $0.25 ]
- [ $0.45, $0.20, $0.30, $0.05 ]
- [ $0.97, $0.01, $0.01, $0.01 ]

## The challenge
For each interval, what is the most storage-efficient way to track the total number of points among all active players during that interval? Solutions must have a storage overhead of O(C*N) or less, where N is the number of intervals that a spent amount is spread across and C is some constant factor.

## Example

Imagine the following scenario, where Alice spends $1, Bob spends $1, and Carol spends $1.75:

Interval        1       2       3       4       5       6       7
Alice           $0.25   $0.25   $0.25   $0.25
Bob                     $0.25   $0.25   $0.25   $0.25
Carol                   $0.50   $0.50   $0.50   $0.25

For interval 1, the total is 1 point (Alice: 1)
For interval 2, the total is 2 points (Alice: 1.25, Bob: 0.25, Carol: 0.50)
For interval 3, the total is 3 points (Alice: 1.50, Bob: 0.50, Carol: 1)
For interval 4, the total is 4 points (Alice: 1.75, Bob: 0.75, Carol: 1.50)
For interval 5, the total is 3.25 points (Bob: 1.25, Carol: 2)
For interval 6, the total is 0 points