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
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="d134a-102">Belgeye Katıştırılmış Stil Sayfası Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d134a-102">Style Sheet Directives Embedded in a Document</span></span>

<span data-ttu-id="d134a-103">Bazen varolan XML, öğesinin `<?xml:stylesheet?>`stil sayfası yönergesini içerir.</span><span class="sxs-lookup"><span data-stu-id="d134a-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="d134a-104">Microsoft Internet Explorer, `<?xml-stylesheet?>` söz dizimini bir alternatif olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d134a-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="d134a-105">XML verileri aşağıdaki verilerde gösterildiği gibi `<?xml:stylesheet?>` bir yönerge içerdiğinde, bu verileri XML belge nesne modeli yüklemeye ÇALıŞMAK (DOM) bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d134a-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

<span data-ttu-id="d134a-106">Bunun nedeni, `<?xml:stylesheet?>` Dom için geçersiz bir **processingyönergesini** kabul ettiğinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="d134a-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="d134a-107">XML belirtiminde ad alanlarına göre herhangi bir işlem **yönergesi**, nitelenmiş adların (QNames 'ler) aksine yalnızca iki nokta üst üste olmayan adlar (NCNames) olabilir.</span><span class="sxs-lookup"><span data-stu-id="d134a-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>

<span data-ttu-id="d134a-108">XML belirtiminde ad alanlarının 6. bölümünde, **Load** ve **LoadXml** yöntemlerine sahip olmanın etkisi bir belgede olur:</span><span class="sxs-lookup"><span data-stu-id="d134a-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>

- <span data-ttu-id="d134a-109">Tüm öğe türleri ve öznitelik adları sıfır veya bir iki nokta üst üste içerir.</span><span class="sxs-lookup"><span data-stu-id="d134a-109">All element types and attribute names contain either zero or one colon.</span></span>

- <span data-ttu-id="d134a-110">Hiçbir varlık adı, Işleme yönergesi hedefi veya gösterim adı herhangi bir iki nokta üst üste içermez.</span><span class="sxs-lookup"><span data-stu-id="d134a-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>

<span data-ttu-id="d134a-111">İki nokta `<?xml:stylesheet?>` üst üste içeren, artık kuralı ikinci madde işaretiyle ihlal edersiniz.</span><span class="sxs-lookup"><span data-stu-id="d134a-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>

<span data-ttu-id="d134a-112">World Wide Web Konsorsiyumu (W3C) [Ile xml belgelerinin sürüm 1,0 önerisi Ile ilişkilendirme](https://www.w3.org/TR/xml-stylesheet/), XSLT stil SAYFASıNı bir XML belgesi `<?xml-stylesheet?>`ile ilişkilendirmek için işleme yönergesi, iki nokta üst üste yerine bir tire ile.</span><span class="sxs-lookup"><span data-stu-id="d134a-112">According to the World Wide Web Consortium (W3C) [Associating Style Sheets with XML documents Version 1.0 Recommendation](https://www.w3.org/TR/xml-stylesheet/),  the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>

## <a name="see-also"></a><span data-ttu-id="d134a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d134a-113">See also</span></span>

- [<span data-ttu-id="d134a-114">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="d134a-114">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
