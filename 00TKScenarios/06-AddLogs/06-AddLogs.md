# Think first, then act

## Use Copilot Plan mode, then execute

### Full Q/A logging

![alt text](image.png)

In **Plan** mode, ask:

```text
Add a backend mechanism that logs both user questions and answers to the configured Application Insights, and always prints them to the console.
```

Pay attention to the back-and-forth and Copilot objections.

![alt text](image-1.png)

![alt text](image-2.png)

Save the plan as a reusable prompt template.

![alt text](image-3.png)

![alt text](image-4.png)

![alt text](image-5.png)

![alt text](image-6.png)

Then switch to implementation (claude 4.5 or newer).

### Verify

- Run locally and confirm logs show up.
- Commit + push so GitHub Actions builds/deploys.
