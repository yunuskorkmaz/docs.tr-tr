---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: a5e9161132ba6d571daa30ce82e1bfb1dd2b064f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Bir veya daha fazla bildirilen programlama öğeleri hiçbir erişim kısıtlaması olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bileşeni ya da bir sınıf kitaplığı gibi bir bileşen kümesi yayımlıyorsanız programlama öğeleri ile derlemenizi çalıştığı herhangi bir kod tarafından erişilebilir olması için genellikle istiyor. Bu tür bir öğe üzerinde sınırsız erişimi confer için ile bildirebilir `Public`.  
  
 Genel erişim bir programlama öğesi için normal düzeyi olduğunda erişimi sınırlamak gerekmez. Erişim düzeyi, bir öğenin bir arabirim, modülü, sınıf veya yapı içinde bildirilen Not Varsayılan olarak `Public` , aksi takdirde değil bildirirseniz.  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `Public` yalnızca düzeyinde modül, arabirim veya ad alanı. Bu bildirimi bağlamının anlamına gelir bir `Public` öğesi bir kaynak dosya, ad alanı, arabirimi, modülü, sınıf veya yapı olmalıdır ve bir yordam olamaz.  
  
## <a name="behavior"></a>Davranış  
  
-   **Erişim düzeyi.** Bir modül, sınıf veya yapı erişebilen tüm kod erişmek için kendi `Public` öğeleri.  
  
-   **Varsayılan erişim.** Yerel değişkenler bir yordam varsayılan genel erişim ve içindeki tüm erişim değiştiricileri üzerlerinde kullanamazsınız.  
  
-   **Erişim değiştiricileri.** Erişim düzeyi belirtin anahtar sözcükleri adlı *erişim değiştiricileri*. Erişim değiştiricileri karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Public` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum Deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Özel korumalı](private-protected.md)   
 [Korumalı Friend](protected-friend.md)   
 [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
