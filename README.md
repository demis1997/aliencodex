# aliencodex
 
The contract uses the following code specifically 

  function retract() contacted public {
    codex.length--;
  }

with no protection against underflows since you can reduce the length even if the length is at 0. You start off by making contact with the contract to turn the boolean to true and allow you to use the other functions. Then, you retract which will make the array take up the entire storage size 2**256-1 slots. The owner slot now is at location 0 and the array is at location 1. The evm storage is located at keccak256(bytes32(1)) and the location we need is index = 2 ** 256 - uint();
After calculating the result we can use it within the revise function

  function revise(uint i, bytes32 _content) contacted public {
    codex[i] = _content;
  }
  
which in turn will make us the owner! Once again, by underflowing an array from 0 you can make it take up the entire storage size 2**256-1 slots and you can then manipulate everything stored within.
