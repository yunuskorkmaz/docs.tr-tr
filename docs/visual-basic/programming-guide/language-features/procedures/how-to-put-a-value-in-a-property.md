---
title: 'Nasıl yapılır: Bir Özelliğe Değer Ekleme'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: ad0d0e81f94dd3dead50f21c3bd6ff580c004dd6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346050"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Nasıl yapılır: Bir Özelliğe Değer Ekleme (Visual Basic)
Özellik adını atama ifadesinin sol tarafına yerleştirerek bir özelliği bir değer depoluyorsanız.  
  
 Özelliğin `Set` yordamı bir değeri depolar, ancak bunu açıkça adıyla çağırmayın. Özelliğini, bir değişkeni kullandığınız gibi kullanırsınız. Visual Basic, özelliğin yordamlarına çağrı yapar.  
  
### <a name="to-store-a-value-in-a-property"></a>Bir özelliğinde bir değeri depolamak için  
  
1. Atama ifadesinin sol tarafındaki özellik adını kullanın.  
  
     Aşağıdaki örnek, `Set` yordamını örtülü olarak çağırarak Visual Basic `TimeOfDay` özelliğinin değerini öğle olarak ayarlar.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin. Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.  
  
3. Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin. Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.  
  
4. Atama ifadesinin sağ tarafında oluşturulan değer özelliğinde depolanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic Özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Visual Basic varsayılan bir özellik bildirme ve çağırma](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
