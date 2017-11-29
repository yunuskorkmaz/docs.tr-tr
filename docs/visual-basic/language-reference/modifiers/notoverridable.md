---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6fc5fb006b36cda1b6ad0e128604bc3bb427fd94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Türetilen bir sınıfta bir özellik veya yordam kılınamaz belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `NotOverridable` Değiştiricisi engelleyen bir özellik veya yöntem türetilen bir sınıfta geçersiz kılındı.  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) türetilen bir sınıfta geçersiz kılınmak üzere bir sınıftaki değiştiricisi sağlayan bir özellik veya yöntem. Daha fazla bilgi için bkz: [devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Varsa `Overridable` veya `NotOverridable` değiştiricisi belirtilmezse, varsayılan ayar olup özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılmaları üzerinde bağlıdır. Özellik veya yöntem bir temel sınıf özelliği veya yöntemi geçersiz kılar, varsayılan ayardır `Overridable`; Aksi takdirde, bu `NotOverridable`.  
  
 Geçersiz kılınamaz bir öğe adlandırılan bir *korumalı* öğesi.  
  
 Kullanabileceğiniz `NotOverridable` yalnızca bir özellik veya yordam bildirimi deyimi içinde. Belirleyebileceğiniz `NotOverridable` yalnızca bir özellik veya başka bir özellik veya yordam, diğer bir deyişle, yalnızca birlikte içinde geçersiz kılmaları yordamı üzerinde `Overrides`.  
  
## <a name="combined-modifiers"></a>Birleşik değiştirici  
 Belirtemeyeceğiniz `Overridable` veya `NotOverridable` için bir `Private` yöntemi.  
  
 Belirtemeyeceğiniz `NotOverridable` ile birlikte `MustOverride`, `Overridable`, veya `Shared` aynı bildirimi.  
  
## <a name="usage"></a>Kullanım  
 `NotOverridable` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değiştiriciler](../../../visual-basic/language-reference/modifiers/index.md)  
 [Devralma temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [Geçersiz kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Geçersiz kılmaları](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
