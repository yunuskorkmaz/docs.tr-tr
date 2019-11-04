---
title: XAML'de xml:space İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458798"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="4902c-102">XAML'de xml:space İşleme</span><span class="sxs-lookup"><span data-stu-id="4902c-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="4902c-103">`xml:space` özniteliği bir nesne öğesi içinde önemli beyaz boşluk işleme davranışını bildiren XML tanımlı bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="4902c-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="4902c-104">Bu davranış, `xml:space` bildirildiği öğede bulunan tüm içerik (iç metin) ve ayrıca alt öğe kapsamları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4902c-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="4902c-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4902c-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="4902c-106">\- veya-</span><span class="sxs-lookup"><span data-stu-id="4902c-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="4902c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4902c-107">Remarks</span></span>  
 <span data-ttu-id="4902c-108">XAML 'de iki olası değeri de dahil olmak üzere `xml:space` özniteliğinin tanımı, XML için W3C belirtimleri tarafından bir "özel öznitelik" olarak tanımlanan `xml:space` türetilir.</span><span class="sxs-lookup"><span data-stu-id="4902c-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="4902c-109">`xml:space` özniteliğin varsayılan değeri, `"default"`değişmez değer değeridir.</span><span class="sxs-lookup"><span data-stu-id="4902c-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="4902c-110">`"default"`değer için ya da `xml:space` hiç belirtilmemişse, önemli boşluk ayrıştırması davranışı [xaml 'Deki beyaz boşluk işleme](whitespace-processing-in-xaml.md)konusunda tanımlandığı şekilde varsayılan işleme olur.</span><span class="sxs-lookup"><span data-stu-id="4902c-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="4902c-111">Nesne öğesi içeriği içinde boşluk korumak için, bu nesne öğesinde `xml:space="preserve"` belirtin.</span><span class="sxs-lookup"><span data-stu-id="4902c-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="4902c-112">En çok yorumlamalar altında, `xml:space` öznitelik etkileri ve özniteliğin değeri alt öğelerin kapsamına alınır.</span><span class="sxs-lookup"><span data-stu-id="4902c-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="4902c-113">XAML 'de beyaz alan işleme hakkında tam bir açıklama için bkz. [xaml 'de beyaz boşluk işleme](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="4902c-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4902c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4902c-114">See also</span></span>

- [<span data-ttu-id="4902c-115">XAML 'de boşluk işleme</span><span class="sxs-lookup"><span data-stu-id="4902c-115">White-space processing in XAML</span></span>](whitespace-processing-in-xaml.md)
- [<span data-ttu-id="4902c-116">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="4902c-116">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
