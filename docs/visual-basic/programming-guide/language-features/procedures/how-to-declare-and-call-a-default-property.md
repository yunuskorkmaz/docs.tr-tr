---
title: "Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8baa03e37325a6ad7065ec1a60052b3ea6a46c6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma
A *varsayılan özellik* kodunuzu belirtme olmadan erişebileceği bir sınıf veya yapı özelliğidir. Kodu çağırma bir sınıf veya yapı ancak bir özellik adları ve bağlam bir özelliğine erişim verir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] varsa, bu sınıf veya yapısı varsayılan özellik erişim giderir.  
  
 En çok bir sınıf veya yapı bir varsayılan özelliğine sahip olabilir. Ancak, varsayılan bir özellik aşırı yükleme ve birden fazla sürümüne sahip olmalıdır.  
  
 Daha fazla bilgi için bkz: [varsayılan](../../../../visual-basic/language-reference/modifiers/default.md).  
  
### <a name="to-declare-a-default-property"></a>Varsayılan bir özellik bildirmek için  
  
1.  Özellik normal şekilde bildirin. Belirtmeyin `Shared` veya `Private` anahtar sözcüğü.  
  
2.  Dahil `Default` özellik bildirimi anahtar sözcük.  
  
3.  Özelliği için en az bir parametre belirtin. En az bir bağımsız değişken almaz ve varsayılan bir özellik tanımlanamaz.  
  
     [!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a>Varsayılan bir özellik çağırmak için  
  
1.  İçeren sınıf veya yapı türünde bir değişken bildirin.  
  
     [!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  Burada normal olarak özellik adını içerir bir ifadede tek başına değişken adını kullanın.  
  
     [!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  Bir bağımsız değişken listesi parantez içinde değişken adıyla izleyin. Varsayılan bir özellik en az bir değişken almanız gerekir.  
  
     [!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  Varsayılan özellik değerini almak için bir bağımsız değişken listesiyle bir ifadede ya da eşit aşağıdaki değişken adını kullanın (`=`) bir atama deyiminde oturum açın.  
  
     [!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  Varsayılan özellik değerini ayarlamak için bir atama deyimi sol tarafındaki bir bağımsız değişken listesiyle değişken adını kullanın.  
  
     [!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  Yalnızca diğer herhangi bir özelliğe erişmek için yaptığınız gibi her zaman varsayılan özellik adı değişken adı ile birlikte belirtebilirsiniz.  
  
     [!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sınıf üzerinde varsayılan bir özellik bildirir.  
  
 [!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek varsayılan özellik nasıl çağırılacağını `myProperty` sınıfındaki `class1`. Üç atama deyimleri değerlerini depolamak `myProperty`ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> çağrısı değerleri okur.  
  
 [!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 Varsayılan bir özellik en yaygın kullanımı <xref:Microsoft.VisualBasic.Collection.Item%2A> çeşitli koleksiyon sınıfları özelliği.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Varsayılan Özellikler kaynak kod-karakterlerini küçük azalmasına neden olabilir, ancak bunlar kodunuzu okumak daha zor hale getirebilir. Sınıf veya yapı adı için bir başvuru yaptığında, çağrıyı yapan kod, sınıf veya yapı, bilinen değilse, bu başvuru sınıf veya yapı kendisini veya varsayılan bir özellik mi erişen belirli olamaz. Bu derleyici hataları veya Zarif çalışma zamanı mantık hataları neden olabilir.  
  
 Her zaman kullanarak varsayılan özellik hataları olasılığını biraz azaltabilir [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) denetlemesini derleyici türünü ayarlamak için `On`.  
  
 Önceden tanımlanmış sınıf veya yapı kodunuzda belirlemeniz gerekir varsayılan bir özellik olup olmadığını ve bu durumda kullanmayı planlıyorsanız, ne adıdır.  
  
 Bu olumsuzlukları nedeniyle varsayılan özellikleri tanımlamaya değil göz önünde bulundurmalısınız. Kod okunabilirlik için ayrıca her zaman tüm özelliklerini açıkça başvuran göz önünde bulundurun, hatta özellikleri varsayılan.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellik yordamları](./property-procedures.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Varsayılan](../../../../visual-basic/language-reference/modifiers/default.md)  
 [Visual Basic'de özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)  
 [Nasıl yapılır: özellik oluşturma](./how-to-create-a-property.md)  
 [Nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Nasıl yapılır: bir özellik yordamı çağırma](./how-to-call-a-property-procedure.md)  
 [Nasıl yapılır: bir özelliğe değer ekleme](./how-to-put-a-value-in-a-property.md)  
 [Nasıl yapılır: bir özellikten değer alma](./how-to-get-a-value-from-a-property.md)
