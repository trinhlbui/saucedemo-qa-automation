# Sauce Demo QA Automation

UI and API test automation built with **Playwright + TypeScript**, using the
Page Object Model and run automatically in **GitHub Actions**.

- UI target: https://www.saucedemo.com (public practice e-commerce site)
- API target: https://jsonplaceholder.typicode.com (public fake REST API)

## What's covered

| Area | Tests |
|------|-------|
| Login | valid login, wrong password, locked-out user, empty username, empty password |
| Cart & checkout | add to cart updates badge, full end-to-end order, required-field validation, price sort order |
| API | GET single resource, GET with query params, POST create, 404 handling |

## Project structure

```
pages/      Page objects (LoginPage, ShopPage, CheckoutPage)
tests/      Test specs (login, checkout, api)
.github/    CI workflow
```

## Run it

```bash
npm install
npx playwright install chromium
npm test              # everything
npm run test:ui       # UI tests only
npm run test:api      # API tests only
npm run test:headed   # watch the browser
npm run report        # open the HTML report
```

## Design notes

- Page objects keep selectors in one place, so a UI change means one fix, not many.
- Locators prefer `data-test` attributes and accessible roles/placeholders over brittle CSS paths.
- Tests are independent and can run in parallel.
- Traces and screenshots are captured on failure to speed up debugging.

## Ideas for next steps

- Add more users (e.g. `problem_user`, `performance_glitch_user`) and document any bugs found.
- Add a mobile viewport project.
- Add a Postman collection for the same API endpoints.
