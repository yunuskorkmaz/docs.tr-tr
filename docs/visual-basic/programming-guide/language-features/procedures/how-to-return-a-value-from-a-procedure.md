---
title: 'Nasıl yapılır: Bir Yordamdan Değer Döndürme'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 917e52b711645fbf94a132216a3fa90b0dfc15b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414330"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Nasıl yapılır: Bir Yordamdan Değer Döndürme (Visual Basic)
`Function`Yordam, çağırma koduna, bir `Return` ifadeyi yürüterek veya bir veya ifadesiyle karşılaşarak bir değer döndürür `Exit Function` `End Function` .  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Return ifadesini kullanarak bir değer döndürmek için  
  
1. `Return`Yordamın görevinin tamamlandığı noktaya bir ifade koyun.  
  
2. `Return`Çağırma koduna döndürmek istediğiniz değeri veren bir ifadeyle anahtar sözcüğünü izleyin.  
  
3. Aynı yordamda birden fazla deyime sahip olabilirsiniz `Return` .  
  
     Aşağıdaki `Function` yordam, sağ üçgenin en uzun tarafını veya hipotenüsü hesaplar ve bunu çağıran koda döndürür.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     Aşağıdaki örnek `hypotenuse` , döndürülen değeri depolayan, için tipik bir çağrısını gösterir.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Çıkış Işlevini veya End Işlevini kullanarak bir değer döndürmek için  
  
1. Yordamda en az bir yerde `Function` , yordamın adına bir değer atayın.  
  
2. Bir `Exit Function` veya `End Function` ifadesini yürüttüğünüzde, Visual Basic yordamın adına en son atanan değeri döndürür.  
  
3. Aynı yordamda birden fazla deyime sahip olabilirsiniz `Exit Function` ve `Return` `Exit Function` aynı yordamda ve deyimlerini karıştırabilirsiniz.  
  
4. Yordamda yalnızca bir `End Function` deyiminiz olabilir `Function` .  
  
     Daha fazla bilgi ve örnek için bkz. [Function deyimindeki](../../../language-reference/statements/function-statement.md)"dönüş değeri".  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Function Deyimi](../../../language-reference/statements/function-statement.md)
- [Return ekstresi](../../../language-reference/statements/return-statement.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
