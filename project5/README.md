## High Level Approach
The high level approach was to follow the steps laid out in the assignment. We began by adding a failure response to all gets and puts, then implemented the election protocol, and finally added a real implementation of getting and putting for the leader only, ignoring actual consensus which will be implemented in further version. The code is based around an event loop, which reads messages and delegates action for each message type to a corresponding function. If the receiver is a leader, it sends a heartbeat every tenth of a second. Global variables track leader/candidate/follower state as well as various other important state variables.


## Challenges 
Getting the election protocol in place was the primary challenge here. One bug that took a while to track down was a spontaneous reelection that was entered. The source of the bug was that the leader itself was initiating the reelection because it was timing out; because it was the leader it never received messages from the leader. We disabled the check on the leader and things proceeded smoothly. Additionally, though Raft is undoubtably easier to understand than Paxos, it still presented a challenge to understanding.

## Testing
Testing was done with print statements. A debug function that added replica id and timestamp information to log messages made life easier.

