---
title: "'<propertyname1>' varsayılan özelliği, '<propertyname2>' içindeki '<classname>' varsayılan özelliğiyle çakıştığından, 'Shadows' olarak bildirilmemelidir"
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: b857a9ae7875a156179602cbe77558333d07b7b9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874508"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>'\<propertyname1>' varsayılan özelliği, '\<propertyname2>' içindeki '\<classname>' varsayılan özelliğiyle çakıştığından, 'Shadows' olarak bildirilmemelidir

Bir özellik, temel sınıfta tanımlanan bir özellik ile aynı adla bildirilmiştir. Bu durumda, bu sınıftaki özelliğin temel sınıf özelliğini gölgelemelidir.  
  
 Bu ileti bir uyarıdır. `Shadows` Varsayılan olarak varsayılır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC40007  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `Shadows`Bildirime anahtar sözcüğü ekleyin veya belirtilen özelliğin adını değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shadows](../modifiers/shadows.md)
- [Visual Basic'de Gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)
