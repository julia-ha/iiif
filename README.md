# IIIF resources and examples

## Resources

- **IIIF Presentation API** ([2.1.1](https://iiif.io/api/presentation/2.1/)) ([3.0](https://iiif.io/api/presentation/3.0/))
- **IIIF Image API** ([2.1.1](https://iiif.io/api/image/2.1/)) ([3.0](https://iiif.io/api/image/3.0/))
- [Web Annotation Data Model](https://www.w3.org/TR/annotation-model/)

## IIIF Presentation Manifest examples

### v2.1.1

- [Manifest using static image](https://jstor-labs.github.io/iiif-example/manifests/Ginevra_de_Benci-static.json)
- [Manifest using Labs IIIF image service](https://jstor-labs.github.io/iiif-example/manifests/Ginevra_de_Benci-labs.json)
- [Manifest using 3rd party IIIF image service](https://jstor-labs.github.io/iiif-example/manifests/Ginevra_de_Benci-iiifhosting.json)

### v3

TODO

## Visual essay example

[Ginevra de' Benci](https://dev.visual-essays.app/essay/jstor-labs/iiif-example/ginevra-de-benci)

## Annotations

TODO

### Creating a manifest

#### Manually

#### Labs IIIF service (option 1)

**Post JSON docment to:** `https://iiif.visual-essays.app/presentation/create`

**General request document structure:**

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

**Example using the Genevra image:**

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

**Generated manifest:** https://iiif.visual-essays.app/presentation/e39d51b68f1d98e822a5783cec6635fc0e3746dfef532c4fc4292070/manifest

#### Labs IIIF service (option 2)

**Post JSON docment to:** `https://iiif-v2.visual-essays.app/manifest/`

**General request document structure:**

```json
{
    "url": "",
    "label": "",
    "other metadata": ""
}
```

**Example using the Genevra image:**

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

**Generated manifest:** https://iiif-v2.visual-essays.app/manifest/1f1bb3168b5785e2735a980d7e7fb99173fcf238d5526aa29872963a4ffd3750

#### Dynamically, using ve-image tag within Visual Essays tool

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
