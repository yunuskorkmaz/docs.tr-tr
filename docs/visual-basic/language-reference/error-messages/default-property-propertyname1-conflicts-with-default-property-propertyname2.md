---
description: "Hakkında daha fazla bilgi edinin: BC40007: ' ' varsayılan özelliği ' ' <propertyname1> içinde ' ' varsayılan özelliği ile çakışıyor <propertyname2> ve bu nedenle, <classname> ' Shadows ' olarak bildirilmelidir"
title: "'<propertyname1>' varsayılan özelliği, '<propertyname2>' içindeki '<classname>' varsayılan özelliğiyle çakıştığından, 'Shadows' olarak bildirilmemelidir"
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 8ec7e36da18bbf8dda35e1a521d64268d14b7b26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796645"
---
# <a name="bc40007-default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>BC40007: ' ' varsayılan özelliği, \<propertyname1> ' ' içindeki ' ' varsayılan özelliğiyle çakışıyor \<propertyname2> ve bu \<classname> nedenle ' Shadows ' olarak bildirilmelidir

Bir özellik, temel sınıfta tanımlanan bir özellik ile aynı adla bildirilmiştir. Bu durumda, bu sınıftaki özelliğin temel sınıf özelliğini gölgelemelidir.

 Bu ileti bir uyarıdır. `Shadows` Varsayılan olarak varsayılır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **Hata kimliği:** BC40007

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- `Shadows`Bildirime anahtar sözcüğü ekleyin veya belirtilen özelliğin adını değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Shadows](../modifiers/shadows.md)
- [Visual Basic'de Gölgeleme](../../programming-guide/language-features/declared-elements/shadowing.md)
