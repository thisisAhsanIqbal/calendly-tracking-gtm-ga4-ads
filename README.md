# Calendly Booking Tracking with GTM → GA4 → Google Ads

This guide shows how to:

- Track Calendly bookings using Google Tag Manager
- Send custom events to GA4
- Mark those events as conversions in Google Ads
- Attribute conversions by traffic source (Google Ads, Facebook, Organic, etc.)

## 🔧 Tools Used

- Google Tag Manager (GTM)
- Google Analytics 4 (GA4)
- Google Ads
- Calendly (with embed or popup widget)

## 📜 Step-by-Step Instructions

### 1. Add Calendly Listener Script

```html
<script>
  window.dataLayer = window.dataLayer || [];
  window.addEventListener("message", function (e) {
    if (e.data.event && e.data.event.indexOf("calendly") === 0) {
      window.dataLayer.push({
        event: "calendly",
        calendly_event: e.data.event.split(".")[1],
      });
    }
  });
</script>
```
  <img src="https://github.com/thisisAhsanIqbal/calendly-tracking-gtm-ga4-ads/blob/main/Step%201.png?raw=true" alt="Step 1" width="800">
  
### 2. Create GTM Trigger

- Trigger type: Custom Event
- Event name: calendly
- Trigger on: All Pages or specific pages

  <img src="https://github.com/thisisAhsanIqbal/calendly-tracking-gtm-ga4-ads/blob/main/Step%202.png?raw=true" alt="Step 2" width="800">

### 3. Create GTM Tag (GA4 Event)
- Tag type: GA4 Event
- Event name: calendly_booking
- Parameters: (optional)
- Linked to the GA4 Config Tag
- Fire on: Custom Event Trigger from above

  <img src="https://github.com/thisisAhsanIqbal/calendly-tracking-gtm-ga4-ads/blob/main/Step%203.png?raw=true" alt="Step 3" width="800">

### 4. Mark as Conversion in GA4

- Go to GA4 > Admin > Events
- Mark calendly_booking as a conversion

### 5. Import into Google Ads

- GA4 > Tools > Conversions > Import from GA4

#### 🧪 Debug Tips

- Use GTM Preview Mode
- Use GA4 Realtime DebugView
- Use Chrome Console to log dataLayer pushes



<h2 align="center">📄 Download Full PDF Guide</h2>
<p align="center">
  <a href="https://github.com/thisisAhsanIqbal/calendly-tracking-gtm-ga4-ads/blob/main/All%20Step.pdf">
    <img src="https://img.shields.io/badge/Download%20PDF-Full%20Steps-blue?style=for-the-badge&logo=adobeacrobatreader" alt="Download PDF">
  </a>
</p>
