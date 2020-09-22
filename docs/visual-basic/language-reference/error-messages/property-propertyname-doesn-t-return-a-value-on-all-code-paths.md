---
title: "'<propertyname>' özelliği tüm kod yollarında değer döndürmüyor"
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 6a80a8275a7b9c5e3cbfa410ee219e0d16ce5918
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870943"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a>'\<propertyname>' özelliği tüm kod yollarında değer döndürmüyor

' \<propertyname> ' Özelliği tüm kod yollarında bir değer döndürmüyor. Sonuç kullanıldığında çalışma zamanında null başvurusu özel durumu oluşabilir.  
  
 Özellik `Get` yordamının, bir değer döndürmeyen kodu üzerinden en az bir olası yolu vardır.  
  
 Aşağıdaki yollarla bir özellik yordamından bir değer döndürebilirsiniz `Get` :  
  
- Özellik adına değeri atayın ve sonra bir `Exit Property` ifade gerçekleştirin.  
  
- Özellik adına değeri atayın ve sonra `End Get` ifadesini gerçekleştirin.  
  
- Değeri [Return ifadesine](../statements/return-statement.md)ekleyin.  
  
 Denetim `Exit Property` veya ' a geçerse `End Get` ve özellik adına herhangi bir değer atamadıysanız, `Get` yordam özelliğin veri türünün varsayılan değerini döndürür. Daha fazla bilgi için bkz. [Işlev deyimindeki](../statements/function-statement.md)"davranış".  
  
 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC42107  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Denetim akışı mantığınızı denetleyin ve dönüşe neden olan her deyimden önce bir değer atadığınızdan emin olun.  
  
     Her zaman ifadesini kullanıyorsanız, yordamdan gelen her döndürün bir değer döndürdüğünden emin olmak daha kolaydır `Return` . Bunu yaparsanız, önceki son deyimin `End Get` bir ifade olması gerekir `Return` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Yordamları](../../programming-guide/language-features/procedures/property-procedures.md)
- [Property Deyimi](../statements/property-statement.md)
- [Get Deyimi](../statements/get-statement.md)
