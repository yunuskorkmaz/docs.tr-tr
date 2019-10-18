---
title: Korumalı arkadaş (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: d3592feaece1d5ce85ee6e2657d8a2715c4097a3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524780"
---
# <a name="protected-friend-visual-basic"></a>Korumalı arkadaş (Visual Basic)

@No__t_0 anahtar sözcük birleşimi bir üye erişim değiştiricisidir. Hem [arkadaş](friend.md) erişimi hem de tanımlı öğeler üzerinde [korumalı](protected.md) erişimi, bu nedenle aynı derlemede, kendi sınıflarından ve türetilmiş sınıflardan erişilebilen her yerde erişilebilir hale gelir. Yalnızca sınıfların üyelerinde `Protected Friend` belirtebilirsiniz; yapılar devralınamadığı için `Protected Friend` bir yapının üyelerine uygulayamazsınız.

> [!NOTE]
> Visual Studio 'da F1 Yardımı ' nı seçmek `protected friend` [korumalı](protected.md) veya [arkadaş](friend.md)için yardım sağlar. IDE, bileşik sözcük yerine imleç altında tek belirteci seçer.

## <a name="rules"></a>Kurallar

**Bildirim bağlamı.** @No__t_0 yalnızca sınıf düzeyinde kullanabilirsiniz. Yani, bir `Protected` öğesi için bildirim bağlamı bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
