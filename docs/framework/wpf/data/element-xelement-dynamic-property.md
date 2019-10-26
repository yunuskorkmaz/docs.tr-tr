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
# <a name="element-xelement-dynamic-property"></a>Öğe (XElement dinamik özelliği)

Belirtilen genişletilmiş ada karşılık gelen alt öğe örneğini almak için kullanılan bir dizin oluşturucuyu alır.

## <a name="syntax"></a>Sözdizimi

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri

`XElement Item(String expandedName)`türünde bir Dizin Oluşturucu. Bu dizin oluşturucu genişletilmiş bir ad parametresi alır ve karşılık gelen <xref:System.Xml.Linq.XElement> döndürür veya belirtilen ada sahip hiçbir öğe yoksa `null`.

## <a name="remarks"></a>Açıklamalar

Bu özellik <xref:System.Xml.Linq.XContainer?displayProperty=fullName> sınıfının <xref:System.Xml.Linq.XContainer.Element%2A> metoduna eşdeğerdir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [XElement sınıfı dinamik özellikleri](attribute-xelement-dynamic-property.md)
- [Elements](elements-xelement-dynamic-property.md)
