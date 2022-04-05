---
# An instance of the Contact widget.
widget: contact

# This file represents a page section.
headless: true
active: true

# Order that this section appears on the page.
weight: 130

title: Contact
subtitle:

content:
  # Automatically link email and phone or display as text?
  autolink: true
  email_form: 0
  
  # Email form provider
  form:
    provider: netlify
    formspree:
      id:
    netlify:
      # Enable CAPTCHA challenge to reduce spam?
      captcha: false

  # Contact details (edit or remove options as required)
  email: jackywang28@outlook.com
  phone: 
  address:
    street: Luoyu Road 1037
    city: Wuhan
    region: 
    postcode: '430000'
    country: China
    country_code: CHN
  #coordinates:
   # latitude: '37.4275'
    #longitude: '-122.1697'
  #directions: Enter Building 1 and take the stairs to Office 200 on Floor 2
  #office_hours:
   # - 'Monday 10:00 to 13:00'
   # - 'Wednesday 09:00 to 10:00'
  #appointment_url: 'https://calendly.com'
  contact_links:

design:
  columns: '2'
---
