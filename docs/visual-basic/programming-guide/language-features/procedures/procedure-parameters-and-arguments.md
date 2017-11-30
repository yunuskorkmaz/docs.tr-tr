---
title: "Yordam Parametreleri ve Bağımsız Değişkenler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 726667950cfb227a0359bd6238c202883561749c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
### <a name="type-parameters"></a>Tür Parametreleri  
 A *genel yordam* de bir veya daha fazla tanımlar *tür parametrelerindeki* normal parametrelerinin yanı sıra. Veri türleri farklı veri türleri tek tek her çağrı gereksinimlerini uyarlayabilirsiniz şekilde yordam çağrıları her zaman geçmesi için çağıran kodu genel bir yordam sağlar. Bkz: [Visual Basic'de genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Alt yordamlar](./sub-procedures.md)  
 [İşlev yordamları](./function-procedures.md)  
 [Özellik yordamları](./property-procedures.md)  
 [İşleç yordamları](./operator-procedures.md)  
 [Nasıl yapılır: bir yordamın parametresini tanımlama](./how-to-define-a-parameter-for-a-procedure.md)  
 [Nasıl yapılır: bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız değişkenleri değere ve başvuruya göre geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Yordam aşırı yüklemesi](./procedure-overloading.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
