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
ms.openlocfilehash: b0ab186945b456d7fb4dde3f52724b08a99e2827
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652506"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Yordam Parametreleri ve Bağımsız Değişkenler (Visual Basic)
Çoğu durumda, bir yordam, onu çağrıldı koşullar hakkında bazı bilgiler gerekir. Yinelenen veya paylaşılan görevleri gerçekleştiren bir yordam her çağrı için farklı bilgileri kullanır. Bu bilgiler değişkenlerinin, sabitleri ve onu çağırdığınızda, yordama geçirdiğiniz ifadeler oluşur.  
  
 A *parametresi* yordamı, çağırdığınızda temin etmeniz bekliyor bir değeri temsil eder. Yordam bildirimi parametrelerini tanımlar.  
  
 Hiçbir parametre, bir parametre veya birden fazla ile bir yordam tanımlayabilirsiniz. Parametreleri belirtir yordamı tanımının bir parçası olarak adlandırılan *parametre listesi*.  
  
 Bir *bağımsız değişkeni* yordam çağrısı, sağladığınız değeri bir yordam parametresini temsil eder. Yordam çağrıları, çağrıyı yapan kod bağımsız değişkenler sağlar. Bağımsız değişkenleri belirten yordam çağrısı parçası olarak adlandırılan *bağımsız değişken listesi*.  
  
 Yordamı çağırma kod aşağıda gösterilmiştir `safeSquareRoot` iki farklı yerde. İlk çağrıda değişkenin değeri olarak geçirir `x` (4.0) parametresine `number`ve dönüş değeri `root` (2.0) değişkenine atanan `y`. Değişmez değer 9.0 için ikinci çağrı geçirir `number`ve dönüş değeri (3.0) değişkenine atar `z`.  
  
 ![Parametresi için bağımsız değişken geçirme grafik diyagramı](./media/parametersargue.gif "ParametersArgue")  
Bir parametre bağımsız değişken geçirme  
  
 Daha fazla bilgi için bkz: [arasındaki farklar parametreler ve bağımsız değişkenler](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Parametre veri türü  
 Kullanarak bir veri türü için bir parametre tanımlayın `As` bildiriminden yan tümcesinde. Örneğin, aşağıdaki işlev bir dize ve tamsayı kabul eder.  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 Tür denetleme geçiş yaparsanız ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `Off,` `As` yan tümcesi olduğunu isteğe bağlı, herhangi bir parametre kullanıyorsa, tüm parametreleri bunu kullanmalı dışında. Tür denetleme ise `On`, `As` yan tümcesi tüm yordam parametreleri için gereklidir.  
  
 Çağıran kodu bir bağımsız değişken bir veri türü, karşılık gelen bir parametre farklı gibi sağlayın bekliyor varsa `Byte` için bir `String` parametresi, aşağıdakilerden birini yapmalısınız:  
  
-   Tedarik yalnızca bağımsız değişken parametre veri türü genişletmek veri türleriyle;  
  
-   Ayarlama `Option Strict Off` örtük daraltma dönüşümleri; izin vermek veya  
  
-   Dönüştürme anahtar sözcüğü açıkça veri türüne dönüştürmek için kullanın.  
  
### <a name="type-parameters"></a>Tür ParameTReleri  
 A *genel yordam* de bir veya daha fazla tanımlar *tür parametrelerindeki* normal parametrelerinin yanı sıra. Veri türleri farklı veri türleri tek tek her çağrı gereksinimlerini uyarlayabilirsiniz şekilde yordam çağrıları her zaman geçmesi için çağıran kodu genel bir yordam sağlar. Bkz: [Visual Basic'de genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Alt Yordamlar](./sub-procedures.md)  
 [İşlev Yordamları](./function-procedures.md)  
 [Özellik Yordamları](./property-procedures.md)  
 [İşleç Yordamları](./operator-procedures.md)  
 [Nasıl yapılır: Bir Yordamın Parametresini Tanımlama](./how-to-define-a-parameter-for-a-procedure.md)  
 [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Yordam Aşırı Yüklemesi](./procedure-overloading.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
