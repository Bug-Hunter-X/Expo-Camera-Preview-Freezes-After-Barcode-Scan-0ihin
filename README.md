# Expo Camera Preview Freeze After Barcode Scan

This repository demonstrates a bug where the Expo Camera preview freezes after a barcode is scanned. The freeze occurs intermittently, and seems to be related to the processing performed within the `onBarCodeScanned` callback function.

## Bug Description
The Expo Camera API's `onBarCodeScanned` prop triggers a callback when a barcode is scanned. If this callback performs intensive operations (e.g., network requests, complex data processing), the camera preview may freeze and become unresponsive. This behavior is not consistent and can be difficult to reproduce reliably.

## Reproduction
1. Clone this repository.
2. Run `npm install`.
3. Run `expo start`.
4. Scan a barcode.  Observe that the preview may freeze.

## Solution
The solution involves offloading the intensive processing to a separate thread or using asynchronous operations within the `onBarCodeScanned` callback to prevent blocking the main thread and thus avoiding the camera freeze. This ensures that the camera preview remains responsive.