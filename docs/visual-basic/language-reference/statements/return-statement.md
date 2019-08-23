---
title: Return Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: af49ea95d7f9d01072190ac3ccf6ba2f1041347e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957668"
---
# <a name="return-statement-visual-basic"></a>Return Deyimi (Visual Basic)
`Function`, ,,`Sub`Veya yordamıçağıran`Operator` koda denetim döndürür. `Get` `Set`  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Bölümüyle  
 `expression`  
 `Function` ,`Get`Veya yordamında`Operator` gereklidir. Çağırma koduna döndürülecek değeri temsil eden ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `Sub` Veya yordamında`Set` , ifade`Return` bir veyaifadesiyle`Exit Property` eşdeğerdir ve`expression`sağlanmamalıdır. `Exit Sub`  
  
 Bir `Function`, `Get`veya yordamında`Operator` ,`expression`ifadesinin içermesi gerekir ve`expression` yordamın dönüş türüne dönüştürülebilir bir veri türü olarak değerlendirilmelidir. `Return` Bir `Function` veya `Get` yordamında, dönüş değeri olarak kullanılacak yordam adına bir ifade atama ve sonra bir `Exit Function` veya `Exit Property` deyimini yürütme alternatifine de sahipsiniz. Bir `Operator` yordamda, kullanmanız `Return expression`gerekir.  
  
 Aynı yordamda uygun olan sayıda `Return` deyim dahil edebilirsiniz.  
  
> [!NOTE]
> `Finally` Bir bloktaki kod, bir `Try` veya `Return` `Catch` bloğundaki deyimden sonra çalışır, ancak bu `Return` deyimden önce çalıştırılır. Bir `Return` ifade bir `Finally` bloğa dahil edilemez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yordamı başka `Return` bir şey yapmak zorunda olmadığında çağıran koda dönmek için birkaç kez ifade kullanır.  
  
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
