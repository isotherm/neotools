## Running Neo Manager in VirtualBox
Install VirtualBox
Create a virtual machine. I used a free Windows XP Mode virtual disk from the Microsoft website. Its archive has a VHD disk.

Install VirtualBox Extension Pack for better USB support. Its version must exactly match the version of VirtualBox.
Install guest additions into the VM.

In the virtual machine settings:
* Enable USB 2.0 EHCI
* Set two USB filters, for the keyboard and comms parts of the device:
  vendorId=081e productId=bd01
  vendorId=081e productId=bd04

Install Neo Manager. If it fails with digital certificate error, update the OS or install the certificate manually.
Plug in AlphaSmart and wait a few minutes till the operating system recognizes it and offers to install a driver.

## Development

### USB captured data
There is no open-source implementation of installing applets. So this is the focus of the USB set under usb_pcap.
The file install_calculator302.pcapng has the most annotations.

Captured with WireShark on Linux host, with NEO Manager 3.9.3 running on Windows XP virtual machine.

* [connection](usb_pcap/connection.pcapng) - Opening manager, idle for several minutes, closing manager.
* [get_info](usb_pcap/get_info.pcapng) - "Get NEO Info" from the manager menu.
* [install_applets_remove_unlisted](usb_pcap/install_applets_remove_unlisted.pcapng) - installing AlphaWord Plus 3.4 and Control Panel 1.07 with the checkmark for "Delete SmartApplets that are not in the Install List from all NEO devices"
* [install_calculator302](usb_pcap/install_calculator302.pcapng) - install a single applet Calculator 3.02
* [install_thesaurus](usb_pcap/install_thesaurus.pcapng) - Thesaurus Large USA 1.1. The manager backed up the applets, removed them and reinstalled again with thesaurus. It happened only for this applet. The delete checkmark was off.
* [install_spellcheck_large_usa_103](usb_pcap/install_spellcheck_large_usa_103.pcapng) - SpellCheck Large USA 1.03
* [send_file3_to_device](usb_pcap/send_file3_to_device.pcapng) - File starts with the line "this is file 3 text", ends with "456"
* [send_file4_to_device](usb_pcap/send_file4_to_device.pcapng) - File starts with the line "this is file 4 text", ends with "456"
* [view_file](usb_pcap/view_file.pcapng) - download a text file
* [install_multiple_fonts](usb_pcap/install_multiple_fonts.pcapng) - The default fonts micro, medium, large, very large, extra large.
* [install_neofont_atto11](usb_pcap/install_neofont_atto11.pcapng)
* [install_neofont_bold6](usb_pcap/install_neofont_bold6.pcapng)
* [install_neofont_femto9](usb_pcap/install_neofont_femto9.pcapng)
* [install_neofont_small6](usb_pcap/install_neofont_small6.pcapng)
* [install_neofont_tech6](usb_pcap/install_neofont_tech6.pcapng)
