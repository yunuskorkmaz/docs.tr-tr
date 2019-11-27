---
title: 'Nasıl yapılır: varsayılan bir özellik bildirme ve çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: b01188ed8a9ff4da95a6975dcac3509625fdffb2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349678"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma
*Varsayılan özellik* , kodunuzun onu belirtmeden erişebileceği bir sınıf veya yapı özelliğidir. Kod adlarını bir sınıf veya yapıya çağırmak ancak bir özelliği değil ve bağlam bir özelliğe erişim izni veriyorsa, Visual Basic, varsa bu sınıfa veya yapının varsayılan özelliğine erişimi çözer.  
  
 Bir sınıf veya yapı en çok bir varsayılan özelliğe sahip olabilir. Ancak, varsayılan bir özelliği aşırı yükleyebilir ve birden fazla sürümüne sahip olabilirsiniz.  
  
 Daha fazla bilgi için bkz. [Default](../../../../visual-basic/language-reference/modifiers/default.md).  
  
### <a name="to-declare-a-default-property"></a>Varsayılan bir özellik bildirmek için  
  
1. Özelliği normal şekilde bildirin. `Shared` veya `Private` anahtar sözcüğünü belirtmeyin.  
  
2. Özellik bildirimine `Default` anahtar sözcüğünü ekleyin.  
  
3. Özellik için en az bir parametre belirtin. En az bir bağımsız değişken almaz varsayılan bir özellik tanımlayamazsınız.  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a>Varsayılan bir özelliği çağırmak için  
  
1. Kapsayan sınıf veya yapı türü için bir değişken bildirin.  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. Değişken adını, normalde özellik adını dahil ettiğiniz bir ifadede kullanın.  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. Parantez içindeki bir bağımsız değişken listesiyle birlikte değişken adını izleyin. Varsayılan özellik en az bir bağımsız değişken almalıdır.  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. Varsayılan özellik değerini almak için, değişken adını bağımsız değişken listesiyle, bir ifadede veya bir atama deyiminde eşittir (`=`) işaretinden sonra kullanın.  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. Varsayılan özellik değerini ayarlamak için, bir atama ifadesinin sol tarafında bir bağımsız değişken listesiyle birlikte değişken adını kullanın.  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. Herhangi bir özelliğe erişmek için yaptığınız gibi, her zaman varsayılan özellik adını değişken adıyla birlikte belirtebilirsiniz.  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sınıfında varsayılan bir özellik bildirir.  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `class1`sınıfında `myProperty` varsayılan özelliğin nasıl çağrılacağını gösterir. Üç atama deyimi `myProperty`değerleri depolar ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> çağrısı değerleri okur.  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 Varsayılan bir özelliğin en yaygın kullanımı, çeşitli koleksiyon sınıflarında <xref:Microsoft.VisualBasic.Collection.Item%2A> özelliğidir.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Varsayılan Özellikler, kaynak kodu karakterlerinin küçük bir azalmasına neden olabilir, ancak kodunuzun okunmasını zorlaşabilir. Çağıran kod sınıfınız veya yapınız hakkında bilgi sahibi değilse, sınıf veya yapı adına bir başvuru yaptığında, başvurunun sınıfa veya yapıya ya da bir varsayılan özelliğe erişim izni verip etmediği kesin olamaz. Bu, derleyici hatalarına veya hafif çalışma zamanı mantığı hatalarına neden olabilir.  
  
 Derleyici türü denetimini `On`olarak ayarlamak için, her zaman [katı bildiri seçeneğini](../../../../visual-basic/language-reference/statements/option-strict-statement.md) kullanarak varsayılan özellik hatalarının olasılığını azaltabilirsiniz.  
  
 Kodunuzda önceden tanımlanmış bir sınıf veya yapı kullanmayı planlıyorsanız, bunun varsayılan bir özelliği olup olmadığını ve varsa adının ne olduğunu belirlemelisiniz.  
  
 Bu dezavantajlar nedeniyle varsayılan özellikleri tanımlamamalısınız. Kod okunabilirlik için, her zaman tüm özelliklere, hatta varsayılan özelliklere de her zaman başvurmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Default](../../../../visual-basic/language-reference/modifiers/default.md)
- [Visual Basic Özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
