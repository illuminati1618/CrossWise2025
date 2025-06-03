---
layout: tailwind
search_exclude: true
hide: true
show_reading_time: false
permalink: /apidocumentation
---

### Major Accomplishments:

#### 1. **Intelligent Wait Time Prediction API**

* **File**: `border.py`
* **Accomplishment**: Designed a smart prediction API that uses both **real-time scraping** and **ML-based long-term forecasting** to return expected border wait times.
* **Purpose**: Provides highly relevant, accurate crossing time estimates for users planning trips.
* **Highlights**:

  * Dual-mode support (`long_term` and `today`).
  * Dynamic handling of missing inputs (`month`, `day`, `hour`) using `datetime`.
  * Custom weighted average algorithm that compares CBP real-time data to historical averages.

---

#### 2. **Historical Visualization API with Plotly**

* **File**: `historicalgraph_api.py`
* **Accomplishment**: Built a visual API endpoint that returns an interactive Plotly chart displaying **average hourly wait times across weekdays**.
* **Purpose**: Helps users and analysts find patterns in border congestion throughout the week.
* **Highlights**:

  * Clean mapping of JSON to pandas DataFrame.
  * Interactive Plotly visual with hover templates, line graphs, and annotations.
  * Used color and hover cues to focus on congestion trends.
  * Returned as HTML via Flask `Response`.

---

#### 3. **Live Social Media Monitoring**

* **Files**: `twitter.py`, `twitter_search.py`
* **Accomplishment**: Implemented a Twitter-based keyword listener that extracts tweets about border delays.
* **Purpose**: Augments our data model with **real user reports** on unusual delays, accidents, or alerts.
* **Highlights**:

  * Query construction using geotagged search for border region.
  * Secure integration with Twitter Bearer Token auth.
  * Pluggable via `run_border_queries()` in main runtime.

---

#### 4. **Facial Recognition Encoding Utility**

* **File**: `facial_encoding.py`
* **Accomplishment**: Built a utility using `face_recognition` to generate secure encodings from user-submitted images.
* **Purpose**: Enables future authentication or personalization features.
* **Highlights**:

  * Extracts face landmarks and encodings.
  * Stores encodings in a consistent format.
  * Modular utility format for expansion.

---

#### 5. **Weather Normalization Helper**

* **File**: `weather_formater.py`
* **Accomplishment**: Converts raw weather data into structured summaries with icons and text.
* **Purpose**: Supports optional context-aware guidance (e.g. “Expect longer delays during fog”).
* **Highlights**:

  * Maps codes to descriptive weather conditions.
  * Clean separation of formatting logic for API consumption.

---

#### 6. **Timelapse Video Generator (Traffic Review)**

* **File**: `timelapse.py`
* **Accomplishment**: Generated stitched video summaries using saved traffic cam footage throughout a day.
* **Purpose**: Allows users to **review congestion visually** before choosing crossing times.
* **Highlights**:

  * Efficient use of `moviepy` for MP4 composition.
  * Organized into timestamped folders for clarity.

---

#### 7. **Structured Border Feedback Collector**

* **File**: `border_feedback.py`
* **Accomplishment**: Created a feedback API to gather user reports on real-life wait experiences.
* **Purpose**: Trains and improves our long-term models using community-submitted data.
* **Highlights**:

  * Validates email + rating + location fields.
  * Automatically timestamps and stores user feedback.

---

#### 8. **Automated Border Video Crawler**

* **File**: `video_crawler.py`
* **Accomplishment**: Developed a background script that crawls and downloads time-stamped traffic cam footage from the San Ysidro crossing every 29 seconds.
* **Purpose**: Supports timelapse generation and historical visual analysis of real border wait conditions throughout the day.
* **Highlights**:

  * Pulls `.mp4` clips from `bordertraffic.com` based on UTC-formatted filenames.
  * Uses `pytz` to localize timestamps to Pacific Time.
  * Includes backfill logic to download the past 2 hours if no files exist on launch.
  * Handles unavailable videos or server timeouts using error messages and retries.

---

Together, these components demonstrate:

* Full-stack engineering (APIs, data models, visualization, utility scripts, etc.).
* ML + Real-time forecasting.
* Focus on usability and reliability.
