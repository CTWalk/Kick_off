## Wait For System Stability

Playwright provides several wait mechanisms that are more focused on overall page state, navigation, and network activities. We can use it for waiting for the application to reach a stable state after performing actions like navigation, form submissions, or any other operations that might lead to a change in the page content or state.

### Waiting for Navigation

Wait for navigation to complete after clicking a link or button. It's useful for scenarios where clicking a link or button leads to a new page.
````javascript
await Promise.all([
  page.waitForNavigation(), // Waits for the next navigation to finish
  page.click('a[href="https://www.example.com"]') // Triggers the navigation
]);
````

### waitForLoadState

The`'networkidle'` state is particularly useful for waiting until there are no more than 2 network connections for at least 500ms, indicating that most of the resources have been loaded.
````javascript
await page.goto('https://example.com');
await page.waitForLoadState('networkidle');
````


### waitForResponse and waitForRequest

These method are useful for testing applications with significant backend interactions.
````javascript
// Wait for a specific request
await page.waitForRequest(request => request.url().includes('/api/data') && request.method() === 'GET');

// Wait for a specific response
await page.waitForResponse(response => response.url().includes('/api/data') && response.status() === 200);
````
use `includes()` to check for a specific part of the URL that identifies the request or response we're interested in. 
