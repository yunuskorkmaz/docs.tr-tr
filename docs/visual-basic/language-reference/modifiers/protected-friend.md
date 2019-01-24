---
title: Korumalı arkadaş (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 1858411e5543448e6d822c97b6e5c18da4a6c11e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639607"
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
