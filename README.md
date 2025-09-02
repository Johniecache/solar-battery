# Solar 21700 USB Battery Charger
A compact hardware project that charges multiple 21700 Li-ion 50E Samsung cells using solar energy, storing it safely, and outputs regulated 5V via USBA. 

## Use Case
Use to power any USB-a device via a 21700 5000mAh battery that is charged itself by solar power.

## Features
- Charges 21700 cell from solar panel (~6V input)
- USB 5V output via boost converter (MT3608)
- Battery management with TP4056 (with protection)
- Rocker switch to save power when not in use
- Designed for portable, off-grid applications

## Components
| Component | Description | Link |
|-----------|-------------|------|
| TP4056 | Li-ion charging + protection | [Amazon](https://www.amazon.com/HiLetgo-Lithium-Charging-Protection-Functions/dp/B07PKND8KG/ref=sr_1_3?crid=2RNCS27X3G67O&dib=eyJ2IjoiMSJ9.mmqI1134FS87MHz1mUcWtVQ3nl56sscrnSMxLFpWabzs2P0VEpvBhthLuQU6SI2Miw-I83Qy9o5TsMndADuD7kOOSb3OrmbtbkryfY6n36x4uXgLHjDBbQdK3YvKYhaD_6Ld93CpeP-UHwzHBChaIwkmEzZ6JKOD7jCRDQ6-ocDRUUeq0i-wfOQYnde4objwYD_PROqkFCInSDxSNV8qIUcOZHZn3yFOwOWFto0EUsk.8vyBwRi72GVM1dxXRx4JKOLEvJc0XP319kvKBtV_rYo&dib_tag=se&keywords=tp4056&qid=1746113787&sprefix=TP40%2Caps%2C341&sr=8-3) |
| MT3608 | Boost converter (3.7V → 5V) | [Amazon](https://www.amazon.com/Dorhea-MT3608-DC-DC-Boost-Converter/dp/B089JYBF25/ref=sr_1_3?crid=1URDLFIGHF7P6&dib=eyJ2IjoiMSJ9.V20UGII4iKhMPSdbA0ORU8ntDcx_O-vpOIRGcpWJV8KYxJ7Fs-oJWyISZ1iSuNb3ElBPVExAVAFQFpZh5Ed6HEAoc5BOM3fxMdJGXJotV6QVZAnsJkccjFaDuhu2CtmD814tj8uIL17duBEOBTgrYZ3MfOMJGW9eC3Kt6-rKT-v74PE6zYvuFmAbYG8XouuDGLXcoEBg26C0AazPxRWOynIeExWw3o4wksGlxug4YDI.0apLGxT--sNxn0hRxi54YFQ_082fLE6HxtZaWxaJNRI&dib_tag=se&keywords=mt3608&qid=1746113828&sprefix=mt3608%2Caps%2C840&sr=8-3) |
| 21700 Battery | Rechargeable Lithium-ion cell | [18650 Battery Store](https://www.18650batterystore.com/products/samsung-50e) |
| Solar Panel | 5.5–6V, 1–2W (min) 5-6w (recommended) | [Amazon](https://www.amazon.com/POWOXI-Maintainer-Intelligent-Controller-Waterproof/dp/B089SVMPHL/ref=sr_1_4?crid=2OZBMUNRHPZA5&dib=eyJ2IjoiMSJ9.rTQirNrW6diGTWMsa86kMUhT7YxLt5144Q9BgTImu0Iz8i1PMQz15hHDgbOXm2Kz9bvChrItzdzXZyRf6AmWo_WOjTII1f5SL6Wp-zw_EgmoEo9hKD426Dbo9xQJlpv0Fzfmd9aw5zyDdnwiOPgkhwHNk2FWSEV8BAw8zXxPtRhp_eXwKmbq6vdWQA2SFXPVN53VXgeS_Oi39-qZTmzjIDY8dyVl-zmzhRbOjZZvkgw.d036ePt3E2ZSaa8IYuVzZKJGpSqT2OKz9lxlyxGiq-k&dib_tag=se&keywords=6w+6v+solar+panel&qid=1746113885&sprefix=6w+6v+solar+panel%2Caps%2C155&sr=8-4) |
| Rocker Switch | Toggleable power output to USBA | [Amazon](https://www.amazon.com/DaierTek-250VAC-Rocker-KCD1-101-Plastic/dp/B07S2QJKTX/ref=sr_1_1_sspa?dib=eyJ2IjoiMSJ9.U6DeqVsNukOmjPf4ZQ1XOXhIcmbstjqzeNS6KO5OiEMwtiSMGtTuNdj9lgAF2eLF12lRtlpVsSJUYRYInjnA5VFP8FE9aDc-i2TQL62o6xBl2I07gcjJubDox_JPmFb_5stm7qSf8PkyeHtLK4MhUrAAGkiquyUc_TYwD4N41ohNEeygO-R6Vh8yhecDRTsQhJy9LfZdBp32LoaykBXpWJFE_DgsxJaon8iclzM-SG0.HrDgsFcjStz9RvCM1nNPtWhK-30_BPh5een2qPg3tNM&dib_tag=se&keywords=rocker+switch&qid=1756828076&sr=8-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1) |
| 22 AWG wire | connection between terminals | [Amazon]([amazon.com/dp/B089CQHRDT?ref_=ppx_hzsearch_conn_dt_b_fed_asin_title_12](https://www.amazon.com/Fermerry-Stranded-Electric-Tinned-Copper/dp/B089CQHRDT/ref=sr_1_4_sspa?dib=eyJ2IjoiMSJ9.LbfmNeaOMKQc2NnauqoG3qGV41E7ROxSi6Xxb0l3ZgfUb5OE2VE2IVYsqTuHy37T1oy0OB7HhgbbAFZn13h4Uw2PPNDdWFW-k2vugdq8nKhybWmN9ODvoRyJ6MHV3KbGWSaYPBtptDogn_N8hEGi6gTbMT13eeC60C4o8-8xEqaCe4afXLqfB_pqxp9VVg9qmJbSRyD_6FkrFiEOTDYgBWPOTj1ukOPC8d-vgVjZgkBVI9_NSbOrtohi_5576x0wK9OkiA9CBVABGx2s7nx_zLwA62wJWaf6r43zm4p-Eqo.AQBYnQ_6EABFiEKMg3BW8fLpb8A8GAVy8ogbX3r2h1g&dib_tag=se&keywords=22+awg+wire&qid=1756828098&sr=8-4-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1)) | 
## Wiring Diagram (hand drawn)
<img width="2480" height="1748" alt="image" src="https://github.com/user-attachments/assets/bef03d62-bfe0-493c-8ef7-17529ae8996e" />

## Power Flow
1. Solar panel feeds TP4056 charger
2. TP4056 charges and protects 18650 cell
3. MT3608 boosts cell output to 5V USB

## Safety Notes
- Use a TP4056 with protection circuit (not the bare one!)
- Do not exceed panel voltage/current ratings
- Keep battery within 3.0V–4.2V range

## Future Plans
- Auto shutoff if battery drops too low
- Enclosure design (weatherproof)
- LED (green, orange, red) to show battery level

## License
MIT

## Author
Caleb Thomas — 2025

