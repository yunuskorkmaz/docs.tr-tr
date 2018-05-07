---
title: Özel (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: d7935cf691d961591ff5e3d2a290afb88de9165a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="private-visual-basic"></a>Özel (Visual Basic)
Bir veya daha fazla bildirilen programlama öğeleri dahil tüm kapsanan türleri içinde bildirim bağlamları içinde yalnızca erişilebilir olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir programlama öğesi özel işlevsellikten temsil eder veya gizli verileri içeriyorsa, genellikle mümkün olduğunca kesinlikle erişimi sınırlamak istiyorsunuz. En fazla kısıtlama, yalnızca modül, sınıf veya erişmek için tanımlayan yapısı sağlayarak elde edin. Bu şekilde bir öğeyi erişimi sınırlamak için ile bildirebilir `Private`.  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `Private` yalnızca modülü düzeyinde. Bu bildirimi bağlamının anlamına gelir bir `Private` öğesi bir modül, sınıf veya yapı olması ve kaynak dosyasını, ad alanı, arabirim veya yordam olamaz.  
  
## <a name="behavior"></a>Davranış  
  
-   **Erişim düzeyi.** Bildirimi bağlam içindeki tüm kodu erişmek için kendi `Private` öğeleri. Bu, iç içe bir sınıf veya numaralandırma atama deyimde gibi bir kapsanan türü içindeki kod içerir. Bildirimi bağlamı dışında hiçbir kod erişmek için kendi `Private` öğeleri.  
  
-   **Erişim değiştiricileri.** Erişim düzeyi belirtin anahtar sözcükleri adlı *erişim değiştiricileri*. Erişim değiştiricileri karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Private` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum Deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
