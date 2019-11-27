---
title: Return Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: efc85a3a844898345aa2d16926ba0e35d7346d1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333009"
---
# <a name="return-statement-visual-basic"></a>Return Deyimi (Visual Basic)
`Function`, `Sub`, `Get`, `Set`veya `Operator` yordamı çağıran koda denetim döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a>Bölümüyle  
 `expression`  
 `Function`, `Get`veya `Operator` yordamında gereklidir. Çağırma koduna döndürülecek değeri temsil eden ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `Sub` veya `Set` yordamında `Return`, bir `Exit Sub` veya `Exit Property` ifadesiyle eşdeğerdir ve `expression` sağlanmamalıdır.  
  
 `Function`, `Get`veya `Operator` yordamında, `Return` deyimin `expression`içermesi gerekir ve `expression` yordamın dönüş türüne dönüştürülebilir bir veri türü olarak değerlendirilmelidir. Bir `Function` veya `Get` yordamında, dönüş değeri olarak kullanılacak yordam adına bir ifade atama ve sonra bir `Exit Function` ya da `Exit Property` deyimi yürütme alternatifi de vardır. `Operator` yordamında `Return expression`kullanmanız gerekir.  
  
 Aynı yordamda uygun olan çok sayıda `Return` deyimi ekleyebilirsiniz.  
  
> [!NOTE]
> Bir `Finally` bloğundaki kod, bir `Try` `Return` deyimden sonra çalışır, ancak bu `Return` deyimin yürütmeden önce `Catch` bloğunda. Bir `Return` deyimleri, bir `Finally` bloğuna dahil edilemez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yordamı başka bir şey yapmak zorunda olmadığında çağırma koduna geri dönmek için `Return` ifadesini birkaç kez kullanır.  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Get Deyimi](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set Deyimi](../../../visual-basic/language-reference/statements/set-statement.md)
- [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
