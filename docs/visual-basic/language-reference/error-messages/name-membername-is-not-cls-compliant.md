---
title: "Ad &lt;membername&gt; CLS uyumlu değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords: BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba0dda520e37b27f9b7ad3c214508ee370162598
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a>Ad &lt;membername&gt; CLS uyumlu değil
Bir derlemeyi olarak işaretlenmiş `<CLSCompliant(True)>` ancak bir alt çizgi ile başlayan bir ada sahip bir üye gösterir (`_`).  
  
 Bir programlama öğesi ile uyumlu olmak ancak bir veya daha fazla alt çizgi, içerebilir [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), alt çizgi ile değil başlamalı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40031  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kaynak kodu denetim varsa, üye adı alt çizgi ile başlamıyor şekilde değiştirin.  
  
-   Üye adı değişmeden gerekiyorsa kaldırma <xref:System.CLSCompliantAttribute> kendi tanımındaki veya olarak işaretlemek `<CLSCompliant(False)>`. Derleme olarak hala işaretleyebilirsiniz `<CLSCompliant(True)>`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bildirilen Öğe Adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  

