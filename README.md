This is a rdflib plugin for parsing html5 microdata and modelling it as an
rdf graph. The rdflib and html5lib libraries are required. Basically you'll
be able to do something like:

```python
>>> import rdflib
>>> import rdflib_microdata
>>> g = rdflib.Graph()
>>> g.parse("https://raw.github.com/edsu/microdata/master/test-data/example.html", format="microdata")
>>> print g.serialize()
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rdf:RDF
   xmlns:ns1="http://schema.org/Person#"
   xmlns:ns2="http://schema.org/PostalAddress#"
   xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
>
  <rdf:Description rdf:about="http://www.xyz.edu/~jane">
    <ns1:name>Jane Doe</ns1:name>
    <ns1:email rdf:resource="mailto:jane-doe@xyz.edu"/>
    <rdf:type rdf:resource="http://schema.org/Person"/>
    <ns1:url rdf:resource="http://www.janedoe.com"/>
    <ns1:colleagues rdf:resource="http://www.xyz.edu/students/alicejones.html"/>
    <ns1:colleagues rdf:resource="http://www.xyz.edu/students/bobsmith.html"/>
    <ns1:telephone>(425) 123-4567</ns1:telephone>
    <ns1:address rdf:nodeID="TggQqDwH2"/>
    <ns1:image rdf:resource="janedoe.jpg"/>
    <ns1:jobTitle>Professor</ns1:jobTitle>
  </rdf:Description>
  <rdf:Description rdf:nodeID="TggQqDwH2">
    <rdf:type rdf:resource="http://schema.org/PostalAddress"/>
    <ns2:addressRegion>WA</ns2:addressRegion>
    <ns2:postalCode>98052</ns2:postalCode>
    <ns2:streetAddress>
          20341 Whitworth Institute
          405 N. Whitworth
        </ns2:streetAddress>
    <ns2:addressLocality>Seattle</ns2:addressLocality>
  </rdf:Description>
</rdf:RDF>
```

Author: [Ed Summers](mailto:ehs@pobox.com)

License: Public Domain
