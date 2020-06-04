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
ms.openlocfilehash: 1b20108a2d42e82c0af7598fde8d60a08fea28ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396200"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Bir özellik veya yordamın bu sınıfta uygulanmadığını ve kullanılmadan önce türetilmiş bir sınıfta geçersiz kılınmasının gerektiğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `MustOverride`Yalnızca bir özellik veya yordam bildirimi ifadesinde kullanabilirsiniz. Belirten özellik veya yordam `MustOverride` bir sınıfın üyesi olmalıdır ve sınıfı [MustInherit](mustinherit.md)olarak işaretlenmiş olmalıdır.  
  
## <a name="rules"></a>Kurallar  
  
- **Tamamlanmamış bildirim.** Belirttiğinizde,, `MustOverride` `End Function` `End Property` veya deyimde değil, özellik veya yordam için ek kod satırı sağlayamazsınız `End Sub` .  
  
- **Birleşik değiştiriciler.** `MustOverride` `NotOverridable` Aynı bildirimde, veya ile birlikte belirtemezsiniz `Overridable` `Shared` .  
  
- **Gölgeleme ve geçersiz kılma.** Hem gölgeleme hem de geçersiz kılma devralınan bir öğeyi yeniden tanımlayın, ancak iki yaklaşım arasında önemli farklılıklar vardır. Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.  
  
- **Alternatif terimler.** Bir geçersiz kılma haricinde kullanılamayan bir öğe bazen *saf sanal* öğe olarak adlandırılır.  
  
 `MustOverride`Değiştirici şu bağlamlarda kullanılabilir:  
  
 [Function Deyimi](../statements/function-statement.md)  
  
 [Property Deyimi](../statements/property-statement.md)  
  
 [Sub Deyimi](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [NotOverridable](notoverridable.md)
- [Overridable](overridable.md)
- [Geçersiz Kılmalar](overrides.md)
- [MustInherit](mustinherit.md)
- [Anahtar sözcükler](../keywords/index.md)
- [Visual Basic'de Gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)
