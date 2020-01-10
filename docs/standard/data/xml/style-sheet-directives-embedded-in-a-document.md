---
title: Belgeye Katıştırılmış Stil Sayfası Yönergeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 19e25ab7262bb006144eea71e74bd7454066b3f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710160"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="547c6-102">Belgeye Katıştırılmış Stil Sayfası Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="547c6-102">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="547c6-103">Bazen mevcut XML, `<?xml:stylesheet?>`stil sayfası yönergesini içerir.</span><span class="sxs-lookup"><span data-stu-id="547c6-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="547c6-104">Microsoft Internet Explorer, `<?xml-stylesheet?>` sözdizimine alternatif olarak bunu kabul eder.</span><span class="sxs-lookup"><span data-stu-id="547c6-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="547c6-105">XML verileri, aşağıdaki verilerde gösterildiği gibi bir `<?xml:stylesheet?>` yönergesi içerdiğinde, bu verileri XML Belge Nesne Modeli yüklemeye çalışmak (DOM) bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="547c6-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="547c6-106">Bunun nedeni, `<?xml:stylesheet?>` DOM 'a geçersiz bir işlem **yönergesi yönergesi** olarak kabul edildiği için oluşur.</span><span class="sxs-lookup"><span data-stu-id="547c6-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="547c6-107">XML belirtiminde ad alanlarına göre herhangi bir işlem **yönergesi**, nitelenmiş adların (QNames 'ler) aksine yalnızca iki nokta üst üste olmayan adlar (NCNames) olabilir.</span><span class="sxs-lookup"><span data-stu-id="547c6-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="547c6-108">XML belirtiminde ad alanlarının 6. bölümünde, **Load** ve **LoadXml** yöntemlerine sahip olmanın etkisi bir belgede olur:</span><span class="sxs-lookup"><span data-stu-id="547c6-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="547c6-109">Tüm öğe türleri ve öznitelik adları sıfır veya bir iki nokta üst üste içerir.</span><span class="sxs-lookup"><span data-stu-id="547c6-109">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="547c6-110">Hiçbir varlık adı, Işleme yönergesi hedefi veya gösterim adı herhangi bir iki nokta üst üste içermez.</span><span class="sxs-lookup"><span data-stu-id="547c6-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="547c6-111">İki nokta üst üste içeren `<?xml:stylesheet?>`, şimdi ikinci madde işareti içindeki kuralı ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="547c6-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="547c6-112">World Wide Web Konsorsiyumu (W3C) [Ile xml belgelerinin sürüm 1,0 önerisi Ile ilişkilendirme](https://www.w3.org/TR/xml-stylesheet/)IÇIN, XSLT stil SAYFASıNı bir XML belgesi ile ilişkilendirme işleme yönergesi, iki nokta üst üste değiştirme ile `<?xml-stylesheet?>`.</span><span class="sxs-lookup"><span data-stu-id="547c6-112">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="547c6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="547c6-113">See also</span></span>

- [<span data-ttu-id="547c6-114">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="547c6-114">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
