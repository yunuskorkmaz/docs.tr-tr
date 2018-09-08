---
title: Belgeye katıştırılmış stil sayfası yönergeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65987c5e29d593758b21259d6367202c882df2de
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201835"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="4224a-102">Belgeye katıştırılmış stil sayfası yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4224a-102">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="4224a-103">Bazen, var olan XML stil sayfası yönergesi içeren `<?xml:stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="4224a-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="4224a-104">Microsoft Internet Explorer alternatif olarak bu kabul `<?xml-stylesheet?>` söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="4224a-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="4224a-105">XML verilerini içerdiğinde bir `<?xml:stylesheet?>` yönerge, aşağıdaki veriler gösterildiği gibi XML belge nesne modeli (DOM) içine bu verileri yüklemeye çalışırken bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4224a-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="4224a-106">Bu durum oluşur `<?xml:stylesheet?>` geçersiz olarak kabul edilir **instruction** yerli için</span><span class="sxs-lookup"><span data-stu-id="4224a-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="4224a-107">Tüm **instruction**, ad alanları XML belirtiminde göre no-iki nokta üst üste adları (NCNames) yalnızca olabilir, yerine tam adları (QNames).</span><span class="sxs-lookup"><span data-stu-id="4224a-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="4224a-108">Bölüm 6 ad alanları XML belirtiminde olan etkisini **yük** ve **LoadXml** yöntemleri uygun belirtimi bir belgede olmasıdır:</span><span class="sxs-lookup"><span data-stu-id="4224a-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="4224a-109">Tüm öğe türleri ve öznitelik adları sıfır veya bir iki nokta üst üste içerir.</span><span class="sxs-lookup"><span data-stu-id="4224a-109">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="4224a-110">Herhangi iki nokta üst üste, hiçbir varlık adları, instruction hedefler ya da bildirim adları içeriyor.</span><span class="sxs-lookup"><span data-stu-id="4224a-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="4224a-111">İle `<?xml:stylesheet?>` bir iki nokta üst üste içeren, Şimdi ikinci madde işareti kuralı ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="4224a-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="4224a-112">World Wide Web Consortium (W3C) göre [XML ile ilişkilendirme stil sayfaları, sürüm 1.0 öneri belgeleri](https://www.w3.org/TR/xml-stylesheet/), bir XSLT stil sayfası bir XML belgesi ile ilişkilendirmek için işleme yönergesi `<?xml-stylesheet?>`, ile bir iki nokta üst üste değiştirerek dash.</span><span class="sxs-lookup"><span data-stu-id="4224a-112">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="4224a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4224a-113">See also</span></span>

- [<span data-ttu-id="4224a-114">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="4224a-114">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
