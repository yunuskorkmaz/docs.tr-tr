---
title: Yordam Parametreleri ve Bağımsız Değişkenler (Visual Basic)
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
ms.openlocfilehash: f7291d809c754249c155eb9382f3fcd8a63c20c7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972572"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Yordam Parametreleri ve Bağımsız Değişkenler (Visual Basic)
Çoğu durumda, bir yordam içinde bunu çağrıldıktan koşullar hakkında bazı bilgiler gerekiyor. Yinelenen veya paylaşılan görevleri gerçekleştiren bir yordam her çağrı için farklı bilgileri kullanır. Bu bilgiler, değişkenleri, sabitleri ve onu çağırdığınızda yordama geçirdiğiniz ifadeleri oluşur.  
  
 A *parametre* yordamı çağırdığınızda, temin etmeniz bekliyor. bir değeri temsil eder. Yordam bildirimi parametrelerini tanımlar.  
  
 Bir yordam parametre, bir parametre veya birden fazla tanımlayabilirsiniz. Parametreleri belirtir bir yordam tanımının bir parçası olarak adlandırılan *parametre listesi*.  
  
 Bir *bağımsız değişken* yordamı çağırdığınızda, sağladığınız değerin bir yordamın parametresini temsil eder. Yordamı çağırdığında, çağıran kodun bağımsız değişkenleri sağlar. Bağımsız değişkenleri belirten yordam çağrısı bir parçası olarak adlandırılan *bağımsız değişken listesi*.  
  
 Yordamı çağırma kodu aşağıdaki çizimde `safeSquareRoot` iki farklı yerde. İlk çağrı değişkenin değeri olarak geçirir `x` (4.0) parametresine `number`ve dönüş değeri `root` (2.0) değişkenine atanan `y`. Değişmez değer 9.0 için yapılan ikinci çağrı geçirir `number`ve dönüş değeri (3.0) değişkene atar `z`.  
  
 ![Parametresi için bağımsız değişken geçirme grafik diyagramı](./media/parametersargue.gif "ParametersArgue")  
Bir parametre bağımsız değişken geçirme  
  
 Daha fazla bilgi için [arasındaki farklar parametreler ve bağımsız değişkenler](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Parametre veri türü  
 Bir parametrenin veri türünü kullanarak tanımladığınız `As` bildiriminden yan tümcesi. Örneğin, aşağıdaki işlev bir dize ve tamsayı kabul eder.  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 Tür denetleme geçerseniz ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `Off,` `As` yan tümcesi, isteğe bağlıdır, hariç, herhangi bir parametre kullanıyorsa, tüm parametreleri onu kullanmanız gerekir. Tür denetleme ise `On`, `As` yan tümcesi tüm parametreler için gereklidir.  
  
 Çağıran kod gibi bir bağımsız değişkeni, karşılık gelen parametresinin farklı bir veri türü ile sağlamak bekliyor durumunda `Byte` için bir `String` parametresi, aşağıdakilerden birini yapmalısınız:  
  
-   Kaynağı yalnızca bağımsız değişkenler için parametre veri türü genişletmek veri türleriyle;  
  
-   Ayarlama `Option Strict Off` daraltma dönüştürmelerini örtülü; izin vermek veya  
  
-   Dönüştürme anahtar sözcüğü, veri türüne açıkça dönüştürmek için kullanın.  
  
### <a name="type-parameters"></a>Tür ParameTReleri  
 A *genel yordam* ayrıca bir veya daha fazla tanımlar *tür parametrelerindeki* normal parametrelerini yanı sıra. Çağıran kod, veri türleri için her bir çağrıyı gereksinimlerini karşılayacak hale getirebilirsiniz şekilde yordamı, çağırdığı her zaman geçiş farklı veri türleri genel bir yordam sağlar. Bkz: [Visual Basic'de genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: Bir yordamın parametresini tanımlama](./how-to-define-a-parameter-for-a-procedure.md)
- [Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
