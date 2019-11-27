---
title: NotOverridable
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: c55d57bb3008b2825fe5382844908ea32f0d500c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351453"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Bir özelliğin veya yordamın türetilmiş bir sınıfta geçersiz kılınamayacağını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `NotOverridable` değiştiricisi, bir özelliğin veya metodun türetilmiş bir sınıfta geçersiz kılınmasını önler.  [Geçersiz kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md) değiştirici, bir sınıftaki özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasına izin verir. Daha fazla bilgi için bkz. [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 `Overridable` veya `NotOverridable` değiştiricisi belirtilmemişse, varsayılan ayar, özelliğin veya metodun bir temel sınıf özelliğini veya yöntemini geçersiz kıldığına bağlıdır. Özellik veya yöntem bir temel sınıf özelliğini veya yöntemini geçersiz kılıyorsa, varsayılan ayar `Overridable`; Aksi takdirde, `NotOverridable`.  
  
 Geçersiz kılınamayan bir öğe, bazen *Sealed* öğesi olarak adlandırılır.  
  
 Yalnızca bir özellik veya yordam bildirimi ifadesinde `NotOverridable` kullanabilirsiniz. Yalnızca bir özellik veya yordamı geçersiz kılan bir özellik veya yordamda yalnızca `Overrides`ile birlikte `NotOverridable` belirtebilirsiniz.  
  
## <a name="combined-modifiers"></a>Birleşik değiştiriciler  
 `Private` yöntemi için `Overridable` veya `NotOverridable` belirtemezsiniz.  
  
 Aynı bildirimde `MustOverride`, `Overridable`veya `Shared` birlikte `NotOverridable` belirtemezsiniz.  
  
## <a name="usage"></a>Kullanım  
 `NotOverridable` değiştiricisi şu bağlamlarda kullanılabilir:  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değiştiriciler](../../../visual-basic/language-reference/modifiers/index.md)
- [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
