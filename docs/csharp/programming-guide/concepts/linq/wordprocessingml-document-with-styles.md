---
title: Styles3 ile WordprocessingML Belge
ms.date: 07/20/2015
ms.assetid: 40e35de6-ac93-4bba-88ab-a018cbe93873
ms.openlocfilehash: 10697744680276a40fb7a175e4c04920c9e3c243
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167874"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="0e323-102">Stillerle WordprocessingML Belgesi</span><span class="sxs-lookup"><span data-stu-id="0e323-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="0e323-103">Daha karmaşık WordprocessingML belgeleri stilleri ile biçimlendirilmiş paragraflar var.</span><span class="sxs-lookup"><span data-stu-id="0e323-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="0e323-104">WordprocessingML belgelerin makyaj hakkında birkaç notlar yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0e323-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="0e323-105">WordprocessingML belgeleri paketler halinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="0e323-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="0e323-106">Paketlerin birden çok bölümü vardır (paketler bağlamında kullanıldığında parçaların açık bir anlamı vardır;</span><span class="sxs-lookup"><span data-stu-id="0e323-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="0e323-107">Bir belge stilleri ile biçimlendirilmiş paragraflar içeriyorsa, onlara uygulanan stilleri olan paragraflar içeren bir belge bölümü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0e323-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="0e323-108">Ayrıca, belge tarafından atıfta bulunulan stilleri içeren bir stil bölümü de olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0e323-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="0e323-109">Paketlere erişirken, bunu rasgele bir yol kullanmak yerine parçalar arasındaki ilişkiler yoluyla yapmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0e323-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="0e323-110">Bu sorun, WordprocessingML Belge öğreticisinde İçeriği Manipüle Etme kapsamının dışındadır, ancak bu öğreticide yer alan örnek programlar doğru yaklaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e323-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="0e323-111">Stilleri Kullanan Bir Belge</span><span class="sxs-lookup"><span data-stu-id="0e323-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="0e323-112">[WordprocessingML Belgelerin (C#)](./shape-of-wordprocessingml-documents.md) başlığı şeklinde sunulan WordML örneği çok basit bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="0e323-112">The WordML example presented in the [Shape of WordprocessingML Documents (C#)](./shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="0e323-113">Aşağıdaki belge daha karmaşıktır: Stilleri ile biçimlendirilmiş paragraflar vardır.</span><span class="sxs-lookup"><span data-stu-id="0e323-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="0e323-114">Office Open XML belgesini oluşturan XML'i görmenin en kolay [yolu, Office Open XML Belge Parçaları (C#) Çıktıları](./example-that-outputs-office-open-xml-document-parts.md)Örneği'ni çalıştırmaktır.</span><span class="sxs-lookup"><span data-stu-id="0e323-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (C#)](./example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="0e323-115">Aşağıdaki belgede, ilk paragrafın stili `Heading1`vardır.</span><span class="sxs-lookup"><span data-stu-id="0e323-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="0e323-116">Varsayılan stili olan birkaç paragraf vardır.</span><span class="sxs-lookup"><span data-stu-id="0e323-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="0e323-117">Stili `Code`olan bir dizi paragraf da vardır.</span><span class="sxs-lookup"><span data-stu-id="0e323-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="0e323-118">Bu göreceli karmaşıklık nedeniyle, bu XML LINQ ile ayrıştırmak için daha ilginç bir belgedir.</span><span class="sxs-lookup"><span data-stu-id="0e323-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="0e323-119">Varsayılan olmayan stilleri olan bu paragraflarda, paragraf öğelerinin `w:pPr`bir alt öğesi vardır, bu da bir alt öğeye `w:pStyle`sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0e323-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="0e323-120">Bu öğe, `w:val`stil adını içeren bir özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="0e323-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="0e323-121">Paragrafvarsayılan stili varsa, paragraf öğesi bir `w:p.Pr` alt öğe olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0e323-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
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
