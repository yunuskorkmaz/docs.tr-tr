---
title: Public (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6cd70adf6ec31c56f39d0443d320dd1b00b00d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Özel](../../../visual-basic/language-reference/modifiers/private.md)  
 [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Yordamları](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Yapıları](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
