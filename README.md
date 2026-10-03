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
