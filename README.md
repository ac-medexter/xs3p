# xs3p XSD documentation generator

This stylesheet transforms XSD (XML Schema Definition) files into 
human-readable documentation in HTML format.

Features:
 - [Bootstrap](https://getbootstrap.com "Bootstrap homepage") HTML toolkit
 - Output of UTF-8 encoded files
 - Output of HTML5
 - [Markdown](https://daringfireball.net/projects/markdown/ "Markdown homepage")
   formatting support in `<documentation>` elements, powered by
   [markdown-it](https://github.com/markdown-it/markdown-it "markdown-it homepage")

## Usage

1. Add the following definition to your XSD file immediately following the 
   `<?xml version="1.0" encoding="UTF-8"?>` or similar element:
   ```xml
   <?xml-stylesheet type="text/xsl" href="xs3p.xsl"?>
   ```
2. In your XSD, adjust the `xs3p.xsl` file location to point to the XSL 
   file in your target environment (filesystem or HTTP).
3. Open the XSD in a browser that permits accessing data in the local 
   filesystem (e.g. Firefox) or place both files on an HTTP server and 
   access the XSD via HTTP.

### Alternate Usage

1. Install an XSLT interpreter
   ```shell
   apt-get install xsltproc
   ```
2. To this cloned repo, add your XSD file `your-schema.xsd`
3. Create a links file `links.xml`
   ```xml
   <?xml version="1.0"?>
   <links>
      <schema file-location="molis.xsd" docfile-location="molis.xsd.html"/>
   </links>
   ```
5. Generate a static HTML documentation
   ```shell
   xsltproc --stringparam title "MOLIS XML schema"  \
            --stringparam searchIncludedSchemas true \
            --stringparam searchImportedSchemas true \
            xs3p.xsl your-schema.xsd > your-schema.xsd.html
   ```

### Known issues

 * There is currently no way to inline the Bootstrap and jQuery sources, thus
   those files must be fetched when viewing the documentation. Their URLs can
   be set, though, so you could serve them locally if offline viewing is a
   requirement.

## Aknowledgements

* Thanks for your work, setting this tool up and further improving it
    * https://github.com/Mapudo/xs3p
        * https://github.com/bitfehler/xs3p
      
