# Question

A message containing letters from A-Z can be encoded into numbers using the following mapping:

- 'A' -> "1"
- 'B' -> "2"
- ...
- 'Z' -> "26"

To decode an encoded message, all the digits must be grouped then mapped back into letters using the reverse of the mapping above (there may be multiple ways). For example, "11106" can be mapped into:

- "AAJF" with the grouping (1 1 10 6)
- "KJF" with the grouping (11 10 6)
- Note that the grouping (1 11 06) is invalid because "06" cannot be mapped into 'F' since "6" is different from "06".

Given a string s containing only digits, return the number of ways to decode it.

# Example

input = "9232203232"

- 9->
- 23->
- 2->
- 3->



# Notes (not an actual solution)

```
class Solution:
    
    def __init__(self):
        self.n_ways = 0
        self.mylist = []
        
    def decode_recursive(self, string):
        
        if(string in self.mylist):
            return
        
        if(len(string) ==0):
            self.n_ways = self.n_ways + 1
            return 
        
        print(string)
        # if(len(string) == 2):
        #     if( (string[0] == 0) ):
        #         return

        # if string has a leading 0 and string length > 2, then just string out the leading zero
        if( (eval(string[0]) == 0)):
            print('my print: ' + string)
            return
        
        

        if(eval(string[0]) > 0):
            self.mylist.append(string)
            self.decode_recursive(string[1:])

        # by this time I reach here there won't be a leading zero in the string
        
        if(len(string) >=2):
            if(eval(string[0] + string[1]) <=26):
                self.mylist.append(string)
                self.decode_recursive(string[2:])
        
            
    

if __name__ == "__main__":
    sol = Solution()
    sol.decode_recursive("11106") # expect 2
    #sol.decode_recursive("106") # expect 1
    #sol.decode_recursive("10") # expect 1
    print('N Ways: {}'.format(sol.n_ways))
```
