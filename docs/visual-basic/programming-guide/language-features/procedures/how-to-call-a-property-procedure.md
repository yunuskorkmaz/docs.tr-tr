---
title: 'Nasıl yapılır: Bir Özellik Yordamı Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 0b35751136937d4cee5b3ca9669b43d3fbdf71a1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071968"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>Nasıl yapılır: Bir Özellik Yordamı Çağırma (Visual Basic)

Özellik yordamını, özelliğinde bir değer depolayarak veya değerini alarak çağırabilirsiniz. Bir özelliğe, bir değişkene erişirken aynı şekilde erişirsiniz.  
  
 Özelliğin `Set` yordamı bir değeri depolar ve `Get` yordamı değerini alır. Ancak, bu yordamları adına göre açıkça çağırmayın. Bir değişkenin değerini depoladığınız veya alacağınız gibi, bir atama deyiminde veya bir ifadede özelliğini kullanın. Visual Basic, özelliğin yordamlarına çağrı yapar.  
  
### <a name="to-call-a-propertys-get-procedure"></a>Bir özelliğin get yordamını çağırmak için  
  
1. Bir ifadede özellik adını bir değişken adı kullandığınız şekilde kullanın. Bir özelliği, bir değişkeni veya sabiti kullanabileceğiniz her yerde kullanabilirsiniz.  
  
     -veya-  
  
     Atama ifadesinde eşittir () işaretinden sonra özellik adını kullanın `=` .  
  
     Aşağıdaki örnek, <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> yordamını dolaylı olarak çağıran özelliğinin değerini okur `Get` .  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin. Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.  
  
3. Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin. Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.  
  
 Özelliğin değeri, ifadeye yalnızca değişken veya sabit gibi, ya da atama deyiminin sol tarafındaki değişkende veya özellikte saklanır.  
  
### <a name="to-call-a-propertys-set-procedure"></a>Bir özelliğin set yordamını çağırmak için  
  
1. Atama ifadesinin sol tarafındaki özellik adını kullanın.  
  
     Aşağıdaki örnek, <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> yordamı dolaylı olarak çağıran özelliğin değerini ayarlar `Set` .  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin. Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.  
  
3. Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin. Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.  
  
 Atama ifadesinin sağ tarafında oluşturulan değer özelliğinde depolanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../language-reference/statements/property-statement.md)
- [Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
- [Get Deyimi](../../../language-reference/statements/get-statement.md)
- [Set deyimleri](../../../language-reference/statements/set-statement.md)
