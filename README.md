pragma solidity ^0.6.0;

contract EarnTRX {
    address payable public owner;
    uint public referralCount;
    mapping(address => bool) public referrals;
    uint public referralBonus;

    constructor() public {
        owner = msg.sender;
        referralBonus = 50; // 50 TRX bonus for each referral
    }

    function refer(address _referral) public {
        require(!referrals[_referral], "Referral has already been registered.");
        referrals[_referral] = true;
        referralCount++;
        owner.transfer(referralBonus); // transfer referral bonus to owner
    }
}
