---
title: Alt Öğeler (XElement dinamik özelliği)
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 8d14b0a94d1a2028a56f649a574f157264ba50fa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920890"
---
# <a name="descendants-xelement-dynamic-property"></a>Alt Öğeler (XElement dinamik özelliği)

Belirtilen genişletilmiş adla eşleşen geçerli öğenin tüm alt öğelerini almak için kullanılan bir dizin oluşturucuyu alır.

## <a name="syntax"></a>Sözdizimi

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri

`IEnumerable<XElement> Item(String expandedName)`türünde bir Dizin Oluşturucu. Bu Dizin Oluşturucu belirtilen alt öğelerin genişletilmiş adını alır ve bir <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` koleksiyonundaki eşleşen alt öğeleri döndürür.

## <a name="remarks"></a>Açıklamalar

Bu özellik <xref:System.Xml.Linq.XContainer> sınıfının <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> yöntemi ile eşdeğerdir.

Döndürülen koleksiyondaki öğeler XML kaynak belgesi sıratümcesinde.

Bu özellik ertelenmiş yürütmeyi kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [XElement sınıfı dinamik özellikleri](attribute-xelement-dynamic-property.md)
- [Elements](elements-xelement-dynamic-property.md)
