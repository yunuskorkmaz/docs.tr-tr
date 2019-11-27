---
title: Overridable
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 9c639665fd92a56de6fb6e5147cda873ef457b45
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351396"
---
# <a name="overridable-visual-basic"></a>Geçersiz Kılınabilir (Visual Basic)
Bir özellik veya yordamın, türetilmiş bir sınıftaki aynı adlı bir özellik veya yordam tarafından geçersiz kılınabileceğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `Overridable` değiştiricisi, bir sınıftaki özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasına izin verir. [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) değiştiricisi bir özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasını önler.  Daha fazla bilgi için bkz. [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 `Overridable` veya `NotOverridable` değiştiricisi belirtilmemişse, varsayılan ayar, özelliğin veya metodun bir temel sınıf özelliğini veya yöntemini geçersiz kıldığına bağlıdır. Özellik veya yöntem bir temel sınıf özelliğini veya yöntemini geçersiz kılıyorsa, varsayılan ayar `Overridable`; Aksi takdirde, `NotOverridable`.  
  
 Devralınan bir öğeyi yeniden tanımlamak için gölge veya geçersiz kılabilirsiniz, ancak iki yaklaşım arasında önemli farklılıklar vardır. Daha fazla bilgi için [Visual Basic 'Da gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)bölümüne bakın.  
  
 Geçersiz kılınabilen bir öğe bazen *sanal* öğe olarak adlandırılır. Geçersiz kılınırsa, ancak olması gerekmez, bazen *somut* öğe olarak da adlandırılır.  
  
 Yalnızca bir özellik veya yordam bildirimi ifadesinde `Overridable` kullanabilirsiniz.  
  
## <a name="combined-modifiers"></a>Birleşik değiştiriciler  
 `Private` yöntemi için `Overridable` veya `NotOverridable` belirtemezsiniz.  
  
 Aynı bildirimde `MustOverride`, `NotOverridable`veya `Shared` birlikte `Overridable` belirtemezsiniz.  
  
 Geçersiz kılan bir öğe örtük olarak geçersiz kılınabilir olduğundan, `Overrides``Overridable` birleştiremezsiniz.  
  
## <a name="usage"></a>Kullanım  
 `Overridable` değiştiricisi şu bağlamlarda kullanılabilir:  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değiştiriciler](../../../visual-basic/language-reference/modifiers/index.md)
- [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
