---
title: Protected Friend
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 202d4f4a3a05a64ab1d74621268f28f6b55e8952
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404842"
---
# <a name="protected-friend-visual-basic"></a>Korumalı arkadaş (Visual Basic)

`Protected Friend`Anahtar sözcük birleşimi bir üye erişim değiştiricisidir. Hem [arkadaş](friend.md) erişimi hem de tanımlı öğeler üzerinde [korumalı](protected.md) erişimi, bu nedenle aynı derlemede, kendi sınıflarından ve türetilmiş sınıflardan erişilebilen her yerde erişilebilir hale gelir. `Protected Friend`Yalnızca sınıfların üyelerinde belirtebilirsiniz; `Protected Friend` yapılar devralınamadığı için bir yapının üyelerine uygulayamazsınız.

> [!NOTE]
> Visual Studio 'da F1 Yardımı ' nı seçmek, `protected friend` [korumalı](protected.md) veya [arkadaş](friend.md)için yardım sağlar. IDE, bileşik sözcük yerine imleç altında tek belirteci seçer.

## <a name="rules"></a>Kurallar

**Bildirim bağlamı.** `Protected Friend`Yalnızca sınıf düzeyinde kullanabilirsiniz. Yani bir öğe için bildirim bağlamı `Protected` bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Geneldir](public.md)
- [Korunamadı](protected.md)
- [Dost](friend.md)
- [Özelleştirme](private.md)
- [Özel korumalı](./private-protected.md)
- [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../programming-guide/language-features/procedures/index.md)
- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
