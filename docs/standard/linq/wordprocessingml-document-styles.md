---
title: Stil ile WordprocessingML belgesi-LINQ to XML
description: Paragrafları stillerle biçimlendirilen WordprocessingML belgeleri hakkında bilgi edinin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 40e35de6-ac93-4bba-88ab-a018cbe93873
ms.openlocfilehash: 7864ce5163d9dfb316c8288850210becdf55dc2d
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553237"
---
# <a name="wordprocessingml-document-with-styles-linq-to-xml"></a>Stillerle WordprocessingML belgesi (LINQ to XML)

Bu makalede, [WordprocessingML BELGELERININ XML şekilinden](xml-shape-wordprocessingml-documents.md)daha karmaşık bir WordprocessingML belgesi sunulmaktadır; Özellikle, paragrafları stillerle biçimlendirilen bir belge gösterir.

Stilleri anlamak için belge yapısıyla ilgili bir şey bilmeniz yararlı olur. WordprocessingML belgesi, *parçaları*içeren bir *pakette* depolanır. Özellikle, terim *paketi* bir zip arşivine karşılık gelir ve TERIMI *bölüm* ZIP içinde depolanan bir dosyaya karşılık gelir. Bir belge stillerle biçimlendirilen paragraflar içeriyorsa, bunlara uygulanmış Stiller içeren bir belge bölümü ve belge bölümünde başvurulan stilleri tanımlayan bir stil bölümü olur.

Bir Office Open XML belgesi oluşturan XML 'yi görmenin en kolay yolu, örneğin [Office Open XML belge parçalarını oluşturan örnek](example-outputs-office-open-xml-document-parts.md)örneğini çalıştırmanız.

Bir pakete eriştiğinizde, bunu, rastgele bir yoldan değil parçalar arasındaki ilişkilerle yapmanız gerekir. Bu sorun, geçerli öğreticinin kapsamının ötesinde, ancak bu ve diğer öğretici makalelerindeki örnek programlar doğru yaklaşımı gösterir.

## <a name="example-a-document-that-uses-styles"></a>Örnek: stilleri kullanan bir belge

Aşağıdaki belgede stillerle biçimlendirilen paragraflar vardır. İlk paragrafın stili `Heading1` ve diğer paragrafları `Code` stili veya varsayılan stili vardır. Varsayılan olmayan stillerdeki paragraflar için, paragraf öğelerinin adlı bir alt öğesi vardır `w:pPr` ve buna karşılık bir alt öğesi vardır `w:pStyle` . Bu öğenin, `w:val` stil adını içeren bir özniteliği vardır. Varsayılan stile sahip paragraflar için, paragraf öğesinin bir `w:p.Pr` alt öğesi yoktur.

```xml
<?xml version="1.0" encoding="utf-8"?>
<w:document
    xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:o="urn:schemas-microsoft-com:office:office"
    xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"
    xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"
    xmlns:v="urn:schemas-microsoft-com:vml"
    xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"
    xmlns:w10="urn:schemas-microsoft-com:office:word"
    xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"
    xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">
  <w:body>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Heading1" />
      </w:pPr>
      <w:r>
        <w:t>Parsing WordprocessingML with LINQ to XML</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">
      <w:r>
        <w:t>The following example prints to the console.</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r>
        <w:t>using System;</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t>class Program {</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t xml:space="preserve">    public static void </w:t>
      </w:r>
      <w:smartTag w:uri="urn:schemas-microsoft-com:office:smarttags" w:element="place">
        <w:r w:rsidRPr="00876F34">
          <w:t>Main</w:t>
        </w:r>
      </w:smartTag>
      <w:r w:rsidRPr="00876F34">
        <w:t>(string[] args) {</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t xml:space="preserve">        Console.WriteLine("Hello World");</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t xml:space="preserve">    }</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t>}</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">
      <w:r>
        <w:t>This example produces the following output:</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r>
        <w:t>Hello World</w:t>
      </w:r>
    </w:p>
    <w:sectPr w:rsidR="00A75AE0" w:rsidSect="00A75AE0">
      <w:pgSz w:w="12240" w:h="15840" />
      <w:pgMar w:top="1440" w:right="1800" w:bottom="1440" w:left="1800" w:header="720" w:footer="720" w:gutter="0" />
      <w:cols w:space="720" />
      <w:docGrid w:linePitch="360" />
    </w:sectPr>
  </w:body>
</w:document>
```
