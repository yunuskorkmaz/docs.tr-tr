---
title: İşlev &#39; &lt;procedurename&gt; &#39; eklenmemişse&#39;t, tüm kod yollarında bir değer döndürür
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: b6cc5143aafb6c2554b183a1fc5fb3b1331ec5d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552196"
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a>İşlev &#39; &lt;procedurename&gt; &#39; eklenmemişse&#39;t, tüm kod yollarında bir değer döndürür
İşlev '\<procedurename >' bütün kod yollarında değer döndürmüyor. 'Return' deyiminiz eksik olabilir mi?  
  
 A `Function` yordamının bir değer döndürmeyen kendi kod aracılığıyla en az bir olası yol vardır.  
  
 Bir değer döndürmek bir `Function` aşağıdaki yollardan biriyle yordamda:  
  
-   Değer bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).  
  
-   Değer atayın `Function` yordamı adlandırın ve ardından gerçekleştirmek bir `Exit Function` deyimi.  
  
-   Değer atayın `Function` yordamı adlandırın ve ardından gerçekleştirmek `End Function` deyimi.  
  
 Denetim için geçerse `Exit Function` veya `End Function` ve yordam adı için herhangi bir değer atamadıysanız, yordamın dönüş veri türünün varsayılan değerini döndürür. Daha fazla bilgi için "Davranışı" bölümüne bakın. [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42105  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Denetim akışı mantığınızı denetleyin ve bir dönüş neden her deyiminden önce bir değer atadığınız emin olun.  
  
     Her zaman kullanırsanız her iade yordamdan gelen bir değer döndürür garanti daha kolaydır `Return` deyimi. Bu, son deyim önce yaparsanız `End Function` olmalıdır bir `Return` deyimi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İşlev Yordamları](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
