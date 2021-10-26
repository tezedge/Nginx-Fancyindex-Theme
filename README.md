# Nginx-Fancyindex-Theme
A responsive theme for [Nginx](https://www.nginx.org/) Fancyindex module. Minimal, modern and simple.
Comes with a search form, aims to handle thousands of files without any problems.

This theme is modified for Viablesystems/Tezedge style.

The fancyindex module can be found [here](https://github.com/aperezdc/ngx-fancyindex) (by @aperezdc).

[Original README.md](README.original.md)

## Using Nginx-Fancyindex-Theme with Tezedge dark theme.

Make sure Nginx uses fancyindex module.

Clone this repository to the system running Nginx, e.g. in `/opt`. Add the
location of this repository to the `server` section of Nginx configuration:

```
  location /Nginx-Fancyindex-Theme {
    root /opt/Nginx-Fancyindex-Theme;
  }
```

For locations serving directory index that should be themed, enable fancyindex with data from this repo, e.g.

```
  location / {
    root /var/lib/served-files;
    # fancyindex specific settings
    fancyindex on;
    fancyindex_localtime on;
    fancyindex_exact_size off;
    fancyindex_header "/Nginx-Fancyindex-Theme-dark/header.html";
    fancyindex_footer "/Nginx-Fancyindex-Theme-dark/footer.html";
    fancyindex_ignore "examplefile.html"; # Ignored files will not show up in the directory listing, but will still be public. 
    fancyindex_ignore "Nginx-Fancyindex-Theme-dark"; # Making sure folder where files are don't show up in the listing. 
    fancyindex_ignore "hfuzz.*\.toml";
    fancyindex_ignore "^\..*";
    # Warning: if you use an old version of ngx-fancyindex, comment the last line if you
    # encounter a bug. See https://github.com/Naereen/Nginx-Fancyindex-Theme/issues/10
    fancyindex_name_length 255; # Maximum file name length in bytes, change as you like.
    fancyindex_default_sort date_desc;
  }

```
