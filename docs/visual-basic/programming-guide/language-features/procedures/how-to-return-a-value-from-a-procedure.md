---
title: 'Nasıl yapılır: Bir Yordamdan Değer Döndürme'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 1371e4ed0ff28f9caf56eabf2a1bb9290edbe75c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346023"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Nasıl yapılır: Bir Yordamdan Değer Döndürme (Visual Basic)
`Function` yordamı, çağırma koduna bir `Return` ifadesiyle veya `Exit Function` ya da `End Function` ifadesiyle karşılaşarak bir değer döndürür.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Return ifadesini kullanarak bir değer döndürmek için  
  
1. Yordamın görevinin tamamlandığı noktaya `Return` bir ifade koyun.  
  
2. Çağırma koduna döndürmek istediğiniz değeri veren bir ifadeyle `Return` anahtar sözcüğünü izleyin.  
  
3. Aynı yordamda birden fazla `Return` deyiminiz olabilir.  
  
     Aşağıdaki `Function` yordam, sağ üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar ve bunu çağıran koda döndürür.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     Aşağıdaki örnek, döndürülen değeri depolayan `hypotenuse`tipik bir çağrısını gösterir.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Çıkış Işlevini veya End Işlevini kullanarak bir değer döndürmek için  
  
1. `Function` yordamında en az bir yerde, yordamın adına bir değer atayın.  
  
2. Bir `Exit Function` veya `End Function` bildirisini çalıştırdığınızda Visual Basic yordamın adına en son atanan değeri döndürür.  
  
3. Aynı yordamda birden fazla `Exit Function` deyimi olabilir ve aynı yordamda `Return` ve `Exit Function` deyimlerini karıştırabilirsiniz.  
  
4. Bir `Function` yordamında yalnızca bir `End Function` deyiminiz olabilir.  
  
     Daha fazla bilgi ve örnek için bkz. [Function deyimindeki](../../../../visual-basic/language-reference/statements/function-statement.md)"dönüş değeri".  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Return Deyimi](../../../../visual-basic/language-reference/statements/return-statement.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
