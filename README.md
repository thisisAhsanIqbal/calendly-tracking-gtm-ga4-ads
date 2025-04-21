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
