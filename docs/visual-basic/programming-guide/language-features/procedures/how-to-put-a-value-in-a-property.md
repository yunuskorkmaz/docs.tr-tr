---
title: 'Nasıl yapılır: Bir özelliğe (Visual Basic) bir değer ekleme'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: d40ca98f94f410bb20c8df0e7f1a3f216cf53bf9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589171"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Nasıl yapılır: Bir özelliğe (Visual Basic) bir değer ekleme
Atama deyiminin sol tarafında özellik adını koyarak bir özelliğe bir değer depolar.  
  
 Özelliğin `Set` yordamı bir değer depolar, ancak siz açıkça bu ada göre çağırmayın. Bir değişken kullanma gibi özelliğini kullanın. Visual Basic özelliğin yordamları çağrılar yapar.  
  
### <a name="to-store-a-value-in-a-property"></a>Bir özelliğin değeri depolamak için  
  
1.  Özellik adı, atama deyiminin sol tarafında kullanın.  
  
     Aşağıdaki örnek, Visual Basic değerini ayarlar `TimeOfDay` noon, örtük olarak arama özelliğini kendi `Set` yordamı.  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  Özellik bağımsız değişkeni alır, parantez içine bağımsız değişken listesi için özellik adıyla izleyin. Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.  
  
3.  Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin. Bağımsız değişkenler özelliği karşılık gelen parametreleri tanımlar aynı sırada sağladığınız emin olun.  
  
4.  Atama ifadesi sağ tarafında oluşturulan değeri özelliğinde depolanır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic'de özellikler ile değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bir özellik yordamı çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir özellikten değer alma](./how-to-get-a-value-from-a-property.md)
