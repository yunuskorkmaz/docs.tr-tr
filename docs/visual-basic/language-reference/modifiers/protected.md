---
title: Korumalı (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 3866e7dd72b9e7145cf76f480bb5ffc6239a775e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="protected-visual-basic"></a>Korumalı (Visual Basic)
Bir veya daha fazla bildirilen programlama öğeleri erişilebilir yalnızca kendi sınıfı içinde veya türetilmiş bir sınıf olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bazen bir sınıfında tanımlanan bir programlama öğesi hassas verileri veya kısıtlı kod içeren ve öğe erişimi sınırlamak istiyorsunuz. Ancak, sınıf devralınabilir ise ve türetilen sınıflar hiyerarşisi beklediğiniz, onu bu türetilen sınıflar veri veya kod erişmek gerekli olabilir. Böyle bir durumda öğesi temel sınıfını hem türetilen tüm sınıflardan erişilebilir olmasını istiyorsunuz. Bu şekilde bir öğeyi erişimi sınırlamak için ile bildirebilir `Protected`.  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `Protected` yalnızca sınıf düzeyinde. Bu bildirimi bağlamının anlamına gelir bir `Protected` öğesi bir sınıf olmalıdır ve bir kaynak dosyasını, ad alanı, arabirim, modülü, yapısı veya yordamı olamaz.  
  
-   **Birleşik değiştirici.** Kullanabileceğiniz `Protected` değiştirici ile birlikte [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) aynı bildiriminde değiştiricisi. Bu birleşim bildirilen öğeler aynı bütünleştirilmiş kodda, kendi sınıfından ve türetilmiş sınıflarından herhangi bir yerindeki erişilebilir hale getirir. Belirleyebileceğiniz `Protected Friend` sınıfları üyeleri yalnızca üzerinde.  
  
## <a name="behavior"></a>Davranış  
  
-   **Erişim düzeyi.** Bir sınıftaki tüm kod öğeleri erişebilir. Bir taban sınıftan türetilen herhangi bir sınıf kodda tüm erişebilir `Protected` öğeleri temel sınıf. Bu türetme tüm nesli için geçerlidir. Bu sınıf erişebilmesini anlamına gelir `Protected` öğeleri temel sınıfın temel sınıf ve benzeri.  
  
     Korumalı Erişim, bir üst veya alt friend erişim değil.  
  
-   **Erişim değiştiricileri.** Erişim düzeyi belirtin anahtar sözcükleri adlı *erişim değiştiricileri*. Erişim değiştiricileri karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Protected` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
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
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
