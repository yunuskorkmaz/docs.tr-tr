---
title: 'Nasıl yapılır: (Visual Basic) bir özellik yordamı çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 6a7c55433001af5c5695044f41f866c1df8c3651
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977870"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir özellik yordamı çağırma
Özelliğin değeri depolamak veya değeri alınırken bir özellik yordamı çağırma. Bir özelliği bir değişkene erişme gibi erişebilirsiniz.  
  
 Özelliğin `Set` yordamı bir değer depolar ve kendi `Get` yordamı değeri alır. Ancak, açıkça bu yordamları adıyla çağırmayın. Yalnızca siz depolamak veya bir değişkenin değerini almak bir atama ifadesi veya bir ifade özelliği kullanın. Visual Basic özelliğin yordamları çağrılar yapar.  
  
### <a name="to-call-a-propertys-get-procedure"></a>Özellik Get yordamı çağırmak için  
  
1.  Özellik adı bir ifade bir değişken adı kullanacağınız aynı şekilde kullanın. Bir özellik kullanabileceğiniz bir değişken veya sabit her yerde kullanabilirsiniz.  
  
     -veya-  
  
     Eşit aşağıdaki özellik adını kullanın (`=`) bir atama ifadesinde oturum açın.  
  
     Aşağıdaki örnek değerini okur <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> örtük olarak arama özelliğini kendi `Get` yordamı.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2.  Özellik bağımsız değişkeni alır, parantez içine bağımsız değişken listesi için özellik adıyla izleyin. Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.  
  
3.  Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin. Bağımsız değişkenler özelliği karşılık gelen parametreleri tanımlar aynı sırada sağladığınız emin olun.  
  
 İfade bir değişken gibi bir özelliğin değerini katıldığı sabiti misiniz veya değişken veya özellik atama ifadesi sol tarafında depolanır.  
  
### <a name="to-call-a-propertys-set-procedure"></a>Bir özellik çağırmak için yordam kümesinde  
  
1.  Özellik adı, atama deyiminin sol tarafında kullanın.  
  
     Aşağıdaki örnekte ayarlar <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> özelliği, örtük olarak çağırma `Set` yordamı.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2.  Özellik bağımsız değişkeni alır, parantez içine bağımsız değişken listesi için özellik adıyla izleyin. Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.  
  
3.  Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin. Bağımsız değişkenler özelliği karşılık gelen parametreleri tanımlar aynı sırada sağladığınız emin olun.  
  
 Atama ifadesi sağ tarafında oluşturulan değeri özelliğinde depolanır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic'de özellikler ile değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir özelliğe değer ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir özellikten değer alma](./how-to-get-a-value-from-a-property.md)
- [Get Deyimi](../../../../visual-basic/language-reference/statements/get-statement.md)
- [Set Deyimi](../../../../visual-basic/language-reference/statements/set-statement.md)
