# RESTful API Example

## Overview
This project demonstrates how to make RESTful API requests using JavaScript's Fetch API. It provides buttons to trigger HTTP methods (GET, POST, PUT, DELETE) and displays the API responses on the webpage.

## APIs Used
The application interacts with a placeholder API: [JSONPlaceholder](https://jsonplaceholder.typicode.com/posts), which is a free online REST API for testing and prototyping.

### 1. GET Request
**Endpoint:** `https://jsonplaceholder.typicode.com/posts`

**Description:** Retrieves a list of posts from the API.

**Implementation:**
```javascript
async function getData() {
  try {
    const response = await fetch(apiUrl);
    const data = await response.json();
    document.getElementById('response').textContent = JSON.stringify(data, null, 2);
  } catch (error) {
    console.error('Error with GET request:', error);
  }
}
```

### 2. POST Request
**Endpoint:** `https://jsonplaceholder.typicode.com/posts`

**Description:** Creates a new post with predefined data.

**Implementation:**
```javascript
async function postData() {
  try {
    const response = await fetch(apiUrl, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ title: 'foo', body: 'bar', userId: 1 })
    });
    const data = await response.json();
    document.getElementById('response').textContent = JSON.stringify(data, null, 2);
  } catch (error) {
    console.error('Error with POST request:', error);
  }
}
```

### 3. PUT Request
**Endpoint:** `https://jsonplaceholder.typicode.com/posts/1`

**Description:** Updates an existing post with new data.

**Implementation:**
```javascript
async function putData() {
  try {
    const response = await fetch(`${apiUrl}/1`, {
      method: 'PUT',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ id: 1, title: 'foo updated', body: 'bar updated', userId: 1 })
    });
    const data = await response.json();
    document.getElementById('response').textContent = JSON.stringify(data, null, 2);
  } catch (error) {
    console.error('Error with PUT request:', error);
  }
}
```

### 4. DELETE Request
**Endpoint:** `https://jsonplaceholder.typicode.com/posts/1`

**Description:** Deletes a post from the API.

**Implementation:**
```javascript
async function deleteData() {
  try {
    const response = await fetch(`${apiUrl}/1`, { method: 'DELETE' });
    document.getElementById('response').textContent = 'Deleted successfully';
  } catch (error) {
    console.error('Error with DELETE request:', error);
  }
}
```

## How to Use
1. Open `index.html` in a web browser.
2. Click the buttons to perform API requests.
3. The response will be displayed on the page.

## Technologies Used
- HTML
- CSS
- JavaScript (Fetch API)

## Notes
- This project uses JSONPlaceholder, which does not actually modify data but simulates API responses.
- The `DELETE` request does not return a JSON response, so a success message is displayed manually.
