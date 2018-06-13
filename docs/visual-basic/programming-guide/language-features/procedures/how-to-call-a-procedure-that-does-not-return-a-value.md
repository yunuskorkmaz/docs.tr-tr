---
title: 'Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: cf136f1486645d6e8e4b5856c0b1baf9e99f6c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649054"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma (Visual Basic)
A `Sub` yordamı çağıran kodu için bir değer döndürmez. Siz açıkça tek başına bir arama deyimiyle çağrısından. Bu deyim içinde adı kullanılarak çağrılamaz.  
  
### <a name="to-call-a-sub-procedure"></a>Bir alt yordam çağrısı için  
  
1.  Adını belirtin `Sub` yordamı.  
  
2.  Bağımsız değişken listesi kapsamak için parantez yordamı adıyla izleyin. Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz. Ancak, parantez kullanarak kodunuzu okumak kolaylaştırır.  
  
3.  Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin. Bağımsız değişkenleri aynı sırada sağladığınız emin olun, `Sub` yordamı ilgili parametreleri tanımlar.  
  
     Aşağıdaki örnek Visual Basic çağırır <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> bir uygulama penceresi etkinleştirmek için işlevi. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> pencere başlığı tek bağımsız değişken olarak alır. Çağrıyı yapan kod için bir değer döndürmüyor. Not Defteri işlemi çalışmıyor, örnek döndürürse bir <xref:System.ArgumentException>. `Shell` Yordam varsayar uygulamalardır belirtilen yollar.  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [Yordamlar](./index.md)  
 [Alt Yordamlar](./sub-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Nasıl yapılır: Yordam Oluşturma](./how-to-create-a-procedure.md)  
 [Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma](./how-to-call-a-procedure-that-returns-a-value.md)  
 [Nasıl yapılır: Visual Basic'te bir olay işleyicisi çağırma](./how-to-call-an-event-handler.md)
