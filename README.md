# Style guide & best practices for using typescript & React
<br/>

## `Table of Contents`

#### [`Section 0: Test code blocks`](#section-0)

A single advice that inspires all the others (1 special bullet)

<br/>


# Section 0️⃣: Test code blocks <a id="section-0"></a>

<br/>

## ⚪️ Block 0

Testing code is not like production-code - design it to be dead-simple, short, abstraction-free, flat, delightful to work with, lean. One should look at a test and get the intent instantly.

✅ **Do:**

```javascript
test("When asking for an admin, ensure only ordered admins in results", () => {
  //assuming we've added here two admins "admin1", "admin2" and "user1"
  const allAdmins = getUsers({ adminOnly: true });

  let admin1Found,
    adming2Found = false;

  if (!admin1Found || !admin2Found) {
    throw new Error("Not all admins were returned");
  }
});
```

❌ **Not:**

```javascript
test("When asking for an admin, ensure only ordered admins in results", () => {
  //assuming we've added here two admins "admin1", "admin2" and "user1"
  const allAdmins = getUsers({ adminOnly: true });

  let admin1Found,
    adming2Found = false;

  if (!admin1Found || !admin2Found) {
    throw new Error("Not all admins were returned");
  }
});
```
> Comment: A test report should tell whether the current application revision satisfies the requirements for the people who are not necessarily familiar with the code: the tester, the DevOps engineer who is deploying and the future you two years from now.

[Test external link 1](http://a.com)

