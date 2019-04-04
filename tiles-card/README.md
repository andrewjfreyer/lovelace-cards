## Description 

Tiles Card for [Lovelace](https://www.home-assistant.io/lovelace/) forked from [Rodrigo Fraga](https://github.com/rodrigofragadf/lovelace-cards/). Huge thanks to Rodrigo for all the work on this project. 

_____

## Installation
1. Download the [tiles-card.js](https://github.com/andrewjfreyer/lovelace-cards/raw/master/tiles-card/tiles-card.js).
2. Save the file in the `config / www` directory or in a subdirectory within it.
3. Add the path file to `resources:` in the `ui-lovelace.yaml` file:

```yaml
resources:
  - url: /local/tiles-card.js?v={{VERSION}}
    type: js
```
5. Choose a number for `{{VERSION}}` in the yaml above and incremenber *every time* a change is made to the underlying javascript. 

## Setup
Below is the default configuration structure, more detailed documentation will be released in the future.

***NOTE: for simplicity and robustness, this fork has removed support for lists and grayscale, which @rodrigofragadf included in the [original](https://github.com/rodrigofragadf/lovelace-cards/raw/master/tiles-card/tiles-card.js)***

Some features available on this card:

- Support for themes
- Opacity support
- Border support
- Shadow support
- Disable unavailable entities
- And more...

_____

## Example Lovelace Config:

```yaml
views:
  - title: Title View
    cards:
      - type: custom:tiles-card

        card_settings: 
          title: Card Title #(optional)
          title_color: white #(optional)#color
          title_align: center #(optional)(left, center, right)
          columns: 4 #(optional)(number)
          column_width: calc(90%/4) #(optional)(px, %, auto)
          row_height: 35px #(optional)(px, %, auto)
          background: gray #(optional)(image or color)(for image use url()) ex. 'url(/local/icons/mobile-television.png)'
          display: show #(optional)#hidden, none, show
          gap: 10px #(optional)
          padding: 10px #(optional)
          align: center #(optional)(left, center, right)
          theme: night #(optional)
          templates: #(optional)
            background: "return 'url(/local/icons/mobile-television.png)'" #(optional)
            display: "return 'show'" #(optional)
            style: "return 'background: black;'" #(optional)
            theme: "return 'day'"

        global_settings: #(Settings here are applied to all entities)
          display: show #(optional)(hidden, none, show)
          orientation: horizontal #(optional)(horizontal or vertical)
          padding: 5px #(optional)
          align: 'center middle' #(optional)(letf, center, right, top, middle, bottom)
          disable: false #(optional)(true or false)
          shadow: 'elevation: 12dp' #(optional)(elevation: 2dp, 3dp, 4dp, 6dp, 8dp, 12dp, 16dp or 24dp or box-shadow css attributes)
          disable_if_unavailable: false #(optional)(true ou false)

          label: #(optional)
            value: Label #(optional)
            color: #(optional)
              value: white #(optional)
              value_on: yellow #(optional)
              value_off: red #(optional)
              value_disabled: black #(optional)
            size: 14px #(optional)
            transform: none #(optional)
            padding: 5px #(optional)
            state: light.lampada_1 #(optional)

          label_sec: #(optional)
            value: Sec #(optional)
            color: #(optional)
              value: black #(optional)
              value_on: orange #(optional)
              value_off: blue #(optional)
              value_disabled: black #(optional)
            size: 18px # (optional)
            transform: uppercase #(optional)
            padding: 5px #(optional)
            state: light.lampada_1 #(optional)

          icon: #(optional)
            value: mdi:lightbulb #(optional) #mdi icon or image. ex. '/local/icons/mobile-television.png'
            value_on: mdi:lightbulb-on #(optional)
            value_off: mdi:account #(optional)
            value_disabled: mdi:lock #(optional)
            color:  #(optional)
              value: white #(optional)
              value_on: yellow #(optional)
              value_off: gray #(optional)
              value_disabled: black #(optional)
            size: 18px #(optional)
            padding: 0px #(optional)

          listbox: #(optional)(Used only for entity input_select)
            column_span: 4
            display: none #(optional)(hidden, none, show)
            orientation: horizontal #(optional)(horizontal or vertical)
            padding: 0px 0px 10px 5px #(optional)
            align: 
            disable: true #(optional)(true or false)

            title: Channel List #(optional)
            title_color: white #(optional)
            title_size: 13px #(optional)
            title_transform: capitalize #(optional)
            title_height: 17px #(optional)

            input_color: blue #(optional)
            input_size: 20px #(optional)
            input_transform: uppercase #(optional)
            input_height: 18px #(optional)
            
            itens_color: yellow #(optional)
            itens_size: 15px #(optional)
            itens_transform: lowercase #(optional)
            list_background: black #(optional)

          background: #(optional)
            value: '#0f2547' #(optional) (color or image, for image use url()) ex. 'url(/local/icons/mobile-television.png)'
            value_on: green #(optional)
            value_off: red #(optional)
            value_disabled: gray #(optional)
            image_size: 25px 25px #(optional)
            
          opacity: #(optional)
            value: 1 #(optional)
            value_on: 1 #(optional)
            value_off: 0.5 #(optional)
            value_disabled: 0.1 #(optional)

          border: #(optional)
            size: 3px #(optional)(default 0px)
            radius: 5px #(optional)(% or px)
            style: dotted #(optional)
            color:  #(optional)
              value: white #(optional)
              value_on: yellow #(optional)
              value_off: blue #(optional)
              value_disabled: gray #(optional)

        entities:
            
            - entity: light.light_1 #(Entity specific settings. Overwrite the global settings)
              column: 1 #(optional)
              row: 1 #(optional)
              column_span: 2 #(optional)
              row_span: 4 #(optional)
              display: show #(optional)(hidden, none, show)
              orientation: #(optional)(horizontal or vertical)
              padding: 0px #(optional)
              align: 'center middle' #(optional)(letf, center, right, top, middle, bottom)
              disabled: true #(optional)(true or false)
              shadow: 'elevation: 12dp' #(optional)(elevation: 2dp, 3dp, 4dp, 6dp, 8dp, 12dp, 16dp or 24dp or box-shadow css attributes)
              more_info: switch.tv #(optional)
              data: #(optional)
              service: #(optional)

              label: #(optional)
                value: Label #(optional)
                color: #(optional)
                  value: white #(optional)
                  value_on: yellow #(optional)
                  value_off: red #(optional)
                  value_disabled: black #(optional)
                size: 14px #(optional)
                transform: none #(optional)
                padding: 5px #(optional)
                state: light.lampada_1 #(optional)

              label_sec: #(optional)
                value: Sec #(optional)
                color: #(optional)
                  value: black #(optional)
                  value_on: orange #(optional)
                  value_off: blue #(optional)
                  value_disabled: black #(optional)
                size: 18px # (optional)
                transform: uppercase #(optional)
                padding: 5px #(optional)
                state: light.lampada_1 #(optional)

              icon: #(optional)
                value: mdi:lightbulb #(optional) #mdi icon or image. ex. '/local/icons/mobile-television.png'
                value_on: mdi:lightbulb-on #(optional)
                value_off: mdi:account #(optional)
                value_disabled: mdi:lock #(optional)
                color:  #(optional)
                  value: white #(optional)
                  value_on: yellow #(optional)
                  value_off: gray #(optional)
                  value_disabled: black #(optional)
                size: 18px #(optional)
                padding: 0px #(optional)

              background: #(optional)
                value: '#0f2547' #(optional) (color or image, for image use url()) ex. 'url(/local/icons/mobile-television.png)'
                value_on: green #(optional)
                value_off: red #(optional)
                value_disabled: gray #(optional)
                image_size: 25px 25px #(optional)
                
              opacity: #(optional)
                value: 1 #(optional)
                value_on: 1 #(optional)
                value_off: 0.5 #(optional)
                value_disabled: 0.1 #(optional)

              border: #(optional)
                size: 3px #(optional)(default 0px)
                radius: 5px #(optional)(% or px)
                style: dotted #(optional)
                color:  #(optional)
                  value: white #(optional)
                  value_on: yellow #(optional)
                  value_off: blue #(optional)
                  value_disabled: gray #(optional)

              templates: #(optional)
                background: #(optional)
                label: #(optional)
                label_color: #(optional)
                label_transform: #(optional)
                label_sec: #(optional)
                label_sec_color: #(optional)
                label_sec_transform: #(optional)
                border_color: #(optional)
                icon: #(optional)
                icon_color: #(optional)
                style: #(optional)
                display: #(optional)
                opacity: #(optional)
                disable: #(optional)
                class_name: #(optional)

            # FOR INPUT_SELECTS
            - entity: "input_select.channel_list"
              column: 1 #(optional)
              row: 1 #(optional)
              column_span: 2 #(optional)
              row_span: 4 #(optional)
              display: show #(optional)(hidden, none, show)
              orientation: #(optional)(horizontal or vertical)
              padding: 0px #(optional)
              align: 'center middle' #(optional)(letf, center, right, top, middle, bottom)
              disabled: true #(optional)(true or false)
              shadow: 'elevation: 12dp' #(optional)(elevation: 2dp, 3dp, 4dp, 6dp, 8dp, 12dp, 16dp or 24dp or box-shadow css attributes)

              title: Channel List #(optional)
              title_color: white #(optional)
              title_size: 13px #(optional)
              title_transform: capitalize #(optional)
              title_height: 17px #(optional)

              input_color: blue #(optional)
              input_size: 20px #(optional)
              input_transform: uppercase #(optional)
              input_height: 18px #(optional)
              
              itens_color: yellow #(optional)
              itens_size: 15px #(optional)
              itens_transform: lowercase #(optional)
              list_background: black #(optional)

              icon: #(optional)
                value: mdi:lightbulb #(optional) #mdi icon or image. ex. '/local/icons/mobile-television.png'
                color:  white #(optional)
                size: 18px #(optional)
                padding: 0px #(optional)

              background: #(optional)
                value: '#0f2547' #(optional) (color or image, for image use url()) ex. 'url(/local/icons/mobile-television.png)'
                value_on: green #(optional)
                value_off: red #(optional)
                value_disabled: gray #(optional)
                image_size: 25px 25px #(optional)

              opacity: #(optional)
                value: 1 #(optional)
                value_on: 1 #(optional)
                value_off: 0.5 #(optional)
                value_disabled: 0.1 #(optional)

              border: #(optional)
                size: 3px #(optional)(default 0px)
                radius: 5px #(optional)(% or px)
                style: dotted #(optional)
                color:  #(optional)
                  value: white #(optional)
                  value_on: yellow #(optional)
                  value_off: blue #(optional)
                  value_disabled: gray #(optional)

              templates: #(optional)
                background: "return 'blue'" #(optional)
                title_color: "return 'red'" #(optional)
                input_color: "return 'red'" #(optional)
                itens_color: "return 'red'" #(optional)
                icon: "return '/local/icons/mobile-television.png'" #(optional)
                icon_color: "return 'blue'" #(optional)
                style: "return 'background: blue;'" #(optional)
                display: "return 'show'" #(optional)
                disable: "return false" #(optional)
                opacity: "return 0.5" #(optional)
                border_color: "return 'red'" #(optional)
```
