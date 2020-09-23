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
ms.openlocfilehash: 7d85066d4678ee2a53b8339bee2db20374482579
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071410"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Nasıl yapılır: Bir Özelliğe Değer Ekleme (Visual Basic)

Özellik adını atama ifadesinin sol tarafına yerleştirerek bir özelliği bir değer depoluyorsanız.  
  
 Özelliğin `Set` yordamı bir değer depolar, ancak bunu açıkça adıyla çağırmayın. Özelliğini, bir değişkeni kullandığınız gibi kullanırsınız. Visual Basic, özelliğin yordamlarına çağrı yapar.  
  
### <a name="to-store-a-value-in-a-property"></a>Bir özelliğinde bir değeri depolamak için  
  
1. Atama ifadesinin sol tarafındaki özellik adını kullanın.  
  
     Aşağıdaki örnek, `TimeOfDay` yordamını dolaylı olarak çağıran Visual Basic özelliğinin değerini öğle olarak ayarlar `Set` .  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin. Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.  
  
3. Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin. Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.  
  
4. Atama ifadesinin sağ tarafında oluşturulan değer özelliğinde depolanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../language-reference/statements/property-statement.md)
- [Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
