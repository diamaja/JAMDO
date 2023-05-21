# JAMDO
Jamaican Block Chain and Smart Contracts 
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract JamaicanCoin {
    string public name;
    string public symbol;
    uint256 public totalSupply;
    mapping(address => uint256) public balances;

    event Transfer(address indexed from, address indexed to, uint256 value);

    constructor() {
        name = "Jamaican Coin";
        symbol = "JMC";
        totalSupply = 100000000000; // Initial supply of 1,000,000 ,000,000JMC
        balances[msg.sender] = totalSupply;
    }

    function transfer(address to, uint256 value) public returns (bool) {
        require(value > 0, "Invalid transfer amount");
        require(balances[msg.sender] >= value, "Insufficient balance");

        balances[msg.sender] -= value;
        balances[to] += value;
        emit Transfer(msg.sender, to, value);
        return true;
    }

    function balanceOf(address account) public view returns (uint256) {
        return balances[account];
    }
}
