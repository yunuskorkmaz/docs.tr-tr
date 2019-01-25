---
title: Geçersiz Kılınabilir (Visual Basic)
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
ms.openlocfilehash: 7002589b303c41b26b611588f339fa70dd19f959
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537601"
---
# <a name="overridable-visual-basic"></a>Geçersiz Kılınabilir (Visual Basic)
Aynı adlı bir özellik ya da yordam türetilen bir sınıfta bir özellik veya yordamı kılınabileceğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `Overridable` Türetilen bir sınıfta geçersiz kılınacak sınıfında değiştiricisi sağlayan bir özellik veya yöntem. [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) değiştiricisi engelleyen bir özellik veya yöntem türetilmiş sınıf içinde geçersiz kılındı.  Daha fazla bilgi için [devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Varsa `Overridable` veya `NotOverridable` değiştiricisi belirtilmezse, varsayılan ayar olup özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılar üzerinde bağlıdır. Bir temel sınıf özelliği veya yöntemi özelliği veya yöntemi geçersiz kılar, varsayılan ayardır `Overridable`; Aksi takdirde bu `NotOverridable`.  
  
 Gölge veya devralınan bir öğeyi yeniden tanımlamak için geçersiz kılar, ancak iki yaklaşım arasında önemli farklar vardır. Daha fazla bilgi için [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Geçersiz kılınabilir bir öğe, bazen olarak adlandırılır bir *sanal* öğesi. Geçersiz kılınabilir ancak olması gerekmez, bazen de denir bir *somut* öğesi.  
  
 Kullanabileceğiniz `Overridable` yalnızca bir özellik veya yordamı bildirim deyiminde.  
  
## <a name="combined-modifiers"></a>Birleşik değiştirici  
 Belirtemezsiniz `Overridable` veya `NotOverridable` için bir `Private` yöntemi.  
  
 Belirtemezsiniz `Overridable` ile birlikte `MustOverride`, `NotOverridable`, veya `Shared` aynı bildirimde.  
  
 Bir geçersiz kılma öğesi örtük olarak geçersiz kılınabilir olduğundan birleştiremezsiniz `Overridable` ile `Overrides`.  
  
## <a name="usage"></a>Kullanım  
 `Overridable` Bu bağlamda değiştirici kullanılabilir:  
  
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
- [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
