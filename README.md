# RMarkdown - Agricultural Compendium

## Create new .Rmd file

To create a new .Rmd file, go to ``` New Blank File -> R Markdown ```, name your file and press okay. This will create a new blank .Rmd file in your current working directory. Next copy and paste a previous .Rmd script and work from there.

## index.Rmd landing page
The index.Rmd is commonly used as the landing page for the website. Use this page as an intorduciton to the website. For the compendium product, the index.Rmd has been edited to produce a .html file called "Agricultural Statistics". This is the first highlisted tab in the nav bar shown.
![image](https://github.com/DavidFrenchSG/compendium_data_gov_scot/assets/144359744/172bfeba-b961-4f48-beae-8234eae2db16)

## Configure .Rmd webpage
The webpage is configured in the first 31 lines of code in a new .Rmd script. Shown below:
![image](https://github.com/DavidFrenchSG/compendium_data_gov_scot/assets/144359744/6a705ca2-9bbd-4e10-bdbf-d5ca627f6e55)
### Title, Author and Date
```
title: "Agricultural Compendium"
author: "`r as.character(Sys.info()[7])`"
date: "`r Sys.Date()`"
```
### Footer
This is the standard footer for gov.scot websites. Ideally these should be links to the respective location on the gov.scot website, rather than editing new .Rmd scripts.
```
  footer:
    link:
      - href: "privacy.html"
        text: "Privacy"
      - href: "cookies.html"
        text: "Cookies"
      - href: "accessibility.html"
        text: "Accessibility"
      - href: "contact.html"
        text: "Contact"
```
### Header
```
 header:
    phase_banner:
      tag: "WIP"
      text: "This is a work in progress."
    site_branding: "Scottish Government"
```
### Metadata
Use this section to assign a  label to the webpage. The breadcrumb trail allows users to create a hierarchy of the current page in relation to the website structure.
```  metadata:
    label: "Collection"
  navigation:
    breadcrumb_trail:
      - text: "Home"
      - text: "Agricultural Compendium"
      - text: "Agricultural and the economy"
```
## Configure _site.yml file (website template)
The ```_site.yml``` file configures the website as a whole. 

The navbar creates the tabs for the website structure. Navbar "topics", (Agricultural and the economy, Structure of Scottish Agriculture, Livestock etc) appear on the website as they are ordered in the script.

In a case where certain modules are not being published in the compendium, e.g. **Livestock**, then ``` - text: "Livestock" ``` and ``` href: "livestock.html ``` can be easily commented out of the script with a '#' symbol. This will disengage the specific .Rmd (and subsequent .html) file, and allow the website to run as normal.
```
name: "Agricultural Compendium"
title-prefix: "data.gov.scot"
navbar:
  left:
    - text: "Agricultural Statistics"
      href: "index.html"
    - text: "Data by publication"
      href: "data_publication_list.html"
    #- text: "Agricultural Compendium"
    #  href: "compendium.html"
...
```
More website configuration options are available below.

One stand out could be ```number_sections: false``` which will remove all section nunmbering.
```output:
  html_document:
    code_download: false
    df_print: paged
    fig_caption: true
    number_sections: false
    self_contained: false
    template: "_template.html"
    toc: true
    toc_depth: 2
    toc_float: false
```

## Build Website
To render all pages on the website use the ```Build pane -> Build Website``` which calls the command ``` rmarkdown::render_site() ```. RStudio will then search through the current working directory and create a .html file for every .Rmd file. Once all .html files are created and configured using the sgtemplate, a pop up window will appear to allow the user to preview the website.
![image](https://github.com/DavidFrenchSG/compendium_data_gov_scot/assets/144359744/324104f9-1173-496d-8599-2f61f61739ae)
