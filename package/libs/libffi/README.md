# libffi package backport

This recipe is copied from `openwrt/openwrt` commit
`9b835ec6264f3364a22a9c67909f16bf5e5328d1` (`libffi: add package`). That
commit moved the existing recipe from the packages feed into the OpenWrt core
tree. The UFI003 workflow locks an older `lkiuyu/immortalwrt` source revision,
while its live ImmortalWrt packages feed now builds GLib 2.88.1 with a runtime
and host-build dependency on `libffi`.

The workflow overlays this package only if the locked source tree does not
already provide `package/libs/libffi/Makefile`. GLib's declared dependency then
selects both the target library and its host build dependency.
