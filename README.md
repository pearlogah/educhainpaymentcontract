# educhainpaymentcontract

 // SPDX-License-Identifier: MIT
 pragma solidity ^0.8.0;

contract Educhain {
    uint256 public paymentCount;
    mapping(uint256 => bool) public paymentReceived;
    
    event PaymentVerified(uint256 indexed paymentId, address indexed payer, uint256 amount);
    
    constructor() {
        paymentCount = 0;
    }
    
    function verifyPayment() public payable {
        require(msg.value > 0, "Payment amount should be greater than 0");
        
        uint256 paymentId = paymentCount;
        paymentCount++;
        paymentReceived[paymentId] = true;
        
        // Perform any payment verification logic here
        
        emit PaymentVerified(paymentId, msg.sender, msg.value);
    }
    
    function acceptPayment() public payable {
        require(msg.value > 0, "Payment amount should be greater than 0");
        
        uint256 paymentId = paymentCount;
        paymentCount++;
        paymentReceived[paymentId] = true;
        
        // Additional logic for accepting payments
        
        emit PaymentVerified(paymentId, msg.sender, msg.value);
    }
}
