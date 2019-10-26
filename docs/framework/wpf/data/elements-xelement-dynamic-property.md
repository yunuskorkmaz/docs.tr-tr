---
title: Öğeler (XElement dinamik özelliği)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.openlocfilehash: 812adabd3bfb01fd9313ce3f35e6cb0a5e23344e
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920855"
---
# <a name="elements-xelement-dynamic-property"></a><span data-ttu-id="0f2a4-102">Öğeler (XElement dinamik özelliği)</span><span class="sxs-lookup"><span data-stu-id="0f2a4-102">Elements (XElement dynamic property)</span></span>

<span data-ttu-id="0f2a4-103">Belirtilen genişletilmiş adla eşleşen geçerli öğenin alt öğelerini almak için kullanılan bir dizin oluşturucuyu alır.</span><span class="sxs-lookup"><span data-stu-id="0f2a4-103">Gets an indexer used to retrieve the child elements of the current element that match the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f2a4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f2a4-104">Syntax</span></span>

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="0f2a4-105">Özellik değeri/dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="0f2a4-105">Property value/return value</span></span>

<span data-ttu-id="0f2a4-106">`IEnumerable<XElement> Item(String expandedName)`türünde bir Dizin Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="0f2a4-106">An indexer of the type `IEnumerable<XElement> Item(String expandedName)`.</span></span> <span data-ttu-id="0f2a4-107">Bu Dizin Oluşturucu, istenen alt öğelerin genişletilmiş adını alır ve bir <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` koleksiyonundaki eşleşen alt öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f2a4-107">This indexer takes the expanded name of the desired child elements and returns the matching child elements in an <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f2a4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f2a4-108">Remarks</span></span>

<span data-ttu-id="0f2a4-109">Bu özellik <xref:System.Xml.Linq.XContainer> sınıfının <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> yöntemi ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0f2a4-109">This property is equivalent to the <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> method of the <xref:System.Xml.Linq.XContainer> class.</span></span>

<span data-ttu-id="0f2a4-110">Döndürülen koleksiyondaki öğeler XML kaynak belgesi sıratümcesinde.</span><span class="sxs-lookup"><span data-stu-id="0f2a4-110">The elements in the returned collection are in XML source document order.</span></span>

<span data-ttu-id="0f2a4-111">Bu özellik ertelenmiş yürütmeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f2a4-111">This property uses deferred execution.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f2a4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f2a4-112">See also</span></span>

- [<span data-ttu-id="0f2a4-113">XElement sınıfı dinamik özellikleri</span><span class="sxs-lookup"><span data-stu-id="0f2a4-113">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="0f2a4-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="0f2a4-114">Element</span></span>](element-xelement-dynamic-property.md)
- [<span data-ttu-id="0f2a4-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f2a4-115">Descendants</span></span>](descendants-xelement-dynamic-property.md)
