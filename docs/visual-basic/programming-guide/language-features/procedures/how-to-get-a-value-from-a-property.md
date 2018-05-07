---
title: 'Nasıl yapılır: Bir Özellikten Değer Alma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 9f97669e8d18e7fc633cb0e691d973a611a8cea0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Nasıl yapılır: Bir Özellikten Değer Alma (Visual Basic)
Bir ifadeyi özellik adı dahil olmak üzere bir özelliğin değerini alır.  
  
 Özelliğin `Get` yordamı değeri alır, ancak siz açıkça, ada göre çağırmayın. Bir değişken kullandığınız özelliğini kullanın. Visual Basic özelliğin yordamları çağrılar.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>Bir özellikten değer almak için  
  
1.  Özellik adı bir ifade bir değişken adı kullanacağınız aynı şekilde kullanın. Bir özellik kullanabileceğiniz bir değişken veya sabit herhangi bir yerde kullanabilirsiniz.  
  
     -veya-  
  
     Eşittir aşağıdaki özellik adı kullanın (`=`) bir atama deyiminde oturum açın.  
  
     Aşağıdaki örnek Visual Basic değerini okur `Now` örtük olarak arama özelliği, kendi `Get` yordamı.  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  Özellik bağımsız değişken alıyorsa, özellik adı bağımsız değişken listesi kapsamak için parantez ile izleyin. Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.  
  
3.  Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin. Bağımsız değişkenler özelliği ilgili parametreleri tanımlar aynı sırada sağladığınız emin olun.  
  
 İfade bir değişken olarak yalnızca özelliğin değerini katıldığı sabiti misiniz veya değişkenin veya özelliğin Atama ifadesinin sol tarafında depolanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Özellik Yordamları](./property-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Visual Basic'de özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)  
 [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)  
 [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)  
 [Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)  
 [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)
