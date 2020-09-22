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
ms.openlocfilehash: 8eec54a12c7fb748df46e8c48a8b07eab983cc72
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867867"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)

Bir özelliğin veya yordamın türetilmiş bir sınıfta geçersiz kılınamayacağını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  

 `NotOverridable`Değiştirici bir özelliğin veya metodun türetilmiş bir sınıfta geçersiz kılınmasını önler.  [Geçersiz kılınabilir](overridable.md) değiştirici, bir sınıftaki özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasına izin verir. Daha fazla bilgi için bkz. [Devralma Temelleri](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 `Overridable`Veya `NotOverridable` değiştiricisi belirtilmemişse, varsayılan ayar, özelliğin veya metodun bir temel sınıf özelliğini veya yöntemini geçersiz kıldığına bağlıdır. Özellik veya yöntem bir temel sınıf özelliğini veya yöntemini geçersiz kılıyorsa, varsayılan ayar olur `Overridable` ; Aksi takdirde, olur `NotOverridable` .  
  
 Geçersiz kılınamayan bir öğe, bazen *Sealed* öğesi olarak adlandırılır.  
  
 `NotOverridable`Yalnızca bir özellik veya yordam bildirimi ifadesinde kullanabilirsiniz. Yalnızca bir özellik veya `NotOverridable` yordamı geçersiz kılan bir özellik ya da yordam üzerinde yalnızca ile birlikte bir özelliği belirtebilirsiniz `Overrides` .  
  
## <a name="combined-modifiers"></a>Birleşik değiştiriciler  

 `Overridable` `NotOverridable` Bir yöntem için veya belirtemezsiniz `Private` .  
  
 `NotOverridable` `MustOverride` Aynı bildirimde, veya ile birlikte belirtemezsiniz `Overridable` `Shared` .  
  
## <a name="usage"></a>Kullanım  

 `NotOverridable`Değiştirici şu bağlamlarda kullanılabilir:  
  
 [Function Deyimi](../statements/function-statement.md)  
  
 [Property Deyimi](../statements/property-statement.md)  
  
 [Sub Deyimi](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değiştiriciler](index.md)
- [Devralma Temelleri](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [Overridable](overridable.md)
- [Geçersiz Kılmalar](overrides.md)
- [Anahtar sözcükler](../keywords/index.md)
- [Visual Basic'de Gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)
