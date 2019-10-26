---
title: Öznitelik (XElement dinamik özelliği)
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 2b645575a5b6876ffbb52a999c4e05a2de037493
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920918"
---
# <a name="attribute-xelement-dynamic-property"></a><span data-ttu-id="cc314-102">Öznitelik (XElement dinamik özelliği)</span><span class="sxs-lookup"><span data-stu-id="cc314-102">Attribute (XElement dynamic property)</span></span>

<span data-ttu-id="cc314-103">Belirtilen genişletilmiş ada karşılık gelen öznitelik örneğini almak için kullanılan bir dizin oluşturucuyu alır.</span><span class="sxs-lookup"><span data-stu-id="cc314-103">Gets an indexer used to retrieve the attribute instance that corresponds to the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="cc314-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc314-104">Syntax</span></span>

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="cc314-105">Özellik değeri/dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="cc314-105">Property value/return value</span></span>

<span data-ttu-id="cc314-106">`XAttribute Item(String expandedName)`türünde bir Dizin Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="cc314-106">An indexer of the type `XAttribute Item(String expandedName)`.</span></span> <span data-ttu-id="cc314-107">Bu Dizin Oluşturucu belirtilen özniteliğin genişletilmiş adını alır ve karşılık gelen <xref:System.Xml.Linq.XAttribute> döndürür ya da belirtilen ada sahip bir öznitelik yoksa `null`.</span><span class="sxs-lookup"><span data-stu-id="cc314-107">This indexer takes the expanded name of the specified attribute and returns the corresponding <xref:System.Xml.Linq.XAttribute>, or `null` if there is no attribute with the specified name.</span></span>

## <a name="remarks"></a><span data-ttu-id="cc314-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc314-108">Remarks</span></span>

<span data-ttu-id="cc314-109">Bu özellik <xref:System.Xml.Linq.XElement?displayProperty=fullName> sınıfının <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemi ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="cc314-109">This property is equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement?displayProperty=fullName> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc314-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc314-110">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [<span data-ttu-id="cc314-111">XElement Sınıfı Dinamik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="cc314-111">XElement Class Dynamic Properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="cc314-112">Değer</span><span class="sxs-lookup"><span data-stu-id="cc314-112">Value</span></span>](value-xattribute-dynamic-property.md)
