---
title: 'Nasıl yapılır: Bir Özellikten Değer Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 85512d4311d3e731a2c4e129d6a01f9b3273b333
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74339824"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Nasıl yapılır: Bir Özellikten Değer Alma (Visual Basic)
Özellik adını bir ifadeye ekleyerek bir özelliğin değerini elde edersiniz.  
  
 Özelliğin `Get` yordamı değeri alır, ancak bunu açıkça adıyla çağırmayın. Özelliğini, bir değişkeni kullandığınız gibi kullanırsınız. Visual Basic, özelliğin yordamlarına çağrı yapar.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>Bir özellikten değer almak için  
  
1. Bir ifadede özellik adını bir değişken adı kullandığınız şekilde kullanın. Bir özelliği, bir değişkeni veya sabiti kullanabileceğiniz her yerde kullanabilirsiniz.  
  
     veya  
  
     Atama deyimindeki eşittir (`=`) işaretinden sonra özellik adını kullanın.  
  
     Aşağıdaki örnek, `Get` yordamını dolaylı olarak çağıran Visual Basic `Now` özelliğinin değerini okur.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. Özelliği bağımsız değişkenler alırsa, bağımsız değişken listesini kapsamak için parantez ile birlikte özellik adını izleyin. Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.  
  
3. Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin. Bağımsız değişkenleri özelliğin ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.  
  
 Özelliğin değeri, ifadeye yalnızca değişken veya sabit gibi, ya da atama deyiminin sol tarafındaki değişkende veya özellikte saklanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic Özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Visual Basic varsayılan bir özellik bildirme ve çağırma](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)
