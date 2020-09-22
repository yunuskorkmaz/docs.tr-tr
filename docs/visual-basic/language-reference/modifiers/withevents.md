---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: c2dcb044d04099c51f57d82a8bc08f0932bf3542
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875420"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)

Bir veya daha fazla tanımlanmış üye değişkeninin, olayları tetiklebilecek bir sınıfın örneğine başvurmayacağını belirtir.

## <a name="remarks"></a>Açıklamalar

Bir değişken kullanılarak tanımlandığında `WithEvents` , bir yöntemin anahtar sözcüğünü kullanarak değişkenin olaylarını işlediğini bildirimli olarak belirtebilirsiniz `Handles` .

`WithEvents`Yalnızca sınıf veya modül düzeyinde kullanabilirsiniz. Diğer bir deyişle, bir değişken için bildirim bağlamı `WithEvents` bir sınıf veya modül olmalıdır ve kaynak dosya, ad alanı, yapı veya yordam olamaz.

`WithEvents`Yapı üyesi üzerinde kullanamazsınız.

İle yalnızca bağımsız değişkenleri (diziler değil) bildirebilirsiniz `WithEvents` .

## <a name="rules"></a>Kurallar

**Öğe türleri.** `WithEvents`Değişkenleri, sınıf örneklerini kabul edebilecek şekilde nesne değişkenleri olacak şekilde bildirmeniz gerekir. Ancak, bunları olarak bildiremezsiniz `Object` . Bunları, olayları yükseltebilen belirli bir sınıf olarak bildirmeniz gerekir.

`WithEvents`Değiştirici Bu bağlamda kullanılabilir: [Dim ekstresi](../statements/dim-statement.md)

## <a name="example"></a>Örnek

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>Ayrıca bkz.

- [Handles](../statements/handles-clause.md)
- [Anahtar sözcükler](../keywords/index.md)
- [Ekinlikler](../../programming-guide/language-features/events/index.md)
