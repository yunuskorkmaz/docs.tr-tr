---
title: "Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bbea50132d1110b38bf9b01397795a2cd51f86d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma (Visual Basic)
A `Sub` yordamı çağıran kodu için bir değer döndürmez. Siz açıkça tek başına bir arama deyimiyle çağrısından. Bu deyim içinde adı kullanılarak çağrılamaz.  
  
### <a name="to-call-a-sub-procedure"></a>Bir alt yordam çağrısı için  
  
1.  Adını belirtin `Sub` yordamı.  
  
2.  Bağımsız değişken listesi kapsamak için parantez yordamı adıyla izleyin. Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz. Ancak, parantez kullanarak kodunuzu okumak kolaylaştırır.  
  
3.  Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin. Bağımsız değişkenleri aynı sırada sağladığınız emin olun, `Sub` yordamı ilgili parametreleri tanımlar.  
  
     Aşağıdaki örnek çağrıları [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> bir uygulama penceresi etkinleştirmek için işlevi. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>pencere başlığı tek bağımsız değişken olarak alır. Çağrıyı yapan kod için bir değer döndürmüyor. Not Defteri işlemi çalışmıyor, örnek döndürürse bir <xref:System.ArgumentException>. `Shell` Yordam varsayar uygulamalardır belirtilen yollar.  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [Yordamları](./index.md)  
 [Alt yordamlar](./sub-procedures.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Nasıl yapılır: bir yordam oluşturma](./how-to-create-a-procedure.md)  
 [Nasıl yapılır: değer döndüren bir yordam çağırma](./how-to-call-a-procedure-that-returns-a-value.md)  
 [Nasıl yapılır: Visual Basic'te bir olay işleyicisi çağırma](./how-to-call-an-event-handler.md)
