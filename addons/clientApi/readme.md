
# IsMySpaceClient Documentation

The `IsMySpaceClient` class provides an interface for interacting with the IsMySpace API. It constructs API URLs based on the current window location and offers methods for making GET and POST requests to retrieve and send messages.

## Initialization

You do not need to instantiate the `IsMySpaceClient` class directly. Instead, use the pre-created and exported `isMySpaceClient` object


## Methods

### 1. `apiGet(readPassword)`

Makes a GET request to the standard API endpoint to retrieve processed messages. If the message is in markdown, this method returns HTML ready to be rendered.

- **Parameters:**
  - `readPassword` (`string`): The read authorization password for the API.

- **Returns:**
  - `Promise<{ path: string, messages: string[] }>`: A promise that resolves to an object containing the path and an array of processed messages.

- **Example Return Value:**
    ```js
    {
      path: "string",
      messages: ["<p>processed message 1</p>", "<p>processed message 2</p>"]
    }
    ```

- **Usage Example:**
    ```js
    isMySpaceClient.apiGet('your-read-password')
        .then(response => {
            console.log(response.path); // Outputs the API path
            console.log(response.messages); // Outputs the array of processed messages
        })
        .catch(error => {
            console.error('Error:', error);
        });
    ```

### 2. `apiGetRaw(readPassword)`

Makes a GET request to the raw API endpoint to retrieve raw messages as typed.

- **Parameters:**
  - `readPassword` (`string`): The read authorization password for the API.

- **Returns:**
  - `Promise<{ path: string, messages: string[] }>`: A promise that resolves to an object containing the path and an array of raw messages.

- **Example Return Value:**
    ```js
    {
      path: "string",
      messages: ["# raw message 1", "## raw message 2"]
    }
    ```

- **Usage Example:**
    ```js
    isMySpaceClient.apiGetRaw('your-read-password')
        .then(response => {
            console.log(response.path); // Outputs the API path
            console.log(response.messages); // Outputs the array of raw messages
        })
        .catch(error => {
            console.error('Error:', error);
        });
    ```

### 3. `apiPost(readPassword, writePassword, messages)`

Makes a POST request to the standard API endpoint to send messages. This method takes in raw messages and returns both raw and handled (processed) messages.

- **Parameters:**
  - `readPassword` (`string`): The read authorization password for the API.
  - `writePassword` (`string`): The write authorization password for the API.
  - `messages` (`Array<string>`): An array of messages to be sent in the POST request body.

- **Returns:**
  - `Promise<{ path: string, rawMessages: string[], handledMessages: string[] }>`: A promise that resolves to an object containing the path, raw messages, and handled (processed) messages.

- **Example Return Value:**
    ```js
    {
      path: "string",
      rawMessages: ["string1", "string2"],
      handledMessages: ["<p>processed string1</p>", "<p>processed string2</p>"]
    }
    ```

- **Usage Example:**
    ```js
    const messages = ["Hello, world!", "# Welcome to IsMySpace"];
    isMySpaceClient.apiPost('your-read-password', 'your-write-password', messages)
        .then(response => {
            console.log(response.path); // Outputs the API path
            console.log(response.rawMessages); // Outputs the array of raw messages
            console.log(response.handledMessages); // Outputs the array of processed messages
        })
        .catch(error => {
            console.error('Error:', error);
        });
    ```

## Summary

- Use `isMySpaceClient.apiGet()` to fetch processed messages.
- Use `isMySpaceClient.apiGetRaw()` to fetch raw, unprocessed messages.
- Use `isMySpaceClient.apiPost()` to send messages and receive both raw and processed responses.

By using the `isMySpaceClient` object, you can easily interact with the IsMySpace API to read and send messages, handling both raw and processed formats.

--- 

This documentation provides a detailed overview of how to use the `isMySpaceClient` object and its methods, ensuring that users have clear instructions and examples for interacting with the IsMySpace API.