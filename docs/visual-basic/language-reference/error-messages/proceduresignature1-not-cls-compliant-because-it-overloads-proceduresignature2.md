---
title: "&lt;proceduresignature1&gt; CLS uyumlu değil çünkü &lt;proceduresignature2&gt; farklı ondan yalnızca dizi parametre türleri dizisi veya dizi parametre türleri derecesini tarafından"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords: BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa9fca7f0590846f60577787aa476539a2c872a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>&lt;proceduresignature1&gt; CLS uyumlu değil çünkü &lt;proceduresignature2&gt; farklı ondan yalnızca dizi parametre türleri dizisi veya dizi parametre türleri derecesini tarafından
Bir yordam veya özellik olarak işaretlenmiş `<CLSCompliant(True)>` zaman başka bir yordam veya özelliğini geçersiz kılar ve bunların parametre listeleri arasındaki tek fark basit bir dizi iç içe geçirme düzeyi veya bir dizi derecesini.  
  
 Aşağıdaki bildirimler, ikinci ve üçüncü bildirimleri bu hata oluştur.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 İkinci bildirim özgün tek boyutlu parametresi değişiklikleri `arrayParam` oluşan bir dizi için. Üçüncü bildirimi değişiklikleri `arrayParam` iki boyutlu bir diziye (derece 2). Visual Basic bu değişiklikler yalnızca biri tarafından farklı aşırı sağlar, ancak bu tür aşırı yüklemesi ile uyumlu değil [dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/12a7a7h3) (CLS).  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40035  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   CLS uyumluluğu gerektiriyorsa, aşırı birbirlerinden yalnızca bu Yardım sayfasında Alıntı yapılan değişiklikler dışındaki yöntemlerle de farklı tanımlayın.  
  
-   Aşırı farklı olduğunu gerekiyorsa yalnızca bu Yardım Alıntı yapılan değişikliklerden sayfasında, kaldırma <xref:System.CLSCompliantAttribute> tanımlarını gelen veya bunları olarak işaretlemek `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<PAVE üzerinden > CLS uyumlu kod yazma](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)  
 [Yordam aşırı yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [Aşırı yüklemeler](../../../visual-basic/language-reference/modifiers/overloads.md)
