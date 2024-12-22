# Stale Closure in React useEffect Hook
This example demonstrates a common error in React's `useEffect` hook: a stale closure due to a missing dependency in the dependency array.

## Bug
The `MyComponent` function uses `useEffect` to update a counter every second. However, the dependency array is empty (`[]`), which means the effect runs only once after the component mounts.  The `count` variable inside the `setInterval` callback refers to the initial value of `count` (0), causing the counter to always display 0, even though the `setInterval` is updating the state. 

## Solution
The solution is to include `count` in the dependency array. Now the effect will rerun whenever `count` changes, ensuring the latest `count` value is used inside the callback.