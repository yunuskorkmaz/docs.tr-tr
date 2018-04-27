---
title: 'Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cbaaa5ed17845a7ac8847786fb10111c724015ba
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma (Visual Basic)
A `Function` yordamı çağıran kodu için bir değer döndürür. Bu adı ve bağımsız değişkenler dahil ederek Atama ifadesinin veya bir ifade sağ taraftaki ya da çağırın.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Bir ifade işlevi yordamda çağırmak için  
  
1.  Kullanmak `Function` yordamı adı bir değişken kullandığınız aynı gibi. Kullanabileceğiniz bir `Function` yordam çağrısı her yerden kullanabileceğiniz bir değişken veya sabit bir ifade.  
  
2.  Bağımsız değişken listesi kapsamak için parantez yordamı adıyla izleyin. Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz. Ancak, parantez kullanarak kodunuzu okumak kolaylaştırır.  
  
3.  Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin. Bağımsız değişkenleri aynı sırada sağladığınız emin olun, `Function` yordamı ilgili parametreleri tanımlar.  
  
     Alternatif olarak, ada göre bir veya daha fazla bağımsız değişkenler geçirebilirsiniz. Daha fazla bilgi için bkz: [geçirme bağımsız değişkenleri konuma ve ada göre](./passing-arguments-by-position-and-by-name.md).  
  
4.  Bir değişkenin değeri olarak yalnızca ifade yordamdan döndürülen değer katılan veya sabiti gerekir.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Bir işlev yordamı bir atama deyiminde çağırmak için  
  
1.  Kullanım `Function` eşittir aşağıdaki yordam adı (`=`) atama deyiminde oturum açın.  
  
2.  Bağımsız değişken listesi kapsamak için parantez yordamı adıyla izleyin. Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz. Ancak, parantez kullanarak kodunuzu okumak kolaylaştırır.  
  
3.  Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin. Bağımsız değişkenleri aynı sırada sağladığınız emin olun, `Function` yordamı ada göre geçirme sürece ilgili parametreleri tanımlar.  
  
4.  Yordamdan döndürülen değer değişken veya özellik Atama ifadesinin sol tarafında depolanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek Visual Basic çağırır <xref:Microsoft.VisualBasic.Interaction.Environ%2A> bir işletim sistemi ortam değişkeni değeri alınamadı. İlk satırı çağrıları `Environ` satır bir ifade ve saniye içinde bir atama deyiminde çağırır. `Environ` tek bağımsız değişken olarak değişken adını alır. Bu, çağrıyı yapan kod değişkenin değeri döndürür.  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlev Yordamları](./function-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Nasıl yapılır: Bir Yordamdan Değer Döndürme](./how-to-return-a-value-from-a-procedure.md)  
 [Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma](./how-to-call-a-procedure-that-does-not-return-a-value.md)
