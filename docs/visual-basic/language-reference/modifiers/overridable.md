---
title: "Geçersiz Kılınabilir (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f7d5dd33f8591be1b4305e954e55e035882626c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="overridable-visual-basic"></a>Geçersiz Kılınabilir (Visual Basic)
Aynı adlı bir özellik veya türetilmiş bir sınıf yordamda bir özellik veya yordam kılınabilir belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `Overridable` Türetilen bir sınıfta geçersiz kılınmak üzere bir sınıftaki değiştiricisi sağlayan bir özellik veya yöntem. [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) değiştiricisi engelleyen bir özellik veya yöntem türetilen bir sınıfta geçersiz kılındı.  Daha fazla bilgi için bkz: [devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Varsa `Overridable` veya `NotOverridable` değiştiricisi belirtilmezse, varsayılan ayar olup özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılmaları üzerinde bağlıdır. Özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılar, varsayılan ayardır `Overridable`; Aksi takdirde, bu `NotOverridable`.  
  
 Gölge veya devralınan bir öğeyi yeniden tanımlamak için geçersiz kılar, ancak iki yaklaşım arasında önemli farklılıklar vardır. Daha fazla bilgi için bkz: [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Geçersiz kılınabilir bir öğe, bazen olarak adlandırılır bir *sanal* öğesi. Geçersiz kılınabilir ancak olması gerekmez, bazen de denir bir *somut* öğesi.  
  
 Kullanabileceğiniz `Overridable` yalnızca bir özellik veya yordam bildirimi deyimi içinde.  
  
## <a name="combined-modifiers"></a>Birleşik değiştirici  
 Belirtemeyeceğiniz `Overridable` veya `NotOverridable` için bir `Private` yöntemi.  
  
 Belirtemeyeceğiniz `Overridable` ile birlikte `MustOverride`, `NotOverridable`, veya `Shared` aynı bildirimi.  
  
 Bir geçersiz kılma öğesi örtülü olarak geçersiz kılınabilir olduğundan birleştiremez `Overridable` ile `Overrides`.  
  
## <a name="usage"></a>Kullanım  
 `Overridable` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değiştiriciler](../../../visual-basic/language-reference/modifiers/index.md)  
 [Devralma temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Geçersiz kılmaları](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
