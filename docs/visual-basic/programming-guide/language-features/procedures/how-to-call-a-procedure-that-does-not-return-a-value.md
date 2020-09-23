---
title: 'Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 2686a4d9dc10cde209f558771feeb5ba4f4ccb21
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075011"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma (Visual Basic)

`Sub`Yordam, çağırma koduna bir değer döndürmez. Bunu tek başına çağırma ifadesiyle açıkça çağırabilirsiniz. Bunu yalnızca bir ifade içinde adını kullanarak çağrılamaz.  
  
### <a name="to-call-a-sub-procedure"></a>Bir alt yordamı çağırmak için  
  
1. Yordamın adını belirtin `Sub` .  
  
2. Bağımsız değişken listesini çevrelemek için, parantez ile yordam adını izleyin. Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz. Ancak, parantezleri kullanmak kodunuzun okunmasını kolaylaştırır.  
  
3. Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin. Bağımsız değişkenleri `Sub` yordamın ilgili parametreleri tanımladığı sırada girdiğinizden emin olun.  
  
     Aşağıdaki örnek, <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> bir uygulama penceresini etkinleştirmek için Visual Basic işlevini çağırır. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> pencere başlığını tek bağımsız değişkeni olarak alır. Çağıran koda bir değer döndürmez. Bir not defteri işlemi çalışmıyorsa, örnek bir oluşturur <xref:System.ArgumentException> . `Shell`Yordam, uygulamaların belirtilen yollarda olduğunu varsayar.  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Sub Deyimi](../../../language-reference/statements/sub-statement.md)
- [Nasıl yapılır: Yordam Oluşturma](./how-to-create-a-procedure.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
- [Nasıl yapılır: Olay İşleyicisi Çağırma (Visual Basic)](./how-to-call-an-event-handler.md)
