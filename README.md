# Strings-
#PALINDROME STRINGS 
def palindrome(s):
  left=0
  right=len(s)-1
  is_palindrome=True
  while left<=right:
    if s[left]!=s[right]:
      is_palindrome=False
      break
    left+=1
    right-=1
  return is_palindrome

# REMOVE OYTERMOST PARENTHESE
def removeOuterParentheses(s):
    ans = ""
        count = 0
        for ch in s:
            if ch == '(':
                if count > 0:
                    ans += ch
                count += 1
            else:
                count -= 1
                if count > 0:
                    ans += ch

        return ans

# ROMAN TO INTEGER
 def romanToInt(self, s: str) -> int:
        # Your code goes here
        values={
            "I":1,
            "II":2,
            "III":3,
            "IV":4,
            "V":5,
            "X":10,
            "L":50,
            "C":100,
            "D":500,
            "M":1000,
        }
        ans=0
        for i in range(len(s)):
            if i+1<len(s) and values[s[i]] < values[s[i+1]]:
                ans-=values[s[i]]
            else:
                ans+=values[s[i]]
        return ans

# STRING TO INTEGER
def myAtoi(self, s):
        i=0
        n=len(s)
        #White space
        while i<n and s[i]==' ':
            i+=1
        #check sign
        sign=1
        if i<n and s[i]=='-':
            sign=-1
            i+=1
        elif i<n and s[i]=='+':
            i+=1
        ans=0
        while i<n and s[i].isdigit():
            ans=ans*10+int(s[i])
            i+=1
        return sign*ans

# LONGEST PALINDROMIC SUBSTRING
def longestPalindrome(self, s: str) -> str:
        def solve(s,i,j):
            if i>=j:
                return True
            if(s[i]==s[j]):
                return solve(s,i+1,j-1)
            return False   
        n=len(s)
        sp=0
        maxLen=0
        for i in range(n):
            for j in range(i,n):
                if (solve(s,i,j)==True):
                    if(j-i+1)>maxLen:
                        maxLen=j-i+1
                        sp=i
        return s[sp:sp+maxLen]

# SUM OF BEAUTY OF ALL SUBSTRINGS 
def beautySum(self, s: str) -> int:
        n=len(s)
        ans=0
        for i in range(n):
            freq=[0]*26
            maxi=0
            for j in range(i,n):
                idx=ord(s[j])-ord('a')
                freq[idx]+=1
                maxi=max(maxi,freq[idx])
                mini=float('inf')
                for k in range(26):
                    if freq[k]>0:
                        mini=min(mini,freq[k])
                ans+=maxi-mini
        return ans

# COUNT MAXDEPTH
def maxDepth(self, s: str) -> int:
        count=0
        maxi=0
        for ch in s:
            if ch=='(':
                count+=1
                maxi=max(maxi,count)
            elif ch==')':
                count-=1
        return maxi

# WONDERFUL WORDS
def countSubstrings(self, s: str) -> int:
        mask=0
        ans=0
        freq={0:1}
        for ch in s:
            bit=ord(ch)-ord('a')
            mask^=(1<<bit)
            ans+=freq.get(mask,0)
            for i in range(10):
                new_mask=mask ^ (1<<i)
                ans+=freq.get(new_mask,0)
            freq[mask]=freq.get(mask,0)+1
        return ans
