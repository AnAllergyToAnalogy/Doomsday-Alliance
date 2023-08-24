# Doomsday: Settlers of the Wasteland 
## Alliance contract

This is the Alliance contact, which will be used in Doomsday: Settlers of the Wasteland Season 3 for the new Alliance feature.

The purpose of this repo is so that players may analyse the code and formulate strategies in anticipation of this feature.

The Alliances will be deployed by a deployer contract, and have their own interface on the Doomsday website.


### Features/Design

Anyone can create an alliance, creating an alliance deploys a new alliance contract. The creator is compensated for the cost of the tx with shares in the new alliance.

Alliances can have one of three types of privacy, which is set when the alliance is created:

 - PRIVATE: only alliance members can add settlements or funds to the alliance
 - FUNDING: anyone can fund (and get shares in) the alliance, but only members can add settlements
 - SETTLEMENTS: anyone can fund or add settlements to the alliance (and receive shares for it)

When an alliance is created, the creator also sets the name and token symbol of the alliance, and how settlements should be valued when they're added to the alliance. They can either set a fixed value, or leave it at "current mint cost".

#### Shares

When adding funds or settlements to an Alliance, the alliance calculates the value, and assigns them to the person adding the funds/settlements.

Every Alliance contract is an ERC-20 contract, shares in the Alliance are ERC-20 tokens.

The Alliance doesn't account for reinforcement when adding Settlements, because this adds too many layers of complexity.

#### Membership 

Alliances have 2 types of members: Leaders and Members.

Leaders can add members to the alliance, or promote other members to be leaders.

Members can execute reinforce transactions and disaster confirms on behalf of the alliance. It doesn't require multiple signatures, so you need to trust the members of an alliance not to waste funds reinforcing the wrong tokens. But it also means shit gets done in a timely way.

#### Cashing out

Settlements can't be abandoned or taken out of the alliance by alliance members. only the final winning token can be abandoned.
All members can also set an acquisition price, which is how much they would be willing to sell the alliance for. Anyone can buy out the alliance at any time by paying the acquisition highest acquisiton price set by any member. They immediately gain the ability to withdraw  all the tokens from the alliance.

When the round is over, or the alliance is acquired, the alliance is over. players can cash out of the alliance, and they receive a share of the alliance's ETH relative to what % of shares they own. this is true whether the alliance won, and got all the spoils, or if it was acquired, all the acqusition eth, or if they are just cashing out the unused reinforcement ETH 



### Security and Social Vulnerability considerations

**NOTE: This is not a trustless Alliance**

Alliance members have the freedom to execute Reinforce functions at any time, assuming the Alliance has sufficient funds for it.

Alliance leaders also have the ability to add new members, or promote leaders.

This means players are taking a risk in trusting that there are no malicious operators on their team, or just stupid team members,
who may use Alliance funds to reinforce Settlements in a non-ideal way.

Relevant warnings will be placed on the Alliance website interface, however the onus is upon players to navigate these risks.

The Alliance is designed to operate effectively at the speed that Doomsday: Settlers of the Wasteland plays out. 
For example, always being able to Reinforce a Settlement in the 75 Block disaster window, or obscuring the resources of an Alliance, while properly compensating users who contribute.

For a completely trustless solution, we recommend using a regular Multisig contract."# Doomsday-Alliance" 
