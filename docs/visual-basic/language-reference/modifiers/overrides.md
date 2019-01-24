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
ms.openlocfilehash: dbcd0625cdbcd06affc495ca29972c6c183c10f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582120"
---
# <a name="overrides-visual-basic"></a>Geçersiz Kılmalar (Visual Basic)
Bir özelliğin ya da yordamın bir aynı adlı bir özellik ya da bir temel sınıftan devralınan yordamın kıldığını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `Overrides` yalnızca bir özellik veya yordamı bildirim deyiminde.  
  
-   **Birleşik değiştiriciler.** Belirtemezsiniz `Overrides` ile birlikte `Shadows` veya `Shared` aynı bildirimde. Bir geçersiz kılma öğesi örtük olarak geçersiz kılınabilir olduğundan birleştiremezsiniz `Overridable` ile `Overrides`.  
  
-   **Eşleşen imzalar.** Bu bildirim imzası tam olarak eşleşmelidir *imza* özellik ya da onu geçersiz kılar yordamı. Başka bir deyişle, aynı sırayla, aynı veri türleriyle parametreleri aynı sayıda parametre listeleri olmalıdır.  
  
     İmza ek olarak, geçersiz kılma bildirimi de tam olarak şu eşleşmelidir:  
  
    -   Erişim düzeyi  
  
    -   Dönüş türü, varsa  
  
-   **Genel imzalar.** Genel bir yordam için imza türü parametre sayısını içerir. Bu nedenle, geçersiz kılma bildirimi de bu açısından temel sınıftaki sürümün eşleşmesi gerekir.  
  
-   **Ek eşleştirme.** Temel sınıftaki sürümün imzası eşleşen ek olarak, bu bildirimi Ayrıca, şu açılardan eşleşmesi gerekir:  
  
    -   Erişim düzeyi değiştirici (gibi [genel](../../../visual-basic/language-reference/modifiers/public.md))  
  
    -   Her parametre mekanizması geçirme ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))  
  
    -   Genel bir yordam üzerinde her tür parametresi kısıtlaması listeler  
  
-   **Gölgeleme ve geçersiz kılma.** Devralınan bir öğe hem gölgeleme ve geçersiz kılma bulunabileceğini, ancak iki yaklaşım arasında önemli farklar vardır. Daha fazla bilgi için [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Kullanırsanız `Overrides`, derleyicinin dolaylı olarak ekler `Overloads` kitaplığınızı API'leri ile çalışmak üzere C# daha kolay.  
  
 `Overrides` Bu bağlamda değiştirici kullanılabilir:  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)
