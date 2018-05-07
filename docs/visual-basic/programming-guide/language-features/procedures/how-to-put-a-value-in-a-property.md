---
title: 'Nasıl yapılır: Bir Özelliğe Değer Ekleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 29e68ca2b9436921c81346eb1def2417157aae9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Nasıl yapılır: Bir Özelliğe Değer Ekleme (Visual Basic)
Bir özellik değeri Atama ifadesinin sol tarafta özellik adını koyarak depolar.  
  
 Özelliğin `Set` yordamı bir değer depolar, ancak siz açıkça, ada göre çağırmayın. Bir değişken kullandığınız özelliğini kullanın. Visual Basic özelliğin yordamları çağrılar.  
  
### <a name="to-store-a-value-in-a-property"></a>Bir özelliğin değeri depolamak için  
  
1.  Özellik adı atama ifadesinin sol taraftaki kullanın.  
  
     Aşağıdaki örnek Visual Basic değerini ayarlar `TimeOfDay` öğlen, örtük çağırma özelliğine kendi `Set` yordamı.  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin. Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.  
  
3.  Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin. Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.  
  
4.  Atama ifadesinin sağ tarafında oluşturulan değeri özelliğinde depolanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [Özellik Yordamları](./property-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Visual Basic'de özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)  
 [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)  
 [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)  
 [Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)  
 [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
