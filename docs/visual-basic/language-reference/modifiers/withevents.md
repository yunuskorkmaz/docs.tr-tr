---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 2309c675b50a2025d73841a47fe8e30e7cecd522
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350751"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Bir veya daha fazla tanımlanmış üye değişkeninin, olayları tetiklebilecek bir sınıfın örneğine başvurmayacağını belirtir.

## <a name="remarks"></a>Açıklamalar

Bir değişken `WithEvents`kullanılarak tanımlandığında, bir yöntemin, `Handles` anahtar sözcüğünü kullanarak değişkenin olaylarını işlediğini bildirimli olarak belirtebilirsiniz.

`WithEvents` yalnızca sınıf veya modül düzeyinde kullanabilirsiniz. Bu, bir `WithEvents` değişkeni için bildirim bağlamının bir sınıf veya modül olması ve kaynak dosya, ad alanı, yapı veya yordam olamayacağı anlamına gelir.

Yapı üyesi üzerinde `WithEvents` kullanamazsınız.

`WithEvents`ile yalnızca bağımsız değişkenleri (diziler değil) bildirebilirsiniz.

## <a name="rules"></a>Kurallar

**Öğe türleri.** Sınıf örneklerini kabul edebilmeleri için `WithEvents` değişkenlerini nesne değişkenleri olacak şekilde bildirmeniz gerekir. Ancak, bunları `Object`olarak bildiremezsiniz. Bunları, olayları yükseltebilen belirli bir sınıf olarak bildirmeniz gerekir.

`WithEvents` değiştiricisi Bu bağlamda kullanılabilir: [Dim ekstresi](../../../visual-basic/language-reference/statements/dim-statement.md)

## <a name="example"></a>Örnek

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>Ayrıca bkz.

- [İşlendiğini](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
