---
title: "&#39; &lt;classname&gt;&#39; CLS uyumlu olmadığından arabirimi &#39;&lt; InterfaceName&gt;&#39; uygular, CLS uyumlu değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords: BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7bad6aa4c8fa9979824766e83aba75697d6e98d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a>&#39; &lt;classname&gt;&#39; CLS uyumlu olmadığından arabirimi &#39;&lt; InterfaceName&gt;&#39; uygular, CLS uyumlu değil
Bir sınıf veya arabirim olarak işaretlenmiş `<CLSCompliant(True)>` zaman türetilen veya olarak işaretlenmiş bir tür uygular `<CLSCompliant(False)>` veya değil olarak işaretlenmiş.  
  
 Bir sınıf veya uyumlu olması için arabirimi için [dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/12a7a7h3) (CLS) tüm Devralma Hiyerarşisi olmalıdır uyumlu. Her tür devraldığı, doğrudan veya dolaylı olarak, uyumlu olması gerektiği anlamına gelir. Bir sınıf bir veya daha fazla arabirimlerini uygular, benzer şekilde, tüm kullanıcıların devralma hiyerarşileri uyumlu olmaları gerekir.  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40029  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   CLS uyumluluğu gerektiriyorsa, farklı bir devralma hiyerarşisi veya uygulama düzeni içinde bu tür tanımlayın.  
  
-   Bu tür, geçerli Devralma Hiyerarşisi veya uygulama düzeni içinde kalmasını gerekiyorsa kaldırma <xref:System.CLSCompliantAttribute> kendi tanımındaki veya olarak işaretlemek `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<PAVE üzerinden > CLS uyumlu kod yazma](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
