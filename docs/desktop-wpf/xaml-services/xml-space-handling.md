---
title: XAML'de xml:space İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 886f906b6d1e3a10920dbf52e36bf76324c5a9f2
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071439"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="43180-102">XAML'de xml:space İşleme</span><span class="sxs-lookup"><span data-stu-id="43180-102">xml:space Handling in XAML</span></span>

<span data-ttu-id="43180-103">Öznitelik, `xml:space` nesne öğesi içindeki önemli beyaz boşluk işleme davranışını bildiren XML tanımlı bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="43180-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="43180-104">Bu davranış, bildirilen öğe `xml:space` içinde bulunan tüm içerik (iç metin) için alakalı ve aynı zamanda alt öğeleri kapsamları.</span><span class="sxs-lookup"><span data-stu-id="43180-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="43180-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="43180-105">XAML Attribute Usage</span></span>

```xaml
<object xml:space="preserve" />
```

 <span data-ttu-id="43180-106">\-veya -</span><span class="sxs-lookup"><span data-stu-id="43180-106">\- or -</span></span>

```xaml
<object xml:space="default" />
```

## <a name="remarks"></a><span data-ttu-id="43180-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43180-107">Remarks</span></span>

<span data-ttu-id="43180-108">XAML'deki iki olası değeri içeren öznitelik `xml:space` tanımı, `xml:space` XML için W3C belirtimleri tarafından "özel öznitelik" olarak tanımlanan tanımdan türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="43180-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>

<span data-ttu-id="43180-109">Özniteliğin `xml:space` varsayılan değeri gerçek değerdir. `"default"`</span><span class="sxs-lookup"><span data-stu-id="43180-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="43180-110">Değer `"default"`için, ya `xml:space` da hiç belirtilmediyse, önemli beyaz boşluk ayrıştırma davranışı, [XAML'de](white-space-processing.md)beyaz alan işleme konusunda tanımlandığı gibi varsayılan işlemedir.</span><span class="sxs-lookup"><span data-stu-id="43180-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](white-space-processing.md).</span></span>

<span data-ttu-id="43180-111">Nesne öğesi içeriğiiçindeki beyaz alanı `xml:space="preserve"` korumak için, bu nesne öğesi üzerinde belirtin.</span><span class="sxs-lookup"><span data-stu-id="43180-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>

<span data-ttu-id="43180-112">Çoğu yorumda, `xml:space` öznitelik efektleri ve öznitelik değeri alt öğelere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="43180-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>

<span data-ttu-id="43180-113">XAML'de beyaz alan işleme nin tam bir tartışması için, [XAML'deki Beyaz alan işleme bölümüne](white-space-processing.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="43180-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](white-space-processing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43180-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43180-114">See also</span></span>

- [<span data-ttu-id="43180-115">XAML'de Boşluk İşleme</span><span class="sxs-lookup"><span data-stu-id="43180-115">White-space processing in XAML</span></span>](white-space-processing.md)
- [<span data-ttu-id="43180-116">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="43180-116">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
