#### Solution

```java
boolean oneAway(String s1, String s2) {
    if (s1.length() == s2.length()) {
        return oneEditReplace(s1, s2);
    } else if (s1.length() == s2.length() + 1) {
        return oneEditInsert(s1, s2);
    } else if (s1.length() + 1 == s2.length()) {
        return oneEditInsert(s2, s1);
    }
    return false;
}

private boolean oneEditReplace(String s1, String s2) {
    int mismatches = 0;
    for (int i = 0; i < s1.length(); i++) {
        if (s1.charAt(i) != s2.charAt(i)) {
            mismatches++;
        }
        if (mismatches > 1) {
            return false;
        }
    }
    return true;
}

// Function assumes s1.length() == s2.length() + 1,
// meaning s1 is longer than s2 by 1 character
private Boolean oneEditInsert(String s1, String s2) {
    if (s1.length() != s2.length() + 1) {
        return null;
    }
    int i = 0;
    int j = 0;
    int inserts = 0;
    while (i < s1.length() && j < s2.length()) {
        if (s1.charAt(i) == s2.charAt(j)) {
            i++;
            j++;
        } else {
            i++;
            inserts++;
        }
        if (inserts > 1) {
            return false;
        }
    }
    return true;
}
```

#### Time/Space Complexity

- Time Complexity: O(n+m)
- Space Complexity: O(1)
