---
title: Yordam Parametreleri ve Bağımsız Değişkenleri
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
ms.openlocfilehash: c7f8eb1fa4e1fa3d87474d048d5a60994b0b7fc5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071280"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Yordam Parametreleri ve Bağımsız Değişkenler (Visual Basic)

Çoğu durumda, bir yordam çağrıldığı koşullara ilişkin bazı bilgilere ihtiyaç duyuyor. Yinelenen veya paylaşılan görevler gerçekleştiren bir yordam, her çağrı için farklı bilgiler kullanır. Bu bilgiler, çağırdığınızda yordama geçirdiğiniz değişkenlerin, sabitlerin ve ifadelerden oluşur.  
  
 Bir *parametre* , yordamı çağırdığınızda belirtmeniz beklenen bir değeri temsil eder. Yordamın bildirimi, parametrelerini tanımlar.  
  
 Parametresiz, bir parametre veya birden fazla parametre içermeyen bir yordam tanımlayabilirsiniz. Yordam tanımının parametreleri belirten bölümü *parametre listesi*olarak adlandırılır.  
  
 Bir *bağımsız değişken* , yordamı çağırdığınızda bir yordam parametresine sağladığınız değeri temsil eder. Çağıran kod, yordamı çağırdığında bağımsız değişkenleri sağlar. Yordam çağrısının bağımsız değişkenleri belirten kısmına *bağımsız değişken listesi*denir.  
  
 Aşağıdaki çizim, iki farklı yerden yordam çağıran kodu gösterir `safeSquareRoot` . İlk çağrı, değişkenin değerini `x` (4,0) parametresine geçirir `number` ve `root` (2,0) içindeki dönüş değeri değişkenine atanır `y` . İkinci çağrı 9,0 sabit değerini ' a geçirir `number` ve dönüş değerini (3,0) değişkenine atar `z` .  
  
 ![Bir parametreye bağımsız değişken geçirmeyi gösteren diyagram](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 Daha fazla bilgi için bkz. [Parametreler ve bağımsız değişkenler arasındaki farklar](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Parametre veri türü  

 Bildiriminde yan tümcesini kullanarak bir parametre için veri türü tanımlarsınız `As` . Örneğin, aşağıdaki işlev bir dizeyi ve bir tamsayıyı kabul eder.  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 Tür denetleme anahtarı ([Option Strict deyimi](../../../language-reference/statements/option-strict-statement.md)) `Off,` yan tümcesi ise, `As` herhangi bir parametre kullanıyorsa, tüm parametrelerin onu kullanması gerekir. Tür denetlemesi ise, `On` `As` yan tümce tüm yordam parametreleri için gereklidir.  
  
 Çağıran kod, bir parametre gibi karşılık gelen parametresinden farklı bir veri türüne sahip bir bağımsız değişken sağlamayı bekliyorsa `Byte` `String` , aşağıdakilerden birini yapması gerekir:  
  
- Yalnızca parametre veri türüne genişletip veri türlerine sahip bağımsız değişkenler sağlayın;  
  
- `Option Strict Off`Örtülü daraltma dönüştürmelerine izin vermek için ayarlayın; veya  
  
- Veri türünü açık bir şekilde dönüştürmek için bir dönüştürme anahtar sözcüğü kullanın.  
  
### <a name="type-parameters"></a>Tür Parametreleri  

 *Genel yordam* , normal parametrelerine ek olarak bir veya daha fazla *tür parametresi* de tanımlar. Genel yordam, çağıran kodun yordamı her çağırdığında farklı veri türlerini geçmesine izin verir, böylece veri türlerini her bir çağrının gereksinimlerine uyarlayabilirsiniz. Bkz. [Visual Basic genel yordamlar](../data-types/generic-procedures.md).  
  
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
- [Visual Basic'de Tür Dönüştürmeleri](../data-types/type-conversions.md)
