---
title: NotOverridable (Visual Basic)
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
ms.openlocfilehash: d2495e9d44a32e080d20deb4232ab27bfbd4051a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595818"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Türetilen bir sınıfta bir özellik veya yordamı kılınamaz belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `NotOverridable` Değiştiricisi engelleyen bir özellik veya yöntem türetilmiş sınıf içinde geçersiz kılındı.  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) türetilen bir sınıfta geçersiz kılınacak sınıfında değiştiricisi sağlayan bir özellik veya yöntem. Daha fazla bilgi için [devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Varsa `Overridable` veya `NotOverridable` değiştiricisi belirtilmezse, varsayılan ayar olup özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılar üzerinde bağlıdır. Bir temel sınıf özelliği veya yöntemi özelliği veya yöntemi geçersiz kılar, varsayılan ayardır `Overridable`; Aksi takdirde bu `NotOverridable`.  
  
 Geçersiz kılınamaz öğenin adlandırılan bir *korumalı* öğesi.  
  
 Kullanabileceğiniz `NotOverridable` yalnızca bir özellik veya yordamı bildirim deyiminde. Belirtebileceğiniz `NotOverridable` yalnızca üzerinde bir özelliği ya da başka bir özellik ya da yordamın, diğer bir deyişle, yalnızca içinde birlikte geçersiz kılan yordamın `Overrides`.  
  
## <a name="combined-modifiers"></a>Birleşik değiştirici  
 Belirtemezsiniz `Overridable` veya `NotOverridable` için bir `Private` yöntemi.  
  
 Belirtemezsiniz `NotOverridable` ile birlikte `MustOverride`, `Overridable`, veya `Shared` aynı bildirimde.  
  
## <a name="usage"></a>Kullanım  
 `NotOverridable` Bu bağlamda değiştirici kullanılabilir:  
  
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
- [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
