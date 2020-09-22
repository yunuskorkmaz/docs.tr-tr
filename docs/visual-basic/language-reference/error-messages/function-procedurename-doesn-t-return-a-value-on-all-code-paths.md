---
title: "'<procedurename>' işlevi tüm kod yollarında değer döndürmüyor"
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 5295775b2541219e611e167e304ca8ef99cf6bd8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874140"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a>'\<procedurename>' işlevi tüm kod yollarında değer döndürmüyor

' \<procedurename> ' İşlevi tüm kod yollarında bir değer döndürmüyor. ' Return ' deyiminiz eksik mi?  
  
 Bir `Function` yordamın, bir değer döndürmeyen kodu aracılığıyla olası en az bir yolu vardır.  
  
 Aşağıdaki yollarla bir yordamdan bir değer döndürebilirsiniz `Function` :  
  
- Değeri [Return ifadesine](../statements/return-statement.md)ekleyin.  
  
- `Function`Yordam adına değeri atayın ve sonra bir `Exit Function` ifade gerçekleştirin.  
  
- `Function`Yordam adına değeri atayın ve sonra `End Function` ifadesini gerçekleştirin.  
  
 Denetim veya öğesine geçerse `Exit Function` `End Function` ve yordam adına herhangi bir değer atamadıysanız, yordam dönüş veri türünün varsayılan değerini döndürür. Daha fazla bilgi için bkz. [Işlev deyimindeki](../statements/function-statement.md)"davranış".  
  
 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC42105  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Denetim akışı mantığınızı denetleyin ve dönüşe neden olan her deyimden önce bir değer atadığınızdan emin olun.  
  
     Her zaman ifadesini kullanıyorsanız, yordamdan gelen her döndürün bir değer döndürdüğünden emin olmak daha kolaydır `Return` . Bunu yaparsanız, önceki son deyimin `End Function` bir ifade olması gerekir `Return` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlev Yordamları](../../programming-guide/language-features/procedures/function-procedures.md)
- [Function Deyimi](../statements/function-statement.md)
- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
