---
title: 'Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 3a5de98c6edf795a11bd9f0465aa6919f09eebfa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340954"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma (Visual Basic)
`Sub` yordam, çağıran koda bir değer döndürmez. Bunu tek başına çağırma ifadesiyle açıkça çağırabilirsiniz. Bunu yalnızca bir ifade içinde adını kullanarak çağrılamaz.  
  
### <a name="to-call-a-sub-procedure"></a>Bir alt yordamı çağırmak için  
  
1. `Sub` yordamının adını belirtin.  
  
2. Bağımsız değişken listesini çevrelemek için, parantez ile yordam adını izleyin. Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz. Ancak, parantezleri kullanmak kodunuzun okunmasını kolaylaştırır.  
  
3. Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin. Bağımsız değişkenleri `Sub` yordamının ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.  
  
     Aşağıdaki örnek, bir uygulama penceresini etkinleştirmek için Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> işlevini çağırır. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> pencere başlığını tek bağımsız değişkeni olarak alır. Çağıran koda bir değer döndürmez. Bir not defteri işlemi çalışmıyorsa, örnek bir <xref:System.ArgumentException>oluşturur. `Shell` yordam, uygulamaların belirtilen yollarda olduğunu varsayar.  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Nasıl yapılır: Yordam Oluşturma](./how-to-create-a-procedure.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
- [Nasıl yapılır: Visual Basic bir olay Işleyicisini çağırma](./how-to-call-an-event-handler.md)
