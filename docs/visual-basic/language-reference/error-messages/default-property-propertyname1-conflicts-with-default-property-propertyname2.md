---
title: "'<propertyname1>' varsayılan özelliği, '<propertyname2>' içindeki '<classname>' varsayılan özelliğiyle çakıştığından, 'Shadows' olarak bildirilmemelidir"
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 290971a3173c59f08fbd279b6fffe3bcb618cb72
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160613"
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
