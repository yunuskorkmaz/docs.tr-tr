---
title: Öğe (XElement dinamik özelliği)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.openlocfilehash: fc0277d0dc38574696f01e6915e5382744345771
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920897"
---
# <a name="element-xelement-dynamic-property"></a><span data-ttu-id="b070a-102">Öğe (XElement dinamik özelliği)</span><span class="sxs-lookup"><span data-stu-id="b070a-102">Element (XElement dynamic property)</span></span>

<span data-ttu-id="b070a-103">Belirtilen genişletilmiş ada karşılık gelen alt öğe örneğini almak için kullanılan bir dizin oluşturucuyu alır.</span><span class="sxs-lookup"><span data-stu-id="b070a-103">Gets an indexer used to retrieve the child element instance that corresponds to the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="b070a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b070a-104">Syntax</span></span>

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="b070a-105">Özellik değeri/dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b070a-105">Property value/return value</span></span>

<span data-ttu-id="b070a-106">`XElement Item(String expandedName)`türünde bir Dizin Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="b070a-106">An indexer of the type `XElement Item(String expandedName)`.</span></span> <span data-ttu-id="b070a-107">Bu dizin oluşturucu genişletilmiş bir ad parametresi alır ve karşılık gelen <xref:System.Xml.Linq.XElement> döndürür veya belirtilen ada sahip hiçbir öğe yoksa `null`.</span><span class="sxs-lookup"><span data-stu-id="b070a-107">This indexer takes an expanded name parameter and returns the corresponding <xref:System.Xml.Linq.XElement>, or `null` if there is no element with the specified name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b070a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b070a-108">Remarks</span></span>

<span data-ttu-id="b070a-109">Bu özellik <xref:System.Xml.Linq.XContainer?displayProperty=fullName> sınıfının <xref:System.Xml.Linq.XContainer.Element%2A> metoduna eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b070a-109">This property is equivalent to <xref:System.Xml.Linq.XContainer.Element%2A> method of the <xref:System.Xml.Linq.XContainer?displayProperty=fullName> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b070a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b070a-110">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [<span data-ttu-id="b070a-111">XElement sınıfı dinamik özellikleri</span><span class="sxs-lookup"><span data-stu-id="b070a-111">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="b070a-112">Elements</span><span class="sxs-lookup"><span data-stu-id="b070a-112">Elements</span></span>](elements-xelement-dynamic-property.md)
