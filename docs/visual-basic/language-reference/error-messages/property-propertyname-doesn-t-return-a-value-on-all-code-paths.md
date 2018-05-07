---
title: Özellik &#39; &lt;propertyname&gt; &#39; mevcut değil&#39;t tüm kod yolları bir değer döndürür
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 72bc7e45cadd2528f29c88bf6e80ee5f381052dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Özellik &#39; &lt;propertyname&gt; &#39; mevcut değil&#39;t tüm kod yolları bir değer döndürür
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
 [Özellik Yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Get Deyimi](../../../visual-basic/language-reference/statements/get-statement.md)
