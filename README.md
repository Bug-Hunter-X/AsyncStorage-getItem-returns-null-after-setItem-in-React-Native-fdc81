# React Native AsyncStorage getItem Returns Null After setItem

This repository demonstrates a bug in React Native's AsyncStorage where `getItem` returns `null` immediately after `setItem`, particularly when multiple `setItem` calls occur in quick succession.  This appears to be related to the asynchronous nature of AsyncStorage and potential race conditions.

## Bug Description

The problem is intermittent.  After calling `setItem`, a subsequent `getItem` call returns `null` instead of the expected value. This only occurs when multiple `setItem` operations are performed rapidly, suggesting a race condition or an asynchronous operation that's not properly handled.

## How to Reproduce

1. Clone the repository.
2. Run `npm install`.
3. Run the app on an emulator or device.
4. Observe the inconsistent retrieval of data from AsyncStorage.

## Solution

The solution involves using the Promise-based nature of AsyncStorage and ensuring that `getItem` is called only after `setItem` has fully completed.  This is achieved using `.then()` to chain the asynchronous operations. The solution file shows how to fix this issue.