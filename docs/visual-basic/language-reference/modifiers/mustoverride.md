---
title: MustOverride
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
ms.openlocfilehash: dc6a153a604fd0e5cee9d7d46ebcd63294f33628
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351493"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Bir özellik veya yordamın bu sınıfta uygulanmadığını ve kullanılmadan önce türetilmiş bir sınıfta geçersiz kılınmasının gerektiğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca bir özellik veya yordam bildirimi ifadesinde `MustOverride` kullanabilirsiniz. `MustOverride` belirten özellik veya yordam, bir sınıfın üyesi olmalıdır ve sınıfı [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)olarak işaretlenmiş olmalıdır.  
  
## <a name="rules"></a>Kurallar  
  
- **Tamamlanmamış bildirim.** `MustOverride`belirttiğinizde, özellik veya yordam için `End Function`, `End Property`veya `End Sub` deyimde değil, ek kod satırı sağlayamazsınız.  
  
- **Birleşik değiştiriciler.** Aynı bildirimde `NotOverridable`, `Overridable`veya `Shared` birlikte `MustOverride` belirtemezsiniz.  
  
- **Gölgeleme ve geçersiz kılma.** Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır. Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.  
  
- **Alternatif terimler.** Bir geçersiz kılma haricinde kullanılamayan bir öğe bazen *saf sanal* öğe olarak adlandırılır.  
  
 `MustOverride` değiştiricisi şu bağlamlarda kullanılabilir:  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
