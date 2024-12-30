# React useEffect Async/Await Race Condition

This repository demonstrates a potential race condition in a React component using the `useEffect` hook with `async/await`.  The component fetches data from a mock API endpoint.  The bug lies in how the component handles the loading and error states, potentially leading to a brief flicker of the loading state even after data has been fetched successfully. 

## Bug Description
The issue is caused by the order of setting states in the `finally` block.  There might be a brief period where `loading` is `false` and then immediately set back to `true` by another unrelated useEffect.