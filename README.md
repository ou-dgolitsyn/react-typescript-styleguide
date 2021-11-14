# Style guide & best practices for using typescript & React
<br/>

## `Table of Contents`

#### [`Section 1: Code style`](#code-style)

Eslint & common patterns

#### [`Section 2: Best practices`](#best-practices)

React + TS

#### [`Section 3: Anti-patterns`](#antipatterns)

The Bad and the Ugly

#### [`Section 4: Useful IDE plugins`](#plugins)

Make your develop easier

#### [`Section 5: Articles`](#articles)

What to read about TS & React

<br/>


## Section 1: Code style <a id="code-style"></a>

### 1.1 Eslint

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

## Section 2: Best practices <a id="best-practices"></a>

### 2.1 ---

Testing code is not like production-code - design it to be dead-simple, short, abstraction-free, flat, delightful to work with, lean. One should look at a test and get the intent instantly.

## Section 3: Anti-patterns <a id="antipatterns"></a>

### 3.1 ---

Testing code is not like production-code - design it to be dead-simple, short, abstraction-free, flat, delightful to work with, lean. One should look at a test and get the intent instantly.

## Section 4: Useful IDE plugins <a id="plugins"></a>

### 4.1 ---

Testing code is not like production-code - design it to be dead-simple, short, abstraction-free, flat, delightful to work with, lean. One should look at a test and get the intent instantly.

![alt text](/assets/test.gif)

## Section 5: Articles <a id="articles"></a>

### 5.1 ---

Testing code is not like production-code - design it to be dead-simple, short, abstraction-free, flat, delightful to work with, lean. One should look at a test and get the intent instantly.

[Test external link 1](http://a.com)
