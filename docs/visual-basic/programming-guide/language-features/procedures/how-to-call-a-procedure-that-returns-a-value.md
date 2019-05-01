---
title: 'Nasıl yapılır: (Visual Basic) bir değer döndüren bir yordam çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 6f45f01489ee84b6addb1f7c7c8dc584332f38dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864188"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir değer döndüren bir yordam çağırma
A `Function` yordamın çağrıldığı koda bir değer döndürür. Bu adı ve bağımsız değişkenler dahil ederek işlecin sağ tarafındaki Atama ifadesinin veya bir ifade ya da çağırırsınız.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>İçinde bir ifade bir işlev yordam çağırmak için  
  
1. Kullanma `Function` yordamı kullandığınız bir değişken gibi adlandırın. Kullanabileceğiniz bir `Function` kullanabileceğiniz bir değişken veya sabit bir ifadede herhangi bir yordam çağırma.  
  
2. Parantez içine bağımsız değişken listesi için yordamın adıyla izleyin. Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz. Ancak, parantezler kullanarak kodunuzu okumayı kolaylaştırır.  
  
3. Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin. Bağımsız değişkenler aynı sırada sağladığınız emin olun, `Function` yordamı karşılık gelen parametreleri tanımlar.  
  
     Alternatif olarak, ada göre bir veya daha fazla bağımsız değişken geçirebilirsiniz. Daha fazla bilgi için [geçirmeden bağımsız değişkenleri konuma ve ada göre](./passing-arguments-by-position-and-by-name.md).  
  
4. Yordamdan döndürülen değer, bir değişken değeri olarak yalnızca ifade katıldığı veya sabiti gerekir.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Bir atama ifadesinde bir işlev yordam çağırmak için  
  
1. Kullanım `Function` eşit aşağıdaki yordam adı (`=`) atama ifadesi oturum açın.  
  
2. Parantez içine bağımsız değişken listesi için yordamın adıyla izleyin. Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz. Ancak, parantezler kullanarak kodunuzu okumayı kolaylaştırır.  
  
3. Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin. Bağımsız değişkenler aynı sırada sağladığınız emin olun, `Function` yordamı ada göre geçirme sürece, karşılık gelen parametreleri tanımlar.  
  
4. Yordamdan döndürülen değer değişken veya özellik atama ifadesi sol tarafında depolanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Visual Basic çağırır <xref:Microsoft.VisualBasic.Interaction.Environ%2A> bir işletim sistemi ortam değişkeninin değerini almak için. İlk satırı çağrıları `Environ` satır içinde bir ifade ve ikinci bir atama ifadesinde çağırır. `Environ` değişken adı, tek bir bağımsız değişken olarak alır. Çağrıldığı koda değişken değerini döndürür.  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlev Yordamları](./function-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Nasıl yapılır: Bir değer döndüren bir yordam oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)
- [Nasıl yapılır: Bir yordamdan değer döndürme](./how-to-return-a-value-from-a-procedure.md)
- [Nasıl yapılır: Bir değer döndürmeyen bir yordam çağırma](./how-to-call-a-procedure-that-does-not-return-a-value.md)
