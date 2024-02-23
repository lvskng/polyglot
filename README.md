# polyglot

## What is polyglot?
polyglot is a simple helper tool to manage your i18n files more efficiently.

## How?
If your framework uses the i18n_<lang>.properties format of internationalization files (eg. SAP UI5, SAP MDK), this tool allows you to auto-generate them from a config file in a more freindly  and human-readable syntax.

## Which syntax?
polyglot uses the HCL (HashiCorp Configuration Language) format as an input and can generate the files in the i18n.properties format for you. 

### Example
i18n.hcl
```
langs = ["en", "fr", "de"]

#Optional
default = "en"

#Define your translations as nested blocks
mainPage {
  #You can use labels to represent empty parent blocks
  header "title" {
    en = "Hello, world!"
    de = "Hallo, Welt!"
    fr = "Bonjour le monde!"
  }
  items {
    computer {
      #Use 'all' directive to define all words with the same string
      fr = "ordinateur"
      all = "computer"
    }
    wine {
      de = "Wein"
      en = "wine"
      fr = "vin"
    }
  }
}
```
The HCL format is far more powerful than needed for this specific purpose, but has a more pleasant syntax than JSON or YAML. [Other features of HCL](https://github.com/hashicorp/hcl) might / should work as well, but are not tested yet.

## Can I migrate existing projects to polyglot?
Yes! If you give polyglot the flag `-migrate` and optionally provide the `-m-in`(input directory) and `-m-out`(output file path) flag parameters, it will read your existing i18n.properties files and create your i18n.hcl file for you.

## How do I use it?
```
Usage of ./polyglot:
  -i string
        Specify input file (default "i18n.hcl")
  -m-in string
        Migration: input directory (default ".")
  -m-out string
        Migration: output file (default "i18n.hcl")
  -migrate
        Translate a directory of i18n .properties files to a polyglot .hcl file
  -o string
        Specify output directory (default "./out")
  -s string
        Specify path separator for generated file (default ".")
```

## Are there more features coming?
Perhaps :)
