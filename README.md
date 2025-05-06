{\rtf1\ansi\ansicpg1252\cocoartf2822
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\froman\fcharset0 Times-Roman;}
{\colortbl;\red255\green255\blue255;\red0\green0\blue0;}
{\*\expandedcolortbl;;\cssrgb\c0\c0\c0;}
\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\deftab720
\pard\pardeftab720\partightenfactor0

\f0\fs24 \cf0 \expnd0\expndtw0\kerning0
\outl0\strokewidth0 \strokec2 =========================================================\
\uc0\u55357 \u56587  iPhone Battery Level Display for Home Assistant\
=========================================================\
\
This project creates a visual display of iPhone battery levels in Home Assistant using battery icons and dynamic styling.\
\
It includes:\
- A template sensor to map raw battery percentage to discrete levels (0, 15, 35, 75, 100)\
- A Lovelace card layout using `custom:button-card` and `custom:layout-card`\
- Local battery icons in `/config/www/battery/`\
- Support for multiple iPhones\
\
---------------------------------------------------------\
\uc0\u55357 \u56513  File Structure\
---------------------------------------------------------\
\
home-assistant-iphone-battery-display/\
\uc0\u9474 \
\uc0\u9500 \u9472 \u9472  README.txt\
\uc0\u9500 \u9472 \u9472  template.yaml\
\uc0\u9500 \u9472 \u9472  ui-lovelace.yaml\
\uc0\u9500 \u9472 \u9472  www/\
\uc0\u9474    \u9492 \u9472 \u9472  battery/\
\uc0\u9474        \u9500 \u9472 \u9472  battery_0.png\
\uc0\u9474        \u9500 \u9472 \u9472  battery_15.png\
\uc0\u9474        \u9500 \u9472 \u9472  battery_35.png\
\uc0\u9474        \u9500 \u9472 \u9472  battery_75.png\
\uc0\u9474        \u9500 \u9472 \u9472  battery_100.png\
\uc0\u9474        \u9492 \u9472 \u9472  (optional) battery_charging.png, battery_warning.png\
\
---------------------------------------------------------\
\uc0\u55357 \u56615  Installation\
---------------------------------------------------------\
\
1. Upload Battery Icons\
-----------------------\
Put these files in:\
  /config/www/battery/\
\
Required PNGs:\
  - battery_0.png\
  - battery_15.png\
  - battery_35.png\
  - battery_75.png\
  - battery_100.png\
\
Optional:\
  - battery_charging.png\
  - battery_warning.png\
\
2. Add Template Sensor\
----------------------\
In configuration.yaml or template.yaml:\
\
template:\
  - sensor:\
      - name: "iPhone Battery Level Mapped"\
        unique_id: iphone_battery_level_mapped\
        state: >\
          \{% set level = states('sensor.iphone_p_lemieux_battery_level') | int(0) %\}\
          \{% if level >= 95 %\}\
            100\
          \{% elif level >= 75 %\}\
            75\
          \{% elif level >= 35 %\}\
            35\
          \{% elif level >= 15 %\}\
            15\
          \{% else %\}\
            0\
          \{% endif %\}\
\
3. Add to Lovelace\
------------------\
Paste the following into your dashboard YAML or a manual card:\
\
(See `ui-lovelace.yaml` for full version)\
\
type: custom:layout-card\
layout_type: vertical\
cards:\
  - type: horizontal-stack\
    cards:\
      - type: custom:button-card\
        entity: sensor.iphone_p_lemieux_battery_level\
        name: \uc0\u55357 \u56587  iPhone\
        show_state: true\
        show_icon: false\
        show_name: true\
        custom_fields:\
          battery_img: |\
            [[[\
              const lvl = parseInt(entity.state);\
              let img = '/local/battery/battery_0.png';\
              if (lvl > 15) img = '/local/battery/battery_15.png';\
              if (lvl > 35) img = '/local/battery/battery_35.png';\
              if (lvl > 75) img = '/local/battery/battery_75.png';\
              if (lvl > 90) img = '/local/battery/battery_100.png';\
              return `<img src="$\{img\}" style="height: 200px;" />`;\
            ]]]\
\
...\
\
(Repeat second card if needed for other iPhones)\
\
---------------------------------------------------------\
\uc0\u55357 \u56550  Requirements\
---------------------------------------------------------\
- custom:button-card \uc0\u8594  https://github.com/custom-cards/button-card\
- custom:layout-card \uc0\u8594  https://github.com/thomasloven/lovelace-layout-card\
(Install with HACS or manually)\
\
---------------------------------------------------------\
\uc0\u55357 \u56567  Preview\
---------------------------------------------------------\
(Screenshot of dashboard goes here)\
\
---------------------------------------------------------\
\uc0\u55358 \u56800  Notes\
---------------------------------------------------------\
- The logic can be extended to show charging or warning images.\
- You can apply the same method to Android or tablet sensors too.\
\
}