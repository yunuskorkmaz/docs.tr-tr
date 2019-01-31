---
title: <membername> adı CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 74b625cc3a60e591417530c6a6229c01666038e2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271258"
---
# <a name="name-membername-is-not-cls-compliant"></a>Adı \<membername > CLS uyumlu değil
Bir derleme olarak işaretlenmiş `<CLSCompliant(True)>` ancak bir alt çizgi ile başlayan bir ada sahip bir üye sunar (`_`).  
  
 Bir programlama öğesi ile uyumlu olmak ancak bir veya daha fazla alt çizgi içerebilir [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) bir alt çizgiyle değil başlamalı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesine özniteliğin ayarladığınız `isCompliant` ya da parametre `True` veya `False` uyumluluk veya uyumsuzluk belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe için uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40031  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Denetime kaynak kodu varsa, alt çizgi ile başlamıyor şekilde üye adıyla değiştirin.  
  
-   Üye adı değişmeden kalmasını gerektiriyorsa, kaldırma <xref:System.CLSCompliantAttribute> kendi tanımından veya olarak işaretlemek `<CLSCompliant(False)>`. Yine de derleme olarak işaretleyebilirsiniz `<CLSCompliant(True)>`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bildirilen Öğe Adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)

