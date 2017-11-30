---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a2f7bdba4b01bd307e0c52802509669f772b5eb5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Bir özellik veya yordam bu sınıfta uygulanmadı ve kullanılabilmesi için türetilen bir sınıfta geçersiz kılınmalıdır belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `MustOverride` yalnızca bir özellik veya yordam bildirimi deyimi içinde. Özellik veya belirtir yordamı `MustOverride` bir sınıf üyesi olması gerekir ve sınıf işaretlenmelidir [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Tamamlanmamış bildirimi.** Belirttiğinizde `MustOverride`, özellik veya yordam, kodun ek satırları değil sağlamazsanız bile `End Function`, `End Property`, veya `End Sub` deyimi.  
  
-   **Birleşik değiştirici.** Belirtemeyeceğiniz `MustOverride` ile birlikte `NotOverridable`, `Overridable`, veya `Shared` aynı bildirimi.  
  
-   **Gölgeleme ve geçersiz kılma.** Hem gölgeleme ve geçersiz kılma devralınan bir öğeyi yeniden tanımlamanız, ancak iki yaklaşım arasında önemli farklılıklar vardır. Daha fazla bilgi için bkz: [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
-   **Diğer koşulları.** Geçersiz kılma dışında kullanılamaz bir öğe adlandırılan bir *saf sanal* öğesi.  
  
 `MustOverride` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Geçersiz kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Geçersiz kılmaları](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
