# Midwest Radio Android App

## Overview

This project is an Android application designed to stream radio content using a service-based architecture and ExoPlayer for audio playback. Below is a breakdown of the project's structure and dependencies.

## Dependencies

- **Gradle File**: `MidwestRadio/app/build.gradle`

## Project Structure

### /Audio
- Contains `AudioService.java` and `AudioPlayer.java`.
- Facilitates audio playback using ExoPlayer.
- Implements a service-based architecture.
- Manages `AudioPlayer` instance and a WiFi lock for seamless playback.

### /fragments
- Contains subclasses of `android.support.v4.app.DialogFragment` or `android.support.v4.app.Fragment`.
- Each file corresponds to an XML layout in `app/src/main/res/layout` or `layout-land`.
- Fragments depend on utility classes, models, audio components, and the network.
- Managed via `MainActivity` and `android.support.v4.app.FragmentManager`.

### /models
- **Station Object**: Core model representing a radio station.
  - Parcelable for Android Bundles.
  - Includes getter and setter methods required for Jackson JSON mapping.
- **StationList Factory**: Maps backend JSON data to an `ArrayList` of `Station` objects using `com.fasterxml.jackson.databind.ObjectMapper`.
- **Important**: Ensure the Station object matches backend attributes to avoid issues.

### /network
- Manages HTTP requests via a standard HTTP client.
- Utilized by `LoadingFragment` and `RadioFragment`.
- Expects HTTP response code `200` for successful callbacks.
- `Requests.java` includes an example of the expected station data JSON format.

### /utils
- Contains utility components and callbacks essential for fragment XML functionality.

## Notes

- Update the `Station` model whenever backend attributes change.
- Ensure all fragments are correctly initialized and managed in `MainActivity`.

---

For further information or questions, refer to the source code comments or documentation.

