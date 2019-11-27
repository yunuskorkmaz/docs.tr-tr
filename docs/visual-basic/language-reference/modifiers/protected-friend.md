---
title: Protected Friend
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: f92021f5f0dab9762470c270bdd5182187d587e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351317"
---
# <a name="protected-friend-visual-basic"></a>Korumalı arkadaş (Visual Basic)

`Protected Friend` anahtar sözcük birleşimi bir üye erişim değiştiricisidir. Hem [arkadaş](friend.md) erişimi hem de tanımlı öğeler üzerinde [korumalı](protected.md) erişimi, bu nedenle aynı derlemede, kendi sınıflarından ve türetilmiş sınıflardan erişilebilen her yerde erişilebilir hale gelir. Yalnızca sınıfların üyelerinde `Protected Friend` belirtebilirsiniz; yapılar devralınamadığı için `Protected Friend` bir yapının üyelerine uygulayamazsınız.

> [!NOTE]
> Visual Studio 'da F1 Yardımı ' nı seçmek `protected friend` [korumalı](protected.md) veya [arkadaş](friend.md)için yardım sağlar. IDE, bileşik sözcük yerine imleç altında tek belirteci seçer.

## <a name="rules"></a>Kurallar

**Bildirim bağlamı.** `Protected Friend` yalnızca sınıf düzeyinde kullanabilirsiniz. Yani, bir `Protected` öğesi için bildirim bağlamı bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.

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
