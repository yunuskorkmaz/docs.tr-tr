---
title: 'Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 7f5d46babf31ea3c6babb29c0f1c08a23e51d598
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340736"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma (Visual Basic)
`Function` yordam, çağıran koda bir değer döndürür. Bunun adını ve bağımsız değişkenlerini atama deyiminin sağ tarafına veya bir ifadeye ekleyerek çağırabilirsiniz.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Bir ifade içindeki bir Işlev yordamını çağırmak için  
  
1. `Function` yordam adını, bir değişkeni kullandığınız şekilde kullanın. Bir deyimde değişken veya sabit kullanabileceğiniz her yerde `Function` yordam çağrısı kullanabilirsiniz.  
  
2. Bağımsız değişken listesini çevrelemek için, parantez ile yordam adını izleyin. Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz. Ancak, parantezleri kullanmak kodunuzun okunmasını kolaylaştırır.  
  
3. Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin. Bağımsız değişkenleri `Function` yordamının ilgili parametreleri tanımladığı sırayla girdiğinizden emin olun.  
  
     Alternatif olarak, bir veya daha fazla bağımsız değişkeni ada göre geçirebilirsiniz. Daha fazla bilgi için bkz. [bağımsız değişkenleri konuma ve ada göre geçirme](./passing-arguments-by-position-and-by-name.md).  
  
4. Yordamdan döndürülen değer, bir değişkenin veya sabitin değeri gibi ifadeye katılır.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Atama deyimindeki bir Işlev yordamını çağırmak için  
  
1. Atama deyimindeki eşittir (`=`) işaretinden sonra `Function` yordam adını kullanın.  
  
2. Bağımsız değişken listesini çevrelemek için, parantez ile yordam adını izleyin. Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz. Ancak, parantezleri kullanmak kodunuzun okunmasını kolaylaştırır.  
  
3. Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin. Bağımsız değişkenleri, `Function` yordamının, ilgili parametreleri ada göre geçirmediğiniz takdirde aynı sırada girdiğinizden emin olun.  
  
4. Yordamdan döndürülen değer, atama ifadesinin sol tarafındaki değişken veya özellikte saklanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir işletim sistemi ortam değişkeninin değerini almak için Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> çağırır. İlk satır bir ifade içinde `Environ` çağırır ve ikinci satır onu bir atama deyiminde çağırır. `Environ` değişken adını tek bağımsız değişkeni olarak alır. Bu, değişkenin değerini çağıran koda döndürür.  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlev Yordamları](./function-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)
- [Nasıl yapılır: Bir Yordamdan Değer Döndürme](./how-to-return-a-value-from-a-procedure.md)
- [Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma](./how-to-call-a-procedure-that-does-not-return-a-value.md)
