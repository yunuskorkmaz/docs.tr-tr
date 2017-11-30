---
title: Non-CLS ile uyumlu &lt;membername&gt; CLS uyumlu arabiriminde izin verilmiyor
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords: BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 358abd338d3ce780c2f0aae7aa8efb53e57b477c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a>Non-CLS ile uyumlu &lt;membername&gt; CLS uyumlu arabiriminde izin verilmiyor
Bir özellik, yordam veya olay arabirimdeki olarak işaretlenmiş `<CLSCompliant(True)>` zaman arabirimi olarak işaretli `<CLSCompliant(False)>` veya değil olarak işaretlenmiş.  
  
 Uyumlu olması bir arabirim için [dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/12a7a7h3) (CLS), tüm üyeleri olmalıdır uyumlu.  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40033  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   CLS uyumluluğu gerektiriyorsa ve arabirim kaynak kodu üzerinde denetim sahibi yoksa arabirimi olarak işaretlemek `<CLSCompliant(True)>` tüm üyeleri uyumlu olması durumunda.  
  
-   CLS uyumluluğu gerektirir ve arabirim kaynak kodu üzerinde denetim sahibi değildir veya da uyumlu olması uygun değilse, bu üye içinde farklı bir arabirim tanımlayın.  
  
-   Bu üye, geçerli arabirimi içinde kalmasını gerekiyorsa kaldırma <xref:System.CLSCompliantAttribute> kendi tanımındaki veya olarak işaretlemek `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Interface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [\<PAVE üzerinden > CLS uyumlu kod yazma](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
