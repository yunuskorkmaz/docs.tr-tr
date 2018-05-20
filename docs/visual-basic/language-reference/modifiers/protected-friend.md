---
title: Korumalı Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: b72cbee0394043620e792d1c014bfe55121e175e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2018
---
# <a name="protected-friend-visual-basic"></a>Korumalı Friend (Visual Basic)

`Protected Friend` Anahtar sözcüğü birleşimi olan bir üye erişim değiştiricisi. Her ikisi de confers [arkadaş](friend.md) erişim ve [korumalı](protected.md) bildirilen öğelerde aynı bütünleştirilmiş kodda, kendi sınıfından ve türetilmiş sınıflarından herhangi bir yerindeki erişilebilir olduklarından erişim. Belirleyebileceğiniz `Protected Friend` yalnızca sınıfları; üyelerinde uygulayamazsınız `Protected Friend` bir yapı üyelerine yapıları devraldığından.

> [!NOTE]
> Visual Studio'da F1 Yardımı seçme `protected friend` ya da Yardım sağlar [korumalı](protected.md) veya [arkadaş](friend.md). IDE bileşik word yerine imleci altında tek belirteç seçer.

## <a name="rules"></a>Kurallar

- **Bildirim bağlamı.** Kullanabileceğiniz `Protected Friend` yalnızca sınıf düzeyinde. Bu bildirimi bağlamının anlamına gelir bir `Protected` öğesi bir sınıf olmalıdır ve bir kaynak dosyasını, ad alanı, arabirim, modülü, yapısı veya yordamı olamaz. 


## <a name="see-also"></a>Ayrıca Bkz.

[Public](../../../visual-basic/language-reference/modifiers/public.md)  
[Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
[Arkadaş](friend.md)   
[Private](../../../visual-basic/language-reference/modifiers/private.md)  
[Özel korumalı](./private-protected.md)   
[Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
