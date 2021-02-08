---
description: 'Daha fazla bilgi edinin: bir belgeye katıştırılmış stil sayfası yönergeleri'
title: Belgeye Katıştırılmış Stil Sayfası Yönergeleri
ms.date: 03/30/2017
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 3585cc2f9e7d931a89c1f81283282712195720f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782942"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="f8a9e-103">Belgeye Katıştırılmış Stil Sayfası Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f8a9e-103">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="f8a9e-104">Bazen varolan XML, öğesinin stil sayfası yönergesini içerir `<?xml:stylesheet?>` .</span><span class="sxs-lookup"><span data-stu-id="f8a9e-104">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="f8a9e-105">Microsoft Internet Explorer, söz dizimini bir alternatif olarak kabul eder `<?xml-stylesheet?>` .</span><span class="sxs-lookup"><span data-stu-id="f8a9e-105">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="f8a9e-106">XML verileri `<?xml:stylesheet?>` aşağıdaki verilerde gösterildiği gibi bir yönerge içerdiğinde, bu VERILERI XML belge nesne modeli yüklemeye çalışmak (DOM) bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8a9e-106">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="f8a9e-107">Bunun nedeni, `<?xml:stylesheet?>` Dom için geçersiz bir **processingyönergesini** kabul ettiğinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="f8a9e-107">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="f8a9e-108">XML belirtiminde ad alanlarına göre herhangi bir işlem **yönergesi**, nitelenmiş adların (QNames 'ler) aksine yalnızca iki nokta üst üste olmayan adlar (NCNames) olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8a9e-108">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="f8a9e-109">XML belirtiminde ad alanlarının 6. bölümünde, **Load** ve **LoadXml** yöntemlerine sahip olmanın etkisi bir belgede olur:</span><span class="sxs-lookup"><span data-stu-id="f8a9e-109">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="f8a9e-110">Tüm öğe türleri ve öznitelik adları sıfır veya bir iki nokta üst üste içerir.</span><span class="sxs-lookup"><span data-stu-id="f8a9e-110">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="f8a9e-111">Hiçbir varlık adı, Işleme yönergesi hedefi veya gösterim adı herhangi bir iki nokta üst üste içermez.</span><span class="sxs-lookup"><span data-stu-id="f8a9e-111">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="f8a9e-112">`<?xml:stylesheet?>`İki nokta üst üste içeren, artık kuralı ikinci madde işaretiyle ihlal edersiniz.</span><span class="sxs-lookup"><span data-stu-id="f8a9e-112">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="f8a9e-113">World Wide Web Konsorsiyumu (W3C) [Ile xml belgelerinin sürüm 1,0 önerisi Ile ilişkilendirme](https://www.w3.org/TR/xml-stylesheet/), XSLT stil SAYFASıNı bir XML belgesi ile ilişkilendirmek için işleme yönergesi, `<?xml-stylesheet?>` iki nokta üst üste yerine bir tire ile.</span><span class="sxs-lookup"><span data-stu-id="f8a9e-113">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8a9e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8a9e-114">See also</span></span>

- [<span data-ttu-id="f8a9e-115">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="f8a9e-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
