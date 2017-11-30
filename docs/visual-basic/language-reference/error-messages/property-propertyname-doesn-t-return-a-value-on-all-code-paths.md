---
title: "Özellik &#39; &lt;propertyname&gt;&#39; belirlemeden #39; tüm kod yolları bir değer döndürmesi t"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords: BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c9ef5b2ac62412f5684cbc78ab6bebf6bc7b6752
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Özellik &#39; &lt;propertyname&gt;&#39; belirlemeden #39; tüm kod yolları bir değer döndürmesi t
Özellik '\<propertyname >' tüm kod yolları bir değer döndürmüyor. Sonuç kullanıldığında çalışma zamanında bir null başvuru özel durumu oluşabilir.  
  
 Bir özellik `Get` yordamının bir değer döndürmüyor kendi kod aracılığıyla en az bir olası yolu vardır.  
  
 Bir özellikten değer döndürme `Get` aşağıdaki yollardan birini yordamda:  
  
-   Özellik adı değeri atayın ve ardından gerçekleştirmek bir `Exit Property` deyimi.  
  
-   Özellik adı değeri atayın ve ardından gerçekleştirmek `End Get` deyimi.  
  
-   Değer içeren bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Denetim geçirir, `Exit Property` veya `End Get` ve özellik adı için herhangi bir değer atamadığınız `Get` yordamı özelliğin veri türünün varsayılan değeri döndürür. Daha fazla bilgi için bkz: "Davranışı" [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42107  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Denetim akışı mantığınızı denetleyin ve satır başı neden olan her deyimi önce bir değer atadığınız emin olun.  
  
     Her zaman kullanıyorsanız her return yordamdan bir değer döndürür güvence altına almak daha kolay `Return` deyimi. Bu, son deyim önce yaparsanız `End Get` olması gereken bir `Return` deyimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellik yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Get deyimi](../../../visual-basic/language-reference/statements/get-statement.md)
