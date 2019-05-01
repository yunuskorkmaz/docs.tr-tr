---
title: 'Nasıl yapılır: (Visual Basic) bir değer döndürmeyen bir yordam çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 6e3ce2a184ca5411a6a016929a16bf3d67e669ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864240"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir değer döndürmeyen bir yordam çağırma
A `Sub` yordamın çağrıldığı koda bir değer döndürmüyor. Bunu açıkça çağıran bir tek başına deyimiyle çağırmanız. Bir ifade içinde adını kullanarak çağrılamıyor.  
  
### <a name="to-call-a-sub-procedure"></a>Bir alt yordam çağırmak için  
  
1. Adını `Sub` yordamı.  
  
2. Parantez içine bağımsız değişken listesi için yordamın adıyla izleyin. Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz. Ancak, parantezler kullanarak kodunuzu okumayı kolaylaştırır.  
  
3. Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin. Bağımsız değişkenler aynı sırada sağladığınız emin olun, `Sub` yordamı karşılık gelen parametreleri tanımlar.  
  
     Aşağıdaki örnek, Visual Basic çağırır <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> uygulama penceresini etkinleştirmek için işlevi. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> pencere başlığı tek bağımsız değişken olarak alır. Çağrıldığı koda bir değer döndürmez. Bir not defteri işlemi çalışmıyor, örneği oluşturur. bir <xref:System.ArgumentException>. `Shell` Yordam uygulamalardır belirtilen yolda varsayar.  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Nasıl yapılır: Bir yordam oluşturma](./how-to-create-a-procedure.md)
- [Nasıl yapılır: Bir değer döndüren bir yordam çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
- [Nasıl yapılır: Visual Basic olay işleyicisi çağırma](./how-to-call-an-event-handler.md)
