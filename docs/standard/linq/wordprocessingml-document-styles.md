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
# <a name="wordprocessingml-document-with-styles-linq-to-xml"></a><span data-ttu-id="6c3e0-103">Stillerle WordprocessingML belgesi (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6c3e0-103">WordprocessingML document with styles (LINQ to XML)</span></span>

<span data-ttu-id="6c3e0-104">Bu makalede, [WordprocessingML BELGELERININ XML şekilinden](xml-shape-wordprocessingml-documents.md)daha karmaşık bir WordprocessingML belgesi sunulmaktadır; Özellikle, paragrafları stillerle biçimlendirilen bir belge gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c3e0-104">This article presents a WordprocessingML document that is more complicated than the one in [The XML shape of WordprocessingML documents](xml-shape-wordprocessingml-documents.md); specifically, it presents a document whose paragraphs are formatted with styles.</span></span>

<span data-ttu-id="6c3e0-105">Stilleri anlamak için belge yapısıyla ilgili bir şey bilmeniz yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="6c3e0-105">To understand styles, it's helpful to know something about document structure.</span></span> <span data-ttu-id="6c3e0-106">WordprocessingML belgesi, *parçaları*içeren bir *pakette* depolanır.</span><span class="sxs-lookup"><span data-stu-id="6c3e0-106">A WordprocessingML document is stored in a *package* that comprises *parts*.</span></span> <span data-ttu-id="6c3e0-107">Özellikle, terim *paketi* bir zip arşivine karşılık gelir ve TERIMI *bölüm* ZIP içinde depolanan bir dosyaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="6c3e0-107">Specifically, the term *package* corresponds to a ZIP archive and the term *part* corresponds to a file stored within the ZIP.</span></span> <span data-ttu-id="6c3e0-108">Bir belge stillerle biçimlendirilen paragraflar içeriyorsa, bunlara uygulanmış Stiller içeren bir belge bölümü ve belge bölümünde başvurulan stilleri tanımlayan bir stil bölümü olur.</span><span class="sxs-lookup"><span data-stu-id="6c3e0-108">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them, and a style part that defines the styles referenced in the document part.</span></span>

<span data-ttu-id="6c3e0-109">Bir Office Open XML belgesi oluşturan XML 'yi görmenin en kolay yolu, örneğin [Office Open XML belge parçalarını oluşturan örnek](example-outputs-office-open-xml-document-parts.md)örneğini çalıştırmanız.</span><span class="sxs-lookup"><span data-stu-id="6c3e0-109">The easiest way to see the XML that makes up an Office Open XML document is to run the example in [Example that outputs Office Open XML document parts](example-outputs-office-open-xml-document-parts.md).</span></span>

<span data-ttu-id="6c3e0-110">Bir pakete eriştiğinizde, bunu, rastgele bir yoldan değil parçalar arasındaki ilişkilerle yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c3e0-110">When you access a package, you should do so through the relationships among parts, not through an arbitrary path.</span></span> <span data-ttu-id="6c3e0-111">Bu sorun, geçerli öğreticinin kapsamının ötesinde, ancak bu ve diğer öğretici makalelerindeki örnek programlar doğru yaklaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c3e0-111">This issue is beyond the scope of the current tutorial, but the example programs in this and other tutorial articles demonstrate the correct approach.</span></span>

## <a name="example-a-document-that-uses-styles"></a><span data-ttu-id="6c3e0-112">Örnek: stilleri kullanan bir belge</span><span class="sxs-lookup"><span data-stu-id="6c3e0-112">Example: A document that uses styles</span></span>

<span data-ttu-id="6c3e0-113">Aşağıdaki belgede stillerle biçimlendirilen paragraflar vardır.</span><span class="sxs-lookup"><span data-stu-id="6c3e0-113">The following document has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="6c3e0-114">İlk paragrafın stili `Heading1` ve diğer paragrafları `Code` stili veya varsayılan stili vardır.</span><span class="sxs-lookup"><span data-stu-id="6c3e0-114">The first paragraph has the style `Heading1` and other paragraphs have the `Code` style or the default style.</span></span> <span data-ttu-id="6c3e0-115">Varsayılan olmayan stillerdeki paragraflar için, paragraf öğelerinin adlı bir alt öğesi vardır `w:pPr` ve buna karşılık bir alt öğesi vardır `w:pStyle` .</span><span class="sxs-lookup"><span data-stu-id="6c3e0-115">For paragraphs with non-default styles the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="6c3e0-116">Bu öğenin, `w:val` stil adını içeren bir özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="6c3e0-116">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="6c3e0-117">Varsayılan stile sahip paragraflar için, paragraf öğesinin bir `w:p.Pr` alt öğesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6c3e0-117">For paragraphs with the default style, the paragraph element doesn't have a `w:p.Pr` child element.</span></span>

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
