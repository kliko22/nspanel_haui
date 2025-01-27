# Nextion Component

[README](../README.md) | [Documentation](README.md) | [Installation](Install.md) | [Configuration](Config.md) | [Panels](panels/README.md) | [FAQ](FAQ.md)

- [Nextion Component](#nextion-component)
  - [Installation](#installation)
  - [How to edit the HMI file](#how-to-edit-the-hmi-file)
  - [Scripts for display](#scripts-for-display)

## Installation

To install the TFT file on the display, the device needs to be already flashed with ESPHome.

The device will provide a button `Update Display` in the device settings. There are also services
available.

- Using a button:

  - Button: `Update Display`
    This will load the TFT file from the URL configured on the ESP.

- Using a service:
  - Service: `nspanel_haui_upload_tft`
    This will load the TFT from the configured URL

  - Service: `nspanel_haui_upload_tft_url`
    This will load the TFT from the URL provided to the service.

## How to edit the HMI file

To edit the HMI file, no special care is needed. Following are some helpful infos. The HMI is used mostly to design the interface but does not need any special code. Only on a page based lifetime of events should be done on the display. If possible, the logic should be placed in the AppDaemon App.

All pages need to send a `sendme` in `Preinitialize`. This is needed to know of a page change event.

Prepare the page in the `Preinitialize` event because the AppDaemon App cannot control the display at this stage. Only after a page is shown, it is possible to change anything or interact with it.

If you want to process any click events, you need to enable `Send Component ID` on the event to be used.

If you want to interact with any component on the display, the component id and objectname is required. They are being used and are defined in the AppDaemon App.

When changing order of components on a page, be aware, that the id of the components will change.

## Scripts for display

see `scripts` in the root directory for different scripts.

- Font generation
- Image generation
