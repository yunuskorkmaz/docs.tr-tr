---
title: "Geçersiz Kılmalar (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1bee6a6235b87a7e20f087a73bef76e0fc7bf124
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Geçersiz kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Tür listesi](../../../visual-basic/language-reference/statements/type-list.md)
