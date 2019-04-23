---
title: Korumalı arkadaş (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 331c63dc290d4096e8158f265ee869b47743a273
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151781"
---
# <a name="protected-friend-visual-basic"></a>Korumalı arkadaş (Visual Basic)

`Protected Friend` Anahtar sözcüğü bir üye erişim değiştiricisi oluşur. Her ikisi de confers [arkadaş](friend.md) erişim ve [korumalı](protected.md) kendi sınıf ve türetilen sınıflar aynı derlemenin başka bir yerindeki erişilebilir olduklarından bildirilmiş öğelere erişimi. Belirtebileceğiniz `Protected Friend` yalnızca; sınıfların üyeleri üzerinde uygulayamazsınız `Protected Friend` bir yapının üyelerine yapıları devraldığından.

> [!NOTE]
> Visual Studio'da F1 Yardımı seçme `protected friend` ya da Yardım sağlayan [korumalı](protected.md) veya [arkadaş](friend.md). IDE bileşik sözcüğü yerine imleç altında tek belirteç seçer.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** Kullanabileceğiniz `Protected Friend` yalnızca sınıf düzeyinde. Bildirim bağlamı başka bir deyişle bir `Protected` öğesi bir sınıf olması gerekir ve bir kaynak dosyası, ad alanı, arabirim, modülü, yapı veya yordamı olamaz. 

## <a name="see-also"></a>Ayrıca bkz.

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
