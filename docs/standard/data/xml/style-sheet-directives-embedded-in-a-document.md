---
title: Belgeye Katıştırılmış Stil Sayfası Yönergeleri
ms.date: 03/30/2017
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 25946fd14a82428ae4367cd33511df68e9929203
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818576"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="c004a-102">Belgeye Katıştırılmış Stil Sayfası Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c004a-102">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="c004a-103">Bazen varolan XML, öğesinin stil sayfası yönergesini içerir `<?xml:stylesheet?>` .</span><span class="sxs-lookup"><span data-stu-id="c004a-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="c004a-104">Microsoft Internet Explorer, söz dizimini bir alternatif olarak kabul eder `<?xml-stylesheet?>` .</span><span class="sxs-lookup"><span data-stu-id="c004a-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="c004a-105">XML verileri `<?xml:stylesheet?>` aşağıdaki verilerde gösterildiği gibi bir yönerge içerdiğinde, bu VERILERI XML belge nesne modeli yüklemeye çalışmak (DOM) bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c004a-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="c004a-106">Bunun nedeni, `<?xml:stylesheet?>` Dom için geçersiz bir **processingyönergesini** kabul ettiğinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="c004a-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="c004a-107">XML belirtiminde ad alanlarına göre herhangi bir işlem **yönergesi**, nitelenmiş adların (QNames 'ler) aksine yalnızca iki nokta üst üste olmayan adlar (NCNames) olabilir.</span><span class="sxs-lookup"><span data-stu-id="c004a-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="c004a-108">XML belirtiminde ad alanlarının 6. bölümünde, **Load** ve **LoadXml** yöntemlerine sahip olmanın etkisi bir belgede olur:</span><span class="sxs-lookup"><span data-stu-id="c004a-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="c004a-109">Tüm öğe türleri ve öznitelik adları sıfır veya bir iki nokta üst üste içerir.</span><span class="sxs-lookup"><span data-stu-id="c004a-109">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="c004a-110">Hiçbir varlık adı, Işleme yönergesi hedefi veya gösterim adı herhangi bir iki nokta üst üste içermez.</span><span class="sxs-lookup"><span data-stu-id="c004a-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="c004a-111">`<?xml:stylesheet?>`İki nokta üst üste içeren, artık kuralı ikinci madde işaretiyle ihlal edersiniz.</span><span class="sxs-lookup"><span data-stu-id="c004a-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="c004a-112">World Wide Web Konsorsiyumu (W3C) [Ile xml belgelerinin sürüm 1,0 önerisi Ile ilişkilendirme](https://www.w3.org/TR/xml-stylesheet/), XSLT stil SAYFASıNı bir XML belgesi ile ilişkilendirmek için işleme yönergesi, `<?xml-stylesheet?>` iki nokta üst üste yerine bir tire ile.</span><span class="sxs-lookup"><span data-stu-id="c004a-112">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="c004a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c004a-113">See also</span></span>

- [<span data-ttu-id="c004a-114">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="c004a-114">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
