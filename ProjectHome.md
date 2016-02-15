# WSDL viewer #

WSDL has its constructive logic, but it is hard to read / understand the content by business professionals (mostly non-programmers).

This XSLT transforms the WSDL into HTML. The HTML is a human-readable documentation of the web service API, method list, message formats in a tree-like view and the syntax-highlighted source code with HTML links for fast jump to related information.

A set of WSDL-s can be converted into web pages (HTML) in a batch process (i.e. an ANT script, that has native XSLT support).

Another elegant option is to add the user-friendly face directly into the WSDL. This way by opening the WSDL in a browser the transformation prepares on-fly the HTML view. This requires just this changes in WSDL:

  * The WSDL is just an XML. Adding a processing instruction can suggest the browser to use on-fly the wsdl-viewer XSLT to convert the WSDL into a "nicer" HTML page. Example of the processing instruction in a WSDL:
```
      <?xml version="1.0" encoding="utf-8"?>
      <?xml-stylesheet type="text/xsl" href="wsdl-viewer.xsl"?>

      <wsdl:definitions ...>
          <!-- ... Here is the service declaration ... -->
      </wsdl:definitions>
```
> > Of course in this case the XSLT is expected to be in the same directory as the WSDL. You can define also an absolute URL (i.e. <?xml-stylesheet type="text/xsl" href="http://tomi.vanek.sk/xml/wsdl-viewer.xsl"?>).
  * The web-browsers (in Windows) are not able by default automatically recognize the .wsdl file type (suffix). For the type recognition the WSDL file has to be renamed: add the suffix .xml - i.e. myservice.wsdl.xml.

The tool WSDL-viewer has moved to Apache Woden project.