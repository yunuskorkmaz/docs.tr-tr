---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 50d5a768393e90d28d150b451405e35e6f4c7953
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583036"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Bir veya daha fazla tanımlanmış üye değişkeninin, olayları tetiklebilecek bir sınıfın örneğine başvurmayacağını belirtir.

## <a name="remarks"></a>Açıklamalar

Bir değişken `WithEvents` kullanılarak tanımlandığında, bir yöntemin, `Handles` anahtar sözcüğünü kullanarak değişkenin olaylarını işlediğini bildirimli olarak belirtebilirsiniz.

@No__t_0 yalnızca sınıf veya modül düzeyinde kullanabilirsiniz. Bu, bir `WithEvents` değişkeni için bildirim bağlamının bir sınıf veya modül olması ve kaynak dosya, ad alanı, yapı veya yordam olamayacağı anlamına gelir.

Yapı üyesi üzerinde `WithEvents` kullanamazsınız.

@No__t_0 ile yalnızca bağımsız değişkenleri (diziler değil) bildirebilirsiniz.

## <a name="rules"></a>Kurallar

**Öğe türleri.** Sınıf örneklerini kabul edebilmeleri için `WithEvents` değişkenlerini nesne değişkenleri olacak şekilde bildirmeniz gerekir. Ancak, bunları `Object` olarak bildiremezsiniz. Bunları, olayları yükseltebilen belirli bir sınıf olarak bildirmeniz gerekir.

@No__t_0 değiştiricisi Bu bağlamda kullanılabilir: [Dim ekstresi](../../../visual-basic/language-reference/statements/dim-statement.md)

## <a name="example"></a>Örnek

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>Ayrıca bkz.

- [İşlendiğini](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
