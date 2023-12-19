# ckanext-salted-template
This extension provides a custom template according to the SALTED Project color scheme.


## File tree
The current file tree is as shown below:
```sh
ckanext-salted-template
└── ckanext
    └── salted_template
        ├── public
        │   ├── images
        │   │   └── ...     <----ADD YOUR IMAGES---->
        │   └── <custom_css_filename>.css
        └── templates
            ├── ...      <----ADD YOUR CUSTOM HTML FILES---->
            └── ...      <----ADD YOUR CUSTOM HTML FILES---->
```

It shows and points out the folders in which you can add the images as well as the css and html files for the customisation of the template.

For the html files, follow the [Replacing a Default Template File](https://docs.ckan.org/en/2.10/theming/templates.html#replacing-a-default-template-file) instructions.


## Requirements
- This extension has been developed using CKAN 2.10.1 version.


## Installation
### Production environment
To install `ckanext-salted-template`:
1. Add the extension to the Dockerfile and add these lines at the end (folder path: `ckan-docker/ckan/`):
    ```bash
    RUN pip3 install -e git+https://github.com/SALTED-Project/ckanext-salted-template.git@main#egg=ckanext-salted-template && \
    pip3 install -r ${APP_DIR}/src/ckanext-salted-template/requirements.txt
    ```

2. Add parameters to `.env` file (folder path: `ckan-docker/`):
    ```bash
    CKAN__PLUGINS = "envvars <plugins> salted_template"
    CKAN__SITE_TITLE = <ckan_title>
    CKAN__HOMEPAGE_STYLE = 1 # layout
    CKAN__FAVICON = <favicon_path>
    CKAN__SITE_LOGO = <logo_path>
    CKAN__SALTED_TEMPLATE__CUSTOM_CSS_FILENAME = <custom_css_path>
    CKAN__SALTED_TEMPLATE__INTRODUCTION_TITLE = <introduction_title> # Can be written in Markdown
    CKAN__SITE_INTRO_TEXT= <introduction_text> # Can be written in Markdown
    CKAN__SITE_ABOUT = <about_text> # Can be written in Markdown
    ```
    **Notes**: 
    - `<plugins>` is a placeholder for the rest of your plugins.
    - change `<ckan_title>`, `<favicon_path>`, `<logo_path>`, `<custom_css_path>`, `<introduction_title>`, `<introduction_text>`, `<about_text>` to whatever you want.

3. Run your docker-compose file (folder path: `ckan-docker/`):
    ```bash
    docker-compose -f <docker-compose file> build --no-cache 
    docker-compose -f <docker-compose file> up
    ```
    With the `--no-cache` parameter, you are specifying to do not use cache when building the image. This parameter is optional.

### Development environment
To install `ckanext-salted-template`:
1. Clone the GitHub repository(folder path: `ckan-docker/src/`):
    ```bash
    git clone https://github.com/SALTED-Project/ckanext-salted-template.git
    ```
    **Note**: if `src/` folder does not exist, create it.

2. Add parameters to `.env` file (folder path: `ckan-docker/`):
    ```bash
    CKAN__PLUGINS = "envvars <plugins> salted_template"
    CKAN__SITE_TITLE = <ckan_title>
    CKAN__HOMEPAGE_STYLE = 1 # layout
    CKAN__FAVICON = <favicon_path>
    CKAN__SITE_LOGO = <logo_path>
    CKAN__SALTED_TEMPLATE__CUSTOM_CSS_FILENAME = <custom_css_path>
    CKAN__SALTED_TEMPLATE__INTRODUCTION_TITLE = <introduction_title> # Can be written in Markdown
    CKAN__SITE_INTRO_TEXT= <introduction_text> # Can be written in Markdown
    CKAN__SITE_ABOUT = <about_text> # Can be written in Markdown
    ```
    **Notes**: 
    - `<plugins>` is a placeholder for the rest of your plugins.
    - change `<ckan_title>`, `<favicon_path>`, `<logo_path>`, `<custom_css_path>`, `<introduction_title>`, `<introduction_text>`, `<about_text>` to whatever you want.

3. Run your docker-compose file (folder path: `ckan-docker/`):
    ```bash
    docker-compose -f <docker-compose-dev file> up --build
    ```


## Authors
The ckanext-salted-template extension has been written by:
- [Laura Martín](https://github.com/lauramartingonzalezzz)
- [Jorge Lanza](https://github.com/jlanza)
- [Víctor González](https://github.com/vgonzalez7)
- [Juan Ramón Santana](https://github.com/juanrasantana)
- [Pablo Sotres](https://github.com/psotres)
- [Luis Sánchez](https://github.com/sanchezgl)


## Acknowledgement
This work was supported by the European Commission CEF Programme by means of the project SALTED "Situation-Aware Linked heTerogeneous Enriched Data" under the Action Number 2020-EU-IA-0274.


## License
This material is licensed under the GNU Lesser General Public License v3.0 whose full text may be found at the *LICENSE* file.

It mainly makes use of the following libraries and frameworks (dependencies of dependencies have been omitted):

| Library / Framework |   License    |
|---------------------|--------------|
| Flask                 | Apache 2.0          |
| click                 | BSD-3-Clause          |
| setuptools                 | MIT          |
