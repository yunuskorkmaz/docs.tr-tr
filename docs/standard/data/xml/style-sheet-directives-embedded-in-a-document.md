---
title: Bir belge içine katıştırılmış stil sayfası yönergeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fa671304c611db571b160cd1d960b83bf451c9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569336"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="37457-102">Bir belge içine katıştırılmış stil sayfası yönergeleri</span><span class="sxs-lookup"><span data-stu-id="37457-102">Style Sheet Directives Embedded in a Document</span></span>
<span data-ttu-id="37457-103">Bazen, stil sayfası yönergesinde varolan XML içeriyor `<?xml:stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="37457-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="37457-104">Microsoft Internet Explorer alternatif olarak bu kabul `<?xml-stylesheet?>` sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="37457-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="37457-105">XML veri içerdiğinde bir `<?xml:stylesheet?>` yönerge, aşağıdaki veri gösterildiği gibi bu verileri XML belge nesne modeli (DOM) içine yüklemeyi denerken bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37457-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 <span data-ttu-id="37457-106">Bu kaynaklanır `<?xml:stylesheet?>` geçersiz olarak kabul **instruction** DOM için</span><span class="sxs-lookup"><span data-stu-id="37457-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="37457-107">Tüm **instruction**, ad alanları XML belirtiminde göre Hayır iki nokta üst üste adları (NCNames) yalnızca olabilir, aksine nitelenmiş adlar (QNames).</span><span class="sxs-lookup"><span data-stu-id="37457-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>  
  
 <span data-ttu-id="37457-108">Ad alanı XML belirtiminde sahip etkisini Bölüm 6'dan **yük** ve **LoadXml** yöntemleri uygun belirtimi olan bir belgede:</span><span class="sxs-lookup"><span data-stu-id="37457-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>  
  
-   <span data-ttu-id="37457-109">Tüm öğesi türleri ve öznitelik adları sıfır veya bir iki nokta üst üste içerir.</span><span class="sxs-lookup"><span data-stu-id="37457-109">All element types and attribute names contain either zero or one colon.</span></span>  
  
-   <span data-ttu-id="37457-110">Hiçbir varlık adları, instruction hedefler ya da gösterim adları herhangi iki nokta üst üste içerir.</span><span class="sxs-lookup"><span data-stu-id="37457-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>  
  
 <span data-ttu-id="37457-111">İle `<?xml:stylesheet?>` bir iki nokta üst üste içeren, artık ikinci madde işareti kuralında ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="37457-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>  
  
 <span data-ttu-id="37457-112">World Wide Web Konsorsiyumu (W3C) ilişkilendirme stil sayfaları www.w3.org/TR/xml-stylesheet bulunan XML belgeleri sürüm 1.0 öneri ile göre XSLTstilsayfasınıbirXMLbelgesiileilişkilendirmekiçinişlemyönergesiolup`<?xml-stylesheet?>`, iki nokta üst üste değiştirerek bir tire ile.</span><span class="sxs-lookup"><span data-stu-id="37457-112">According to the World Wide Web Consortium (W3C) Associating Style Sheets with XML documents Version 1.0 Recommendation, located at www.w3.org/TR/xml-stylesheet, the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37457-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37457-113">See Also</span></span>  
 [<span data-ttu-id="37457-114">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="37457-114">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
