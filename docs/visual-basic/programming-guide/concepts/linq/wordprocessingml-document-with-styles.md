---
title: Styles2 ile WordprocessingML belgesi
ms.date: 07/20/2015
ms.assetid: a9136e4d-c368-4661-8049-7d45c679a236
ms.openlocfilehash: caf80014077bf57dc1ffb8eaeac6390cf4258015
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403556"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="a4ff2-102">Stillerle WordprocessingML Belgesi</span><span class="sxs-lookup"><span data-stu-id="a4ff2-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="a4ff2-103">Daha karmaşık WordprocessingML belgelerinin stillerle biçimlendirilen paragrafları vardır.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="a4ff2-104">WordprocessingML belgelerinin organizasyonel ile ilgili birkaç not yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="a4ff2-105">WordprocessingML belgeleri paketlere depolanır.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="a4ff2-106">Paketler birden çok parçaya sahiptir (parçalar, paketler bağlamında kullanıldığında belirgin bir anlama sahiptir; temelde, parçalar bir paketi oluşturacak şekilde daraltılmış dosyalardır).</span><span class="sxs-lookup"><span data-stu-id="a4ff2-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="a4ff2-107">Bir belge stillerle biçimlendirilen paragraflar içeriyorsa, bu stillerin uygulanmış olduğu paragrafları içeren bir belge bölümü olur.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="a4ff2-108">Ayrıca, belge tarafından başvurulan stilleri içeren bir stil bölümü de olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="a4ff2-109">Paketlere erişirken, bu işlemi, rastgele bir yol kullanmak yerine parçalar arasındaki ilişkilerle yapmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="a4ff2-110">Bu sorun, WordprocessingML belge öğreticisindeki Içerik Işleme kapsamının ötesinde, ancak bu öğreticide yer alan örnek programlar doğru yaklaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="a4ff2-111">Stilleri kullanan bir belge</span><span class="sxs-lookup"><span data-stu-id="a4ff2-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="a4ff2-112">[WordprocessingML belgeleri (Visual Basic) konusunun şeklinde](shape-of-wordprocessingml-documents.md) sunulan WordML örneği çok basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-112">The WordML example presented in the [Shape of WordprocessingML Documents (Visual Basic)](shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="a4ff2-113">Aşağıdaki belge daha karmaşıktır: stillerle biçimlendirilen paragraflar vardır.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="a4ff2-114">Bir Office Open XML belgesi oluşturan XML 'yi görmenin en kolay yolu, [Office Open XML belge parçalarını (Visual Basic) çıkaran örneği](example-that-outputs-office-open-xml-document-parts.md)çalıştırmanız.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (Visual Basic)](example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="a4ff2-115">Aşağıdaki belgede, ilk paragraf stile sahiptir `Heading1` .</span><span class="sxs-lookup"><span data-stu-id="a4ff2-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="a4ff2-116">Varsayılan stili olan bir dizi paragraf vardır.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="a4ff2-117">Ayrıca, stili olan bir dizi paragraf de vardır `Code` .</span><span class="sxs-lookup"><span data-stu-id="a4ff2-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="a4ff2-118">Bu göreli karmaşıklık nedeniyle, LINQ to XML ayrıştırılmaya yönelik daha ilgi çekici bir belgedir.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="a4ff2-119">Varsayılan olmayan stillerdeki bu paragraflarda, paragraf öğelerinin adlı bir alt öğesi vardır ve bu, `w:pPr` sırasıyla bir alt öğesi vardır `w:pStyle` .</span><span class="sxs-lookup"><span data-stu-id="a4ff2-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="a4ff2-120">Bu öğenin, `w:val` stil adını içeren bir özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="a4ff2-121">Paragrafta varsayılan stil varsa, paragraf öğesinin bir alt öğesi olmadığı anlamına gelir `w:p.Pr` .</span><span class="sxs-lookup"><span data-stu-id="a4ff2-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a4ff2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4ff2-122">See also</span></span>

- [<span data-ttu-id="a4ff2-123">Office Open XML WordprocessingML belgelerinin ayrıntıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4ff2-123">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](details-of-office-open-xml-wordprocessingml-documents.md)
