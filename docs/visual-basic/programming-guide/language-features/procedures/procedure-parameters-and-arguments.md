---
title: Parametreler ve Bağımsız Değişkenler
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 7dfbbcb39cf7bb05c8a62a7a252e425f287c9a09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352577"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Yordam Parametreleri ve Bağımsız Değişkenler (Visual Basic)
Çoğu durumda, bir yordam çağrıldığı koşullara ilişkin bazı bilgilere ihtiyaç duyuyor. Yinelenen veya paylaşılan görevler gerçekleştiren bir yordam, her çağrı için farklı bilgiler kullanır. Bu bilgiler, çağırdığınızda yordama geçirdiğiniz değişkenlerin, sabitlerin ve ifadelerden oluşur.  
  
 Bir *parametre* , yordamı çağırdığınızda belirtmeniz beklenen bir değeri temsil eder. Yordamın bildirimi, parametrelerini tanımlar.  
  
 Parametresiz, bir parametre veya birden fazla parametre içermeyen bir yordam tanımlayabilirsiniz. Yordam tanımının parametreleri belirten bölümü *parametre listesi*olarak adlandırılır.  
  
 Bir *bağımsız değişken* , yordamı çağırdığınızda bir yordam parametresine sağladığınız değeri temsil eder. Çağıran kod, yordamı çağırdığında bağımsız değişkenleri sağlar. Yordam çağrısının bağımsız değişkenleri belirten kısmına *bağımsız değişken listesi*denir.  
  
 Aşağıdaki çizim, iki farklı yerden yordam `safeSquareRoot` çağıran kodu gösterir. İlk çağrı `x` (4,0) değişkeninin değerini `number`parametresine geçirir ve `root` (2,0) içindeki dönüş değeri `y`değişkenine atanır. İkinci çağrı 9,0 sabit değerini `number`geçirir ve dönüş değerini (3,0) `z`değişkenine atar.  
  
 ![Bir parametreye bağımsız değişken geçirmeyi gösteren diyagram](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 Daha fazla bilgi için bkz. [Parametreler ve bağımsız değişkenler arasındaki farklar](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Parametre veri türü  
 Bir parametre için, bildiriminde `As` yan tümcesini kullanarak bir veri türü tanımlarsınız. Örneğin, aşağıdaki işlev bir dizeyi ve bir tamsayıyı kabul eder.  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 Tür denetleme anahtarı ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) `Off,` `As` yan tümcesi isteğe bağlıdır, ancak herhangi bir parametre kullanıyorsa, tüm parametrelerin onu kullanması gerekir. Tür denetlemesi `On`, tüm yordam parametreleri için `As` yan tümcesi gereklidir.  
  
 Çağıran kod, `String` parametreye `Byte` gibi, karşılık gelen parametresinden farklı bir veri türüne sahip bir bağımsız değişken sağlamayı bekliyorsa, aşağıdakilerden birini yapmanız gerekir:  
  
- Yalnızca parametre veri türüne genişletip veri türlerine sahip bağımsız değişkenler sağlayın;  
  
- Örtülü daraltma dönüştürmelerine izin vermek için `Option Strict Off` ayarlayın; veya  
  
- Veri türünü açık bir şekilde dönüştürmek için bir dönüştürme anahtar sözcüğü kullanın.  
  
### <a name="type-parameters"></a>Tür Parametreleri  
 *Genel yordam* , normal parametrelerine ek olarak bir veya daha fazla *tür parametresi* de tanımlar. Genel yordam, çağıran kodun yordamı her çağırdığında farklı veri türlerini geçmesine izin verir, böylece veri türlerini her bir çağrının gereksinimlerine uyarlayabilirsiniz. Bkz. [Visual Basic genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: Bir Yordamın Parametresini Tanımlama](./how-to-define-a-parameter-for-a-procedure.md)
- [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Visual Basic dönüşümler yazın](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
