#  Top 10 Real Playwright Interview Questions & Answers
## QA & SDET Interview Preparation (2026)

These are some of the most frequently asked **real-world Playwright interview questions** for QA Automation Engineers and SDETs. The focus is on scenario-based questions rather than basic definitions.

---

# 1. Your Playwright tests are flaky. How would you identify and fix the root cause?

## Answer

Flaky tests usually fail intermittently without any code changes. My approach is to identify whether the issue is caused by synchronization, unstable locators, test data, network latency, or environment differences.

### Steps I follow

- Check Playwright Trace Viewer
- Analyze screenshots and videos
- Verify element locators
- Remove hard waits
- Use Playwright's built-in auto waiting
- Ensure tests are independent
- Mock unstable APIs if needed
- Retry only after identifying the root cause

### Interview Tip

Never say **"I will increase wait time."**

Explain **why** the test is failing.

---

# 2. A Playwright test passes locally but fails in Jenkins or GitHub Actions. How do you debug it?

## Answer

I compare both environments and investigate the differences.

### My debugging approach

- Review CI logs
- Open Trace Viewer
- Compare browser versions
- Verify environment variables
- Check network latency
- Capture screenshots and videos
- Confirm test data availability
- Run the failing test in headed mode

### Best Practice

Always collect evidence before changing the test.

---

# 3. How would you design a Playwright automation framework from scratch?

## Answer

A scalable framework should separate business logic from test logic.

```
Project

│

├── tests

├── pages

├── components

├── fixtures

├── utils

├── test-data

├── api

├── config

├── reports

└── playwright.config.ts
```

### Key Features

- Page Object Model
- Reusable utilities
- Environment configuration
- API helpers
- Reporting
- Logging
- CI/CD integration

### Interview Tip

Explain scalability rather than folder names.

---

# 4. How do you handle dynamic elements whose locators change every build?

## Answer

I avoid XPath whenever possible.

Preferred locator order

1. getByRole()
2. getByLabel()
3. getByPlaceholder()
4. getByTestId()
5. CSS Selector

### Example

```typescript
await page.getByRole('button', {
    name: 'Login'
}).click();
```

If developers can provide **data-testid**, that is usually the most stable option.

---

# 5. Explain Browser, BrowserContext and Page with a real-world example.

## Answer

**Browser**

The browser application itself.

**BrowserContext**

An isolated browser session.

**Page**

A single browser tab.

### Real-world Example

Suppose we are testing a banking application.

- Customer logs in
- Admin logs in
- Manager logs in

Instead of opening three browsers, we create three BrowserContexts.

Each context has its own cookies, cache, and session.

This allows multiple users to interact independently.

---

# 6. How do you reduce execution time for thousands of Playwright tests?

## Answer

For large automation suites, optimization is essential.

### Techniques

- Parallel execution
- Multiple workers
- Sharding
- Reuse authentication using storageState
- API login instead of UI login
- Headless execution
- Independent test execution
- Execute smoke tests before regression

### Interview Tip

Mention both execution speed and resource optimization.

---

# 7. How do you automate OTP, CAPTCHA or Multi-Factor Authentication?

## Answer

CAPTCHA should never be automated because it exists to prevent automation.

Instead, I work with developers to create test-friendly solutions.

### Possible approaches

- Disable CAPTCHA in lower environments
- Mock authentication
- Use API-generated OTP
- Read OTP from database or email service (if permitted)
- Use test accounts

### Interview Tip

This question evaluates practical thinking, not coding ability.

---

# 8. Explain Network Interception in Playwright.

## Answer

Network interception allows us to monitor, modify, or mock API requests.

### Example

```typescript
await page.route("**/users", async route => {

    await route.fulfill({

        status: 200,

        json: {

            id: 1,

            name: "John"

        }

    });

});
```

### Advantages

- Faster execution
- Backend-independent testing
- Edge case validation
- Error simulation

---

# 9. When would you choose Selenium instead of Playwright?

## Answer

Although Playwright is my preferred framework, Selenium is still useful in some situations.

### Selenium is suitable when

- Internet Explorer support is required
- Existing Selenium Grid is already established
- Legacy enterprise applications
- Existing Selenium framework has significant investment

### Playwright is preferred because

- Auto waiting
- Faster execution
- Better debugging
- Built-in API testing
- Cross-browser support

---

# 10. What are the biggest mistakes you have seen in Playwright automation frameworks?

## Answer

Some common issues include:

❌ Hard waits

❌ XPath for every locator

❌ Duplicate code

❌ Shared test data

❌ No Page Object Model

❌ Poor folder structure

❌ No screenshots

❌ No reporting

❌ No retries

❌ Environment-specific values hardcoded

### Best Practices

- Follow Page Object Model
- Use stable locators
- Generate reports
- Capture screenshots on failure
- Store test data separately
- Keep tests independent
- Use configuration files for environments

---

# ⭐ Bonus Interview Question

## What is one Playwright feature you use the most in real projects?

### Sample Answer

One of the features I use most is **BrowserContext** because it allows me to create isolated user sessions for multi-user workflows.

I also frequently use:

- Auto Waiting
- Trace Viewer
- Storage State
- API Testing
- Network Mocking
- Fixtures
- Parallel Execution

These features make Playwright faster, more reliable, and easier to maintain than many traditional automation frameworks.

---

# Final Interview Tips

- Think in terms of solving business problems, not just writing code.
- Explain the reasoning behind your solution instead of only naming Playwright features.
- Support your answers with examples from real projects whenever possible.
- Emphasize maintainability, reliability, and scalability in framework discussions.
- Be prepared to explain trade-offs (e.g., when Selenium may still be the better choice).
