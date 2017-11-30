---
title: "Nasıl yapılır: Bir Yordamdan Değer Döndürme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ce7aa0942be413986cb010963753447ea18cdf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Nasıl yapılır: Bir Yordamdan Değer Döndürme (Visual Basic)
A `Function` yordamı değeri döndürür çağıran kodu çalıştırarak ya da bir `Return` deyimi veya karşılaşmadan bir `Exit Function` veya `End Function` deyimi.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Return deyimi kullanarak bir değer döndürmek için  
  
1.  PUT bir `Return` yordam görev tamamlandı burada noktada deyimi.  
  
2.  İzleyin `Return` dönüş çağıran kodu istediğiniz anahtar sözcüğü ile değer döndüren bir ifade.  
  
3.  Birden fazla sahip `Return` aynı yordamı deyiminde.  
  
     Aşağıdaki `Function` yordamı uzun yan veya sağ üçgen hipotenüsü hesaplar ve arama kodu döndürür.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     Aşağıdaki örnek tipik bir çağrı gösterilmektedir `hypotenuse`, döndürülen değer depolar.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Exit işlevi veya End işlevi kullanarak bir değer döndürmek için  
  
1.  En az bir yerinde `Function` yordamı, Ata bir değer yordamın adı.  
  
2.  Çalıştırdığınızda bir `Exit Function` veya `End Function` deyimi, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] en son yordam adına atanmış bir değer döndürür.  
  
3.  Birden fazla sahip `Exit Function` aynı yordamı ve deyiminde karışık `Return` ve `Exit Function` aynı yordamı deyimlerinde.  
  
4.  Yalnızca bir bulunabilir `End Function` deyiminde bir `Function` yordamı.  
  
     Daha fazla bilgi ve bir örnek için "Dönüş değeri" bölümüne bakın [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Alt yordamlar](./sub-procedures.md)  
 [Özellik yordamları](./property-procedures.md)  
 [İşleç yordamları](./operator-procedures.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Return deyimi](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [Nasıl yapılır: değer döndüren bir yordam oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Nasıl yapılır: değer döndüren bir yordam çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
