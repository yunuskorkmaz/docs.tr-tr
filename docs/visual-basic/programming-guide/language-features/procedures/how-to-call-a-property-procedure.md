---
title: 'Nasıl yapılır: Bir Özellik Yordamı Çağırma (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38b3704328916a487f94879ea0096ae923f19082
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>Nasıl yapılır: Bir Özellik Yordamı Çağırma (Visual Basic)
Bir özellik değeri depolamak veya değeri alınırken bir özellik yordamı çağırma. Bir özelliği bir değişkene erişme aynı şekilde erişin.  
  
 Özelliğin `Set` yordamı bir değer depolar ve kendi `Get` yordamı değerini alır. Ancak, siz açıkça bu yordamları adıyla çağırmayın. Yalnızca siz depolamak veya bir değişkenin değerini almak bir atama ifadesi veya bir ifade özelliğini kullanın. Visual Basic özelliğin yordamları çağrılar.  
  
### <a name="to-call-a-propertys-get-procedure"></a>Bir özelliğin Get yordamı çağırmak için  
  
1.  Özellik adı bir ifade bir değişken adı kullanacağınız aynı şekilde kullanın. Bir özellik kullanabileceğiniz bir değişken veya sabit herhangi bir yerde kullanabilirsiniz.  
  
     -veya-  
  
     Eşittir aşağıdaki özellik adı kullanın (`=`) bir atama deyiminde oturum açın.  
  
     Aşağıdaki örnek değeri okuyan <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> örtük olarak arama özelliği, kendi `Get` yordamı.  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin. Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.  
  
3.  Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin. Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.  
  
 İfade bir değişken olarak yalnızca özelliğin değerini katıldığı sabiti misiniz veya değişkenin veya özelliğin Atama ifadesinin sol tarafında depolanır.  
  
### <a name="to-call-a-propertys-set-procedure"></a>Bir özellik çağırmak için yordam kümesinde  
  
1.  Özellik adı atama ifadesinin sol taraftaki kullanın.  
  
     Aşağıdaki örnek değerini ayarlar <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> örtük olarak arama özelliği, `Set` yordamı.  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin. Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.  
  
3.  Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin. Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.  
  
 Atama ifadesinin sağ tarafında oluşturulan değeri özelliğinde depolanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellik Yordamları](./property-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Visual Basic'de özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)  
 [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)  
 [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)  
 [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)  
 [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)  
 [Get Deyimi](../../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set Deyimi](../../../../visual-basic/language-reference/statements/set-statement.md)
