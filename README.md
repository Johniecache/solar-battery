# Solar 21700 USB Battery Charger
A compact hardware project that charges a single 21700 Li-ion cell using solar energy, stores it safely, and outputs regulated 5V via USB. Includes real-time voltage, current, and battery percentage display for monitoring.

## Use Case
Use to power any USB-a device via a 21700 5000mAh battery that is charged itself by solar power.

## Features
- Charges 21700 cell from solar panel (~6V input)
- USB 5V output via boost converter (MT3608)
- Battery management with TP4056 (with protection)
- Live monitoring: voltage, current, charge %
- Designed for portable, off-grid applications

## Components
| Component | Description | Link |
|-----------|-------------|------|
| TP4056 | Li-ion charging + protection | [Amazon](https://www.amazon.com/HiLetgo-Lithium-Charging-Protection-Functions/dp/B07PKND8KG/ref=sr_1_3?crid=2RNCS27X3G67O&dib=eyJ2IjoiMSJ9.mmqI1134FS87MHz1mUcWtVQ3nl56sscrnSMxLFpWabzs2P0VEpvBhthLuQU6SI2Miw-I83Qy9o5TsMndADuD7kOOSb3OrmbtbkryfY6n36x4uXgLHjDBbQdK3YvKYhaD_6Ld93CpeP-UHwzHBChaIwkmEzZ6JKOD7jCRDQ6-ocDRUUeq0i-wfOQYnde4objwYD_PROqkFCInSDxSNV8qIUcOZHZn3yFOwOWFto0EUsk.8vyBwRi72GVM1dxXRx4JKOLEvJc0XP319kvKBtV_rYo&dib_tag=se&keywords=tp4056&qid=1746113787&sprefix=TP40%2Caps%2C341&sr=8-3) |
| MT3608 | Boost converter (3.7V → 5V) | [Amazon](https://www.amazon.com/Dorhea-MT3608-DC-DC-Boost-Converter/dp/B089JYBF25/ref=sr_1_3?crid=1URDLFIGHF7P6&dib=eyJ2IjoiMSJ9.V20UGII4iKhMPSdbA0ORU8ntDcx_O-vpOIRGcpWJV8KYxJ7Fs-oJWyISZ1iSuNb3ElBPVExAVAFQFpZh5Ed6HEAoc5BOM3fxMdJGXJotV6QVZAnsJkccjFaDuhu2CtmD814tj8uIL17duBEOBTgrYZ3MfOMJGW9eC3Kt6-rKT-v74PE6zYvuFmAbYG8XouuDGLXcoEBg26C0AazPxRWOynIeExWw3o4wksGlxug4YDI.0apLGxT--sNxn0hRxi54YFQ_082fLE6HxtZaWxaJNRI&dib_tag=se&keywords=mt3608&qid=1746113828&sprefix=mt3608%2Caps%2C840&sr=8-3) |
| 21700 Battery | Rechargeable Lithium-ion cell | [18650 Battery Store](https://www.18650batterystore.com/products/samsung-50e) |
| Solar Panel | 5.5–6V, 1–2W (min) 5-6w (recommended) | [Amazon](https://www.amazon.com/POWOXI-Maintainer-Intelligent-Controller-Waterproof/dp/B089SVMPHL/ref=sr_1_4?crid=2OZBMUNRHPZA5&dib=eyJ2IjoiMSJ9.rTQirNrW6diGTWMsa86kMUhT7YxLt5144Q9BgTImu0Iz8i1PMQz15hHDgbOXm2Kz9bvChrItzdzXZyRf6AmWo_WOjTII1f5SL6Wp-zw_EgmoEo9hKD426Dbo9xQJlpv0Fzfmd9aw5zyDdnwiOPgkhwHNk2FWSEV8BAw8zXxPtRhp_eXwKmbq6vdWQA2SFXPVN53VXgeS_Oi39-qZTmzjIDY8dyVl-zmzhRbOjZZvkgw.d036ePt3E2ZSaa8IYuVzZKJGpSqT2OKz9lxlyxGiq-k&dib_tag=se&keywords=6w+6v+solar+panel&qid=1746113885&sprefix=6w+6v+solar+panel%2Caps%2C155&sr=8-4) |
| INA219 | Current/voltage sensor (I2C) | [Amazon](https://www.amazon.com/Interface-Bi-Directional-Current-Monitoring-Breakout/dp/B0CP6WHSS7/ref=sr_1_3?crid=2DOH3DPSOSLC0&dib=eyJ2IjoiMSJ9.jRGNsF10hIV0b5XiN0szdm1wVTkm_4rhStZfkAWr6y4VCDljqBddg1qMXc4bJrlq8Y07e98vc1eeQwkJhgbs1IbdiiGgiIY3iGnPhGTRKiI0I_0fdVMJvjMaIw6OSpPV298dXBNh17DMcWzyIijaPKF3qf4WdGQbj8d1zi5YB2aE_b5S8zQNkbpK2RgF6I-sGkNOl7xHWAuTuIFXoDSh9c6zgTsLaC6D0xzurMvYMp0.x4d8hh8CSFuMNsngDsyHf3ZjgSmLJVKAQ_XlbgOmWq8&dib_tag=se&keywords=INA219&qid=1746113916&sprefix=ina219%2Caps%2C136&sr=8-3) |
| MSP420 | OLED display | [Amazon](https://www.amazon.com/DIYmall-Serial-128x64-Display-Arduino/dp/B00O2KDQBE/ref=sr_1_4?crid=NX5RN4BJSZ7C&dib=eyJ2IjoiMSJ9.z_zp54ql1z5bqQoe4uoh3BpRL4besxbvDWWJyZ5L_vX0hWX__eVE5a7apejz5xFVpl8q8GTTaAUAXQ-3VBwwxkCvLMJjkccQSzSyNNYdWBEPn1ausPe3LZ7maFxtNmmJFVDELS5rpqFsVdZ37mimMYZqrmJWe_PAWjI6HnUM-3-6_a9UWQAIJLBIepd-EDL7FggZOXOw8sT-WvgBT1qoxsvuLvAvp8RDp_6LA4hcf5pEwhwMthOX16Gb9bbW1ln_tgaauvaPiJp0zOvILHRzh08cLbyM8Fv4U8Oop5EldPA.qX2GPfRVsNJFZ5P7l2I2bDXyd24Q06WU6yaWYi8Atec&dib_tag=se&keywords=msp420&qid=1746113938&sprefix=msp42%2Caps%2C228&sr=8-4&th=1) |
| Microcontroller | ATmega32U4 Pro Micro | [Amazon](https://www.amazon.com/Atmega32U4-Programming-Development-Micro-Controller-Compatible/dp/B0D83FBYPD/ref=sr_1_3?crid=2A1615KXQR3PP&dib=eyJ2IjoiMSJ9.3P-KUgX1Vdaf0PPqaQWYDDFFpmIne7paSLLC7cj06wZzQRiK_Zgsr5t47HOHDOjw0-xEI7uzMXsyN0rkQQiejN3CBnK2NkM_6-ZJcMYPQLJsdgpjUvp6fe8Qwkq3xK6BbhFbkxv1lXOLC-rqzhmUJ57H9Ez1HM1ySqBdfXcWuqfUnvdoGof__ojXH12lJSm8mnLzb2OjlLsRAbFw4qFsOpuwmE-Xf1yQgN5FKtahfxk.uv5uALh_FZmeVCsZ87ZWovZdr6M52td4tGThJKVEAmo&dib_tag=se&keywords=atmega32u4&qid=1746113957&sprefix=atmega32u4%2Caps%2C231&sr=8-3) |
| 100k&Omega; resistors | for feedback loop | [Amazon](https://www.amazon.com/Projects-10EP514100K-100k-Resistors-Pack/dp/B00CVZ4LQ6?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=AODFMOUHD0RRM&gQT=1&th=1) |
| 10k&Omega; resistors | for feedback loop | [Amazon](https://www.amazon.com/Projects-10EP51410K0-10k-Resistors-Pack/dp/B00CVZ4DKU/ref=pd_bxgy_d_sccl_2/144-3813552-6749341?pd_rd_w=6zRBo&content-id=amzn1.sym.de9a1315-b9df-4c24-863c-7afcb2e4cc0a&pf_rd_p=de9a1315-b9df-4c24-863c-7afcb2e4cc0a&pf_rd_r=5J8RD0JDNZQVS3BS9EYS&pd_rd_wg=Kzrb9&pd_rd_r=3cf6fd17-3ac7-49bb-bdce-0cf6924240b5&pd_rd_i=B00CVZ4DKU&th=1) |
| 33&mu;H Inductor | for MT3608 | [AliExpress](https://www.aliexpress.us/item/3256805480792922.html?spm=a2g0o.productlist.main.13.3aa9fhaJfhaJ9H&algo_pvid=8d42e0f0-a759-4758-b6a4-53d9d2611187&algo_exp_id=8d42e0f0-a759-4758-b6a4-53d9d2611187-6&pdp_ext_f=%7B%22order%22%3A%2255%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21USD%211.65%211.45%21%21%211.65%211.45%21%40210318c317465653916737912e628a%2112000033949793787%21sea%21US%210%21ABX&curPageLogUid=RDIzS7d7RpUL&utparam-url=scene%3Asearch%7Cquery_from%3A) |
| 10&mu;F Capacitor | for MT3608 | [AliExpress](https://www.aliexpress.us/item/3256806057749356.html?spm=a2g0o.productlist.main.29.43e647b7e33BVw&algo_pvid=b3f26418-6e12-4507-beb4-3f51980b0c36&algo_exp_id=b3f26418-6e12-4507-beb4-3f51980b0c36-14&pdp_ext_f=%7B%22order%22%3A%224180%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21USD%214.95%213.02%21%21%2135.60%2121.70%21%402103146c17465654244524942e35d2%2112000036442215262%21sea%21US%210%21ABX&curPageLogUid=ENpalIeT6Jec&utparam-url=scene%3Asearch%7Cquery_from%3A) |
| 100&mu;F Capacitor | for MT3608 | [AliExpress](https://www.aliexpress.us/item/3256806057749356.html?spm=a2g0o.productlist.main.29.43e647b7e33BVw&algo_pvid=b3f26418-6e12-4507-beb4-3f51980b0c36&algo_exp_id=b3f26418-6e12-4507-beb4-3f51980b0c36-14&pdp_ext_f=%7B%22order%22%3A%224180%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21USD%214.95%213.02%21%21%2135.60%2121.70%21%402103146c17465654244524942e35d2%2112000036442215262%21sea%21US%210%21ABX&curPageLogUid=ENpalIeT6Jec&utparam-url=scene%3Asearch%7Cquery_from%3A) |
| SOT23-6 MT3608 | for MT3608 | [AliExpress](https://www.aliexpress.us/item/3256808667259021.html?spm=a2g0o.productlist.main.9.39e0no5mno5mtY&algo_pvid=47de4a8f-1c6c-4639-a94a-1b02b3a6954c&algo_exp_id=47de4a8f-1c6c-4639-a94a-1b02b3a6954c-4&pdp_ext_f=%7B%22order%22%3A%222%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21USD%213.15%212.95%21%21%213.15%212.95%21%402103244617465656211398444e98f5%2112000046953361201%21sea%21US%210%21ABX&curPageLogUid=Q2fGZLaD7PE0&utparam-url=scene%3Asearch%7Cquery_from%3A) |

## Wiring Diagram (hand drawn)

## Power Flow
1. Solar panel feeds TP4056 charger
2. TP4056 charges and protects 18650 cell
3. MT3608 boosts cell output to 5V USB
4. INA219 + microcontroller read voltage/current
5. Display shows real-time data

## Firmware
Firmware is in `/code`. Uses:
- Adafruit INA219 library
- Adafruit SSD1306 library
- Arduino core for ATmega32U4

Upload via Arduino IDE or PlatformIO.

## Safety Notes
- Use a TP4056 with protection circuit (not the bare one!)
- Do not exceed panel voltage/current ratings
- Keep battery within 3.0V–4.2V range

## Future Plans
- Auto shutoff if battery drops too low
- Enclosure design (weatherproof)

## License
MIT

## Author
Caleb Thomas — 2025

