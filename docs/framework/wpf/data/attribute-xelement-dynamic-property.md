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
# <a name="attribute-xelement-dynamic-property"></a>Öznitelik (XElement dinamik özelliği)

Belirtilen genişletilmiş ada karşılık gelen öznitelik örneğini almak için kullanılan bir dizin oluşturucuyu alır.

## <a name="syntax"></a>Sözdizimi

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri

`XAttribute Item(String expandedName)`türünde bir Dizin Oluşturucu. Bu Dizin Oluşturucu belirtilen özniteliğin genişletilmiş adını alır ve karşılık gelen <xref:System.Xml.Linq.XAttribute> döndürür ya da belirtilen ada sahip bir öznitelik yoksa `null`.

## <a name="remarks"></a>Açıklamalar

Bu özellik <xref:System.Xml.Linq.XElement?displayProperty=fullName> sınıfının <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemi ile eşdeğerdir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [XElement Sınıfı Dinamik Özellikleri](attribute-xelement-dynamic-property.md)
- [Değer](value-xattribute-dynamic-property.md)
