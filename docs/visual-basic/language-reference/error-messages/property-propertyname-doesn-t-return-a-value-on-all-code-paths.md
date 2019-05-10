---
title: "'<propertyname>' özelliği tüm kod yollarında değer döndürmüyor"
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: a5cb28a024274e58da1755b437d6ba4ca6712610
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661709"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a>Özellik '\<propertyname >' bütün kod yollarında değer döndürmüyor
Özellik '\<propertyname >' bütün kod yollarında değer döndürmüyor. Sonuç kullanıldığında çalışma zamanında null başvurusu özel durumu oluşabilir.  
  
 Bir özellik `Get` yordamının bir değer döndürmeyen kendi kod aracılığıyla en az bir olası yol vardır.  
  
 Bir özelliği bir değer döndürebilir `Get` aşağıdaki yollardan biriyle yordamda:  
  
- Özellik adlarının değer atamak ve ardından gerçekleştirin bir `Exit Property` deyimi.  
  
- Özellik adlarının değer atamak ve ardından gerçekleştirin `End Get` deyimi.  
  
- Değer bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Denetim için geçerse `Exit Property` veya `End Get` ve özellik adı için herhangi bir değer atamadınız `Get` yordamı özelliğinin veri türünün varsayılan değerini döndürür. Daha fazla bilgi için "Davranışı" bölümüne bakın. [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42107  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Denetim akışı mantığınızı denetleyin ve bir dönüş neden her deyiminden önce bir değer atadığınız emin olun.  
  
     Her zaman kullanırsanız her iade yordamdan gelen bir değer döndürür garanti daha kolaydır `Return` deyimi. Bu, son deyim önce yaparsanız `End Get` olmalıdır bir `Return` deyimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Get Deyimi](../../../visual-basic/language-reference/statements/get-statement.md)
