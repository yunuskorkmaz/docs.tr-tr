---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 0ddd7d0d2a57afc02aa7483ba5e83b65c48af534
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822823"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Bir özelliğin ya da yordamın bu sınıfta uygulanmadığını ve kullanmadan önce türetilmiş bir sınıfta geçersiz kılınması belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `MustOverride` yalnızca bir özellik veya yordamı bildirim deyiminde. Özellik veya yordamı belirten `MustOverride` bir sınıf üyesi olması gerekir ve sınıf işaretlenmelidir [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Tamamlanmamış bildirimi.** Belirttiğinizde `MustOverride`, özellik veya yordam, kodun ek satırları değil vermezsiniz bile `End Function`, `End Property`, veya `End Sub` deyimi.  
  
-   **Birleşik değiştiriciler.** Belirtemezsiniz `MustOverride` ile birlikte `NotOverridable`, `Overridable`, veya `Shared` aynı bildirimde.  
  
-   **Gölgeleme ve geçersiz kılma.** Devralınan bir öğe hem gölgeleme ve geçersiz kılma bulunabileceğini, ancak iki yaklaşım arasında önemli farklar vardır. Daha fazla bilgi için [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
-   **Diğer koşullar.** Dışında bir geçersiz kılma kullanılamaz bir öğe adlandırılan bir *saf sanal* öğesi.  
  
 `MustOverride` Bu bağlamda değiştirici kullanılabilir:  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
