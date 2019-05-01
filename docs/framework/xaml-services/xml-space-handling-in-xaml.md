---
title: XAML'de xml:space İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: d15bab1ad9234959048fa7b7c3fa2bbbeca5fe6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938729"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="f0bf3-102">XAML'de xml:space İşleme</span><span class="sxs-lookup"><span data-stu-id="f0bf3-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="f0bf3-103">`xml:space` Özniteliği olan bir nesne öğesi içinde önemli boşluk işleme davranışını bildiren XML tanımlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f0bf3-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="f0bf3-104">Bu öğe içinde bulunan tüm içeriği (iç metni) ilgili, davranıştır burada `xml:space` bildirilmiş ve aynı zamanda kapsamları alt öğeleri için.</span><span class="sxs-lookup"><span data-stu-id="f0bf3-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="f0bf3-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="f0bf3-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="f0bf3-106">\- veya -</span><span class="sxs-lookup"><span data-stu-id="f0bf3-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="f0bf3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0bf3-107">Remarks</span></span>  
 <span data-ttu-id="f0bf3-108">Tanımı `xml:space` iki olası değerleri dahil olmak üzere XAML özniteliği türetilen `xml:space` "özel özniteliği" belirtimleri XML W3C tarafından tanımlandığı şekilde.</span><span class="sxs-lookup"><span data-stu-id="f0bf3-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="f0bf3-109">Varsayılan değer olan `xml:space` özniteliktir değişmez değer `"default"`.</span><span class="sxs-lookup"><span data-stu-id="f0bf3-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="f0bf3-110">Değeri için `"default"`, veya `xml:space` önemli boşluk ayrıştırma davranıştır varsayılan işleme konusundaki tanımlandığı şekilde, belirtilmemiş [boşluk XAML içinde işleme](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f0bf3-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="f0bf3-111">Boşluk nesne öğe içeriği içinde korumak için bu seçeneği belirtin `xml:space="preserve"` o nesne öğesi üzerinde.</span><span class="sxs-lookup"><span data-stu-id="f0bf3-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="f0bf3-112">Çoğu yorumlaması altında `xml:space` özniteliği etkiler ve öznitelik değeri için alt öğeleri kapsanır.</span><span class="sxs-lookup"><span data-stu-id="f0bf3-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="f0bf3-113">Boşluk işleme XAML içinde tam bir açıklaması için bkz: [boşluk XAML içinde işleme](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f0bf3-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0bf3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0bf3-114">See also</span></span>

- [<span data-ttu-id="f0bf3-115">Boşluk XAML içinde işleme</span><span class="sxs-lookup"><span data-stu-id="f0bf3-115">White-space processing in XAML</span></span>](whitespace-processing-in-xaml.md)
- [<span data-ttu-id="f0bf3-116">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="f0bf3-116">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
