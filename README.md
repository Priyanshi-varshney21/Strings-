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
