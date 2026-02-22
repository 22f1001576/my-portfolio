name: Cache Dependencies

on:
  push:
    branches: [main]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Cache dependencies
        id: cache-step
        uses: actions/cache@v4
        with:
          path: ~/.npm
          key: cache-871147f

      - name: prime-cache-871147f
        run: echo "Cache hit - ${{ steps.cache-step.outputs.cache-hit }}"
```

**4. Commit changes**

The workflow will re-run automatically. Then check:
👉 https://github.com/22f1001576/my-portfolio/actions

Make sure the step named exactly `prime-cache-871147f` appears in the run logs. Then submit:
```
https://github.com/22f1001576/my-portfolio
