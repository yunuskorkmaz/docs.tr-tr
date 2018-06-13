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
ms.openlocfilehash: 3fae1a4b587c379dbc459cbc973982851e713785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600759"
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
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değiştiriciler](../../../visual-basic/language-reference/modifiers/index.md)  
 [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
