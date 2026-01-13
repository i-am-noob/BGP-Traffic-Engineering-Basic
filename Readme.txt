          AS 65010
           R1
            |
            |
        AS 65020
           R2
         /     \
        /       \
     AS 65030   AS 65040
        R3        R4

🛠️ BGP Traffic Engineering Lab

Task 1: Route Filtering (AS-Path/Prefix Control)
Objective: Restrict the propagation of specific routes originating from a peer Autonomous System.
Requirement: Implement a BGP filter so the Loopback address advertised by AS 65040 is no longer present in R1’s BGP table.
Constraint: Ensure all other BGP prefixes remain reachable and unaffected.
Verification: Confirm the specific prefix is missing from show ip bgp while other routes remain valid.


Task 2: Local Preference Manipulation
Objective: Influence outbound traffic selection by prioritizing one provider/peer over another.
Requirement: For the 100.100.100.100/32 prefix, modify the BGP policy so the path via AS 65030 is preferred over the path via AS 65040.
Constraint: * The Local Preference value must be higher than the default (100).
This policy must apply exclusively to the 100.100.100.100/32 prefix.
Verification: * Run show ip bgp 100.100.100.100 to confirm the Local Preference value.
Verify which path is marked as the "best" (indicated by the > symbol).

Task 3: AS-Path Prepending
Objective: Influence inbound traffic by making a specific path appear less desirable to external neighbors.
Requirement: R2 learns the prefix 200.200.200.200/32 from both R3 and R4. Modify the BGP advertisement so the path via AS 65040 is less attractive.
Strategy: Artificially increase the AS-Path length using prepending.
Verification: * On the receiving router (R2), verify that the AS-Path for the AS 65040 route has been extended.
Confirm that BGP path selection has shifted to the alternate route as a result of the longer path.