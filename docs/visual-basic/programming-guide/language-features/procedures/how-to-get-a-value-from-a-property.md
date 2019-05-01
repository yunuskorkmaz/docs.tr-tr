---
title: 'Nasıl yapılır: Değer bir özelliği (Visual Basic) alma'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5e2676a0880092a78405fe5dafa0469161b85610
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863642"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Nasıl yapılır: Değer bir özelliği (Visual Basic) alma
Bir özelliğin değeri, özellik adı bir ifade dahil ederek alın.  
  
 Özelliğin `Get` yordamı değeri alır, ancak siz açıkça bu ada göre çağırmayın. Bir değişken kullanma gibi özelliğini kullanın. Visual Basic özelliğin yordamları çağrılar yapar.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>Bir özellikten değer almak için  
  
1. Özellik adı bir ifade bir değişken adı kullanacağınız aynı şekilde kullanın. Bir özellik kullanabileceğiniz bir değişken veya sabit her yerde kullanabilirsiniz.  
  
     -veya-  
  
     Eşit aşağıdaki özellik adını kullanın (`=`) bir atama ifadesinde oturum açın.  
  
     Aşağıdaki örnek, Visual Basic değerini okur `Now` örtük olarak arama özelliğini kendi `Get` yordamı.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. Özellik bağımsız değişkeni alır, parantez içine bağımsız değişken listesi için özellik adıyla izleyin. Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.  
  
3. Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin. Bağımsız değişkenler özelliği karşılık gelen parametreleri tanımlar aynı sırada sağladığınız emin olun.  
  
 İfade bir değişken gibi bir özelliğin değerini katıldığı sabiti misiniz veya değişken veya özellik atama ifadesi sol tarafında depolanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic'de özellikler ile değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bir özellik yordamı çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir özelliğe değer ekleme](./how-to-put-a-value-in-a-property.md)
