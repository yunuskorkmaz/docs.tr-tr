---
title: Non-CLS ile uyumlu &lt;membername&gt; CLS uyumlu arabiriminde izin verilmiyor
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: ee533df5e06352034b24651b9173a88d090da0a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594152"
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a>Non-CLS ile uyumlu &lt;membername&gt; CLS uyumlu arabiriminde izin verilmiyor
Bir özellik, yordam veya olay arabirimdeki olarak işaretlenmiş `<CLSCompliant(True)>` zaman arabirimi olarak işaretli `<CLSCompliant(False)>` veya değil olarak işaretlenmiş.  
  
 Uyumlu olması bir arabirim için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), tüm üyeleri olmalıdır uyumlu.  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40033  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   CLS uyumluluğu gerektiriyorsa ve arabirim kaynak kodu üzerinde denetim sahibi yoksa arabirimi olarak işaretlemek `<CLSCompliant(True)>` tüm üyeleri uyumlu olması durumunda.  
  
-   CLS uyumluluğu gerektirir ve arabirim kaynak kodu üzerinde denetim sahibi değildir veya da uyumlu olması uygun değilse, bu üye içinde farklı bir arabirim tanımlayın.  
  
-   Bu üye, geçerli arabirimi içinde kalmasını gerekiyorsa kaldırma <xref:System.CLSCompliantAttribute> kendi tanımındaki veya olarak işaretlemek `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 
