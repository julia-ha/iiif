# IIIF resources and examples

## Resources

### Specifications
- **IIIF Presentation** ([2.1.1](https://iiif.io/api/presentation/2.1/)) ([3.0](https://iiif.io/api/presentation/3.0/))
- **IIIF Image** ([2.1.1](https://iiif.io/api/image/2.1/)) ([3.0](https://iiif.io/api/image/3.0/))
- **W3C** [Web Annotation Data Model](https://www.w3.org/TR/annotation-model/) and [protocol](https://www.w3.org/TR/annotation-protocol/)

### Tools and sites

- [Mirador (v3)](https://projectmirador.org/) ([v2](https://projectmirador.org/demo/)) - IIIF viewer
- [Universal Viewer](https://universalviewer.io/) - IIIF viewer
- [OpenSeadragon](https://openseadragon.github.io/) - Image viewer javascript library, not IIIF specific
- [Annatorious](https://recogito.github.io/annotorious/) ([Github](https://github.com/recogito/annotorious))- Annotation tool for generating annotations compatible with [W3C Web Annotation Data Model](https://www.w3.org/TR/annotation-model/) and [Protocol](https://www.w3.org/TR/annotation-protocol/)

### APIs

- [OpenSeadragon](https://openseadragon.github.io/docs/)
- [Annatorious (Openseadragon plugin)](https://recogito.github.io/annotorious/api-docs/osd-plugin/) 

### Demos and other useful info

- [awesome-iiif](https://github.com/IIIF/awesome-iiif) - A list of lists of awesome IIIF resources
- [kanzaki](https://www.kanzaki.com/) - Some great [IIIF examples](https://www.kanzaki.com/works/2016/pub/image-annotator) and demos by [Masahide Kanzaki](https://www.kanzaki.com/info/who)
- [IIIF manifest validator](https://iiif.io/api/presentation/validator/service/)

## IIIF Presentation Manifest examples

### v2.1.1

- [Manifest using static image](https://jstor-labs.github.io/iiif-example/manifests/Ginevra_de_Benci-static.json) ([Github](manifests/Ginevra_de_Benci-static.json))
- [Manifest using Labs IIIF image service](https://jstor-labs.github.io/iiif-example/manifests/Ginevra_de_Benci-labs.json) ([Github](manifests/Ginevra_de_Benci-labs.json))
- [Manifest using 3rd party IIIF image service](https://jstor-labs.github.io/iiif-example/manifests/Ginevra_de_Benci-iiifhosting.json) ([Github](manifests/Ginevra_de_Benci-iiifhosting.json))

### v3

TODO

## Visual essay example

Use of IIIF manifests in a JSTOR Labs [visual essay](https://dev.visual-essays.app/essay/jstor-labs/iiif-example/ginevra-de-benci) using the Wikimedia Commons Ginevra de' Benci image.

- [Visual essay Markdown source](ginevra-de-benci.md) ([raw](https://raw.githubusercontent.com/JSTOR-Labs/iiif-example/develop/ginevra-de-benci.md))

## Annotations

- Labs annotation server endpoint: [https://annotations.visual-essay/](https://annotations.visual-essay) ([Github](https://github.com/JSTOR-Labs/ve-annotations), adapted from[azaroth42/MangoServer](https://github.com/azaroth42/MangoServer))
- [Sample annotations for Ginevra image in visual essay](https://annotations.visual-essays.app/ve/?target=https%3A%2F%2Fvisual-essays.app%2Fjstor-labs%2Fve-contentginevra-de-benci%2F3d4b78a087e203f982c66c0e621b33ab7d76de5680e8f8b22e4dfe0f5fd5667a)
- Labs annotation admin tool - TBD

### Creating a manifest

IIIF presentation manifests can be created manually or using an automated service.  In either case
the resulting JSON file needs to be accessible via a public URL.

#### Manual manifest generation and hosting

One easy method for manually creating and hosting an IIIF manifest is to use Github.  Some of the example manifests used in this document use this approach and can be seen here:

- [Manifest using static image](/manifests/Ginevra_de_Benci-static.json)
- [Manifest using Labs IIIF image service](/manifests/Ginevra_de_Benci-labs.json)
- [Manifest using 3rd party IIIF image service](/manifests/Ginevra_de_Benci-iiifhosting.json)

#### Labs IIIF service (option 1)

JSTOR Labs has also created a service for generating and storing manifests.

*Post JSON document to:* `https://iiif.visual-essays.app/presentation/create`  
*General request document structure:*
```json
{
    "@context": "http://iiif.io/api/presentation/2/context.json",
    "label": "",
    "description": "",
    "attribution": "",
    "license": "",
    "metadata": [
        {"label": "", "value": ""}
    ],
    "sequences": [{
        "label": "",
        "canvases": [{
            "height": 3000,
            "width": 3000,
            "images": [{
                "region": "full",
                "size": "1000,",
                "rotation": "0",
                "url": ""
            }]
        }]
    }]
}
```

*Example using the Wikimedia Commons Ginevra de' Benci image:*
```json
{
    "@context": "http://iiif.io/api/presentation/2/context.json",
    "label": "Ginevra de' Benci, painting by Leonardo da Vinci",
    "description": "Ginevra de' Benci is a portrait painting by Leonardo da Vinci of the 15th-century Florentine aristocrat Ginevra de' Benci (born c.  1458). The oil-on-wood portrait was acquired by the National Gallery of Art in Washington, D.C. in 1967. The sum of US$5 million—an absolute record price at the time—came from the Ailsa Mellon Bruce Fund and was paid to the Princely Family of Liechtenstein. It is the only painting by Leonardo on public view in the Americas.",
    "attribution": "Wikimedia Commons and Google Art Project",
    "license": "Public domain",
    "metadata": [
        {"label": "Author", "value": "Leonardo da Vinci"},
        {"label": "Date", "value": "1474 - 1478"},
        {"label": "Type", "value": "Oil on panel"},
        {"label": "Size", "value": "38.1 cm × 37 cm (15.0 in × 15 in)"},
        {"label": "Location", "value": "National Gallery of Art, Washington, D.C."},
        {"label": "Image hosting service", "value": "JSTOR Labs"},
        {"label": "source", "value": "https://upload.wikimedia.org/wikipedia/commons/3/39/Leonardo_da_Vinci_-_Ginevra_de%27_Benci_-_Google_Art_Project.jpg"}
    ],
    "sequences": [{
        "label": "Ginevra de' Benci, painting by Leonardo da Vinci",
        "canvases": [{
            "height": 3000,
            "width": 3000,
            "images": [{
                "region": "full",
                "size": "1000,",
                "rotation": "0",
                "url": "https://upload.wikimedia.org/wikipedia/commons/3/39/Leonardo_da_Vinci_-_Ginevra_de%27_Benci_-_Google_Art_Project.jpg"
            }]
        }]
    }]
}
```
*Generated manifest:* https://iiif.visual-essays.app/presentation/e39d51b68f1d98e822a5783cec6635fc0e3746dfef532c4fc4292070/manifest

#### Labs IIIF service (option 2)

*Post JSON document to:* `https://iiif-v2.visual-essays.app/manifest/`
*General request document structure:*
```json
{
    "url": "",
    "label": "",
    "other metadata": ""
}
```

*Example using the Wikimedia Commons Ginevra de' Benci image:*
```json
{
    "url": "https://upload.wikimedia.org/wikipedia/commons/3/39/Leonardo_da_Vinci_-_Ginevra_de%27_Benci_-_Google_Art_Project.jpg",
    "label": "Ginevra de' Benci, painting by Leonardo da Vinci",
    "description": "Ginevra de' Benci is a portrait painting by Leonardo da Vinci of the 15th-century Florentine aristocrat Ginevra de' Benci (born c.  1458). The oil-on-wood portrait was acquired by the National Gallery of Art in Washington, D.C. in 1967. The sum of US$5 million—an absolute record price at the time—came from the Ailsa Mellon Bruce Fund and was paid to the Princely Family of Liechtenstein. It is the only painting by Leonardo on public view in the Americas.",
    "attribution": "Wikimedia Commons and Google Art Project",
    "license": "Public domain",
    "Author": "Leonardo da Vinci",
    "Date": "1474 - 1478",
    "Type": "Oil on panel",
    "Size": "38.1 cm × 37 cm (15.0 in × 15 in)",
    "Location": "National Gallery of Art, Washington, D.C.",
    "Image hosting service": "JSTOR Labs"
}
```
*Generated manifest:* https://iiif-v2.visual-essays.app/manifest/1f1bb3168b5785e2735a980d7e7fb99173fcf238d5526aa29872963a4ffd3750

#### Dynamically created, using ve-image tag within Visual Essays tool

```html
<param ve-image iiif
    "url"="https://upload.wikimedia.org/wikipedia/commons/3/39/Leonardo_da_Vinci_-_Ginevra_de%27_Benci_-_Google_Art_Project.jpg",
    "label"="Ginevra de' Benci, painting by Leonardo da Vinci",
    "description": "Ginevra de' Benci is a portrait painting by Leonardo da Vinci of the 15th-century Florentine aristocrat Ginevra de' Benci (born c.  1458). The oil-on-wood portrait was acquired by the National Gallery of Art in Washington, D.C. in 1967. The sum of US$5 million—an absolute record price at the time—came from the Ailsa Mellon Bruce Fund and was paid to the Princely Family of Liechtenstein. It is the only painting by Leonardo on public view in the Americas.",
    "attribution"="Wikimedia Commons and Google Art Project",
    "license"="Public domain",
    "Author"="Leonardo da Vinci",
    "Date"="1474 - 1478",
    "Type"="Oil on panel",
    "Size"="38.1 cm × 37 cm (15.0 in × 15 in)",
    "Location"="National Gallery of Art, Washington, D.C.">
```
