 ## Chainable Methods : Locator Methods
 Methods that return a `Locator` object can be chained with other `Locator` methods. These include methods to refine or filter locators, such as `.locator()` , `.nth()` ,`.first()` , `.last()` ,and `.filter()`. Because these methods return a new `Locator` object, we can contiune chaining with methods that operate on or further refine locators.

```javascript
// Chainable Locator methods
page.locator('.class').first().click();
```


 ## Non-chainable Methods : Action Methods
 Methods that perform actions on elements or the page, such as `.click()`, `.fill()` , `.press()` , `.isVisible()` , `.textContent()`, and others that inherently produce a side effect or return a value other than a `Locator` , are not chainable with locator medthods. 
 These methods typically return a `Promise` that resolves to void (for actions) or specific types of values (e.g., `boolean` for `.isVisible()`, `string` for `.textContent()`). It's the end of the chain.

```javascript
// Non-chainable action methods
await page.locator('button').click();
const isVisible = await page.locator('.some-element').isVisible();
```

# Summing up

 ## Return Type
 If a method retuns a `Locator`, we can chain further `Locator` methods. If it returns anything else, chaining `Locator` methods directly after is not applicable.

## Use Promises
It‘s more of a usage in JavaScript than Playwright's API for element interaction, but useful.

```javascript
page.locator('button').click().then(() => {
  // Code to execute after the click action completes
});
```
 
