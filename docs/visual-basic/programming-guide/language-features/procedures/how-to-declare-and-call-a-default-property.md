---
title: "Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın"
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
ms.openlocfilehash: ca282acbe6831f2189d83faa2f83d32d420d9b53
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640972"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın
A *varsayılan özellik* kodunuzun bu belirtmeden erişeceği sınıfın veya yapının bir özelliktir. Kodu adları çağrılırken bir sınıf veya yapı ancak değil bir özellik ve bağlamı bir özellik erişim sağlar, varsa, Visual Basic erişim o sınıfın veya yapının varsayılan özellik giderir.  
  
 Bir sınıf veya yapı, en fazla bir varsayılan özelliğine sahip olabilir. Ancak, varsayılan bir özelliği aşırı yükleme ve birden fazla sürümüne sahip.  
  
 Daha fazla bilgi için [varsayılan](../../../../visual-basic/language-reference/modifiers/default.md).  
  
### <a name="to-declare-a-default-property"></a>Varsayılan bir özelliği bildirme  
  
1.  Özelliği, normal bir şekilde bildirin. Belirtmeyin `Shared` veya `Private` anahtar sözcüğü.  
  
2.  Dahil `Default` özelliği bildirimindeki anahtar sözcüğü.  
  
3.  Bir özellik için en az bir parametre belirtin. En az bir bağımsız değişken almaz ve varsayılan bir özellik tanımlanamaz.  
  
     [!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a>Varsayılan özellik çağırmak için  
  
1.  Bir değişken içeren bir sınıf veya yapı türü bildirin.  
  
     [!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  Değişken adı bir ifadede tek başına, özellik adı burada normalde verilebilir kullanın.  
  
     [!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  Değişken adı parantez içinde bir bağımsız değişken listesiyle izleyin. Varsayılan özellik en az bir bağımsız değişken almalıdır.  
  
     [!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  Varsayılan özellik değerini almak için bir bağımsız değişken listesiyle bir ifadede veya eşittir değişken adını kullanın (`=`) bir atama ifadesinde oturum açın.  
  
     [!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  Varsayılan özellik değerini ayarlamak için değişken adı, atama deyiminin sol tarafında bir bağımsız değişken listesiyle kullanın.  
  
     [!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  Yalnızca diğer herhangi bir özelliğe erişmek için yaptığınız gibi her zaman varsayılan özellik adı değişken adı ile birlikte belirtebilirsiniz.  
  
     [!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sınıf üzerinde varsayılan bir özelliği bildirir.  
  
 [!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan özellik nasıl çağırılacağını `myProperty` sınıfında `class1`. Üç atama deyimleri değerleri depolamak `myProperty`ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> çağrı değerlerini okur.  
  
 [!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 Varsayılan özellik en yaygın kullanımı <xref:Microsoft.VisualBasic.Collection.Item%2A> çeşitli koleksiyon sınıflarını özelliği.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Varsayılan Özellikler kaynak kod-harfler küçük azalmasına neden olabilir, ancak bunlar kodunuzu okunacak daha zor hale getirebilir. Bir sınıf veya yapı adı başvuru yaptığında çağıran kod, sınıf veya yapı, birlikte bilinen değilse, bu başvuruyu sınıf veya yapının kendisi veya varsayılan bir özellik olup erişen belirli olamaz. Bu, derleyici hataları veya Zarif çalışma zamanı mantık hataları neden olabilir.  
  
 Her zaman kullanarak biraz varsayılan özellik hata olasılığını azaltabilirsiniz [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) derleyici tür denetlemesini ayarlanacak `On`.  
  
 Bir önceden tanımlanmış sınıf veya yapı kodunuzda belirlemeniz gerekir, varsayılan bir özellik sahip olup olmadığını ve bu durumda kullanmayı planlıyorsanız, onun adı nedir?  
  
 Bu dezavantajların nedeniyle varsayılan özellikleri tanımlamaya değil dikkate almalısınız. Kod okunabilirlik açısından, ayrıca her zaman tüm özelliklere açıkça başvuran göz önünde bulundurun, hatta özellikleri varsayılan.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Default](../../../../visual-basic/language-reference/modifiers/default.md)
- [Visual Basic'de özellikler ile değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bir özellik yordamı çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Bir özelliğe değer ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir özellikten değer alma](./how-to-get-a-value-from-a-property.md)
