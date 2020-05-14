# LibreOffice-BreezeDark Fork

Fork that fixes some of the installation issues 


## Installation


```
sudo cp -R LibreOffice-BreezeDark/images_breeze_dark.zip /usr/lib/libreoffice/share/config
cp -R LibreOffice-BreezeDark/standard.soc ~/.config/libreoffice/4/user/config/standard.soc

#backup
cp ~/.config/libreoffice/4/user/registrymodifications.xcu ~/.config/libreoffice/4/user/registrymodifications.xcu.bak

# copy my registry
cp -R LibreOffice-BreezeDark/myregistrymodifications.xcu ~/.config/libreoffice/4/user/registrymodifications.xcu
```


## Alternative 

Instead of copying my registry, inject only the dark color scheme. 

```
cat LibreOffice-BreezeDark/dark-color-scheme.xcu | xcp
vim ~/.config/libreoffice/4/user/registrymodifications.xcu 
# paste **before** </oor:items> tag

```

## Checks 

- double check permissions 
- use xmllint to detect issues in XML


## Known issue

Normal for dark-color-scheme.xcu to not pass xmllint

```
dark-color-scheme.xcu:1: namespace error : Namespace prefix oor for path on item is not defined
<item oor:path="/org.openoffice.Office.UI/ColorScheme"><prop oor:name="CurrentCo
                                                      ^
dark-color-scheme.xcu:1: namespace error : Namespace prefix oor for name on prop is not defined
noffice.Office.UI/ColorScheme"><prop oor:name="CurrentColorScheme" oor:op="fuse"
                                                                               ^
dark-color-scheme.xcu:1: namespace error : Namespace prefix oor for op on prop is not defined
noffice.Office.UI/ColorScheme"><prop oor:name="CurrentColorScheme" oor:op="fuse"
                                                                               ^
dark-color-scheme.xcu:3: parser error : Extra content at the end of the document
<item oor:path="/org.openoffice.Office.Common/Misc"><prop oor:name="SymbolStyle"
```
