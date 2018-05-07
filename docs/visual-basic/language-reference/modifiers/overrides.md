---
title: Geçersiz Kılmalar (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 81118b9e97f320bffdbb58e5e1a2859052c4cee5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="overrides-visual-basic"></a>Geçersiz Kılmalar (Visual Basic)
Bir özellik veya yordam aynı adlı bir özellik ya da bir taban sınıftan devralınan yordamı kıldığını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `Overrides` yalnızca bir özellik veya yordam bildirimi deyimi içinde.  
  
-   **Birleşik değiştirici.** Belirtemeyeceğiniz `Overrides` ile birlikte `Shadows` veya `Shared` aynı bildirimi. Bir geçersiz kılma öğesi örtülü olarak geçersiz kılınabilir olduğundan birleştiremez `Overridable` ile `Overrides`.  
  
-   **Eşleşen imzalar.** Bu bildirim imzası tam olarak eşleşmelidir *imza* özelliği ya da bu geçersiz kılmaları yordamı. Başka bir deyişle, aynı veri türleriyle aynı sırada parametreleri aynı sayıda parametre listeleri olmalıdır.  
  
     İmza yanı sıra geçersiz kılma bildirimi de tam olarak aşağıdaki eşleşmesi gerekir:  
  
    -   Erişim düzeyi  
  
    -   Dönüş türü, varsa  
  
-   **Genel imzalar.** Genel bir yordam için imza türü parametre sayısını içerir. Bu nedenle, geçersiz kılma bildirimi de o açısından taban sınıf sürümle aynı olmalıdır.  
  
-   **Ek eşleşen.** Taban sınıfı sürüm imzası eşleştirmeye ek olarak, bu bildirim ayrıca, aşağıdaki yönden eşleşmesi gerekir:  
  
    -   Erişim düzeyi değiştiricisi (gibi [ortak](../../../visual-basic/language-reference/modifiers/public.md))  
  
    -   Her bir parametreyi mekanizması geçirme ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))  
  
    -   Her bir genel yordam tür parametresinin kısıtlaması listeler  
  
-   **Gölgeleme ve geçersiz kılma.** Hem gölgeleme ve geçersiz kılma devralınan bir öğeyi yeniden tanımlamanız, ancak iki yaklaşım arasında önemli farklılıklar vardır. Daha fazla bilgi için bkz: [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Kullanırsanız `Overrides`, derleyici örtük olarak ekler `Overloads` kitaplığınızın API'leri iş böylece C# ile daha kolay.  
  
 `Overrides` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)
