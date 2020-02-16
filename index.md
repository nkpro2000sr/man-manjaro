## To update mirror list for faster pacman ;)
<script src="https://gist.github.com/nkpro2000sr/aa89e0ed55b4b0401705a47684fec1e4.js"></script>
```txt
## /etc/pacman.d/mirrorlist
## Manjaro Linux custom mirrorlist
## Generated on 2020-02-16 11:02
##
## Please use 'pacman-mirrors -id' to reset custom mirrorlist
## Please use 'pacman-mirrors -c all' to reset custom mirrorlist
## To remove custom config run  'pacman-mirrors -c all'
##

## Country : India
Server = http://mirrors.piconets.webwerks.in/manjaro-mirror/stable/$repo/$arch

   0.231 
.: INFO Writing mirror list
   India           : http://mirrors.piconets.webwerks.in/manjaro-mirror/stable/$
.: INFO Mirror list generated and saved to: /etc/pacman.d/mirrorlist
```

## To backup and restore whole system 
use timeshift (recommended)
`sudo pacman -Syu timeshift`
