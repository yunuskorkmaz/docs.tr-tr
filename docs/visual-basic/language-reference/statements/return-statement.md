---
description: 'Daha fazla bilgi edinin: Return deyimleri (Visual Basic)'
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
ms.openlocfilehash: 62086090ede7e634b09d3edc3dc42feb28d15793
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741204"
---
# <a name="return-statement-visual-basic"></a>Return Deyimi (Visual Basic)

,,, `Function` `Sub` `Get` `Set` Veya `Operator` yordamı çağıran koda denetim döndürür.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a>Bölüm  

 `expression`  
 `Function`, `Get` Veya `Operator` yordamında gereklidir. Çağırma koduna döndürülecek değeri temsil eden ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 `Sub`Veya `Set` yordamında, `Return` ifade bir `Exit Sub` veya `Exit Property` ifadesiyle eşdeğerdir ve `expression` sağlanmamalıdır.  
  
 Bir `Function` , `Get` veya yordamında, `Operator` `Return` ifadesinin içermesi gerekir `expression` ve `expression` yordamın dönüş türüne dönüştürülebilir bir veri türü olarak değerlendirilmelidir. Bir `Function` veya `Get` yordamında, dönüş değeri olarak kullanılacak yordam adına bir ifade atama ve sonra bir veya deyimini yürütme alternatifine de sahipsiniz `Exit Function` `Exit Property` . Bir `Operator` yordamda, kullanmanız gerekir `Return expression` .  
  
 `Return`Aynı yordamda uygun olan sayıda deyim dahil edebilirsiniz.  
  
> [!NOTE]
> Bir bloktaki kod, `Finally` `Return` bir veya bloğundaki deyimden sonra çalışır `Try` `Catch` , ancak bu `Return` deyimden önce çalıştırılır. Bir `Return` ifade bir bloğa dahil edilemez `Finally` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Return` yordamı başka bir şey yapmak zorunda olmadığında çağıran koda dönmek için birkaç kez ifade kullanır.  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Function Deyimi](function-statement.md)
- [Sub Deyimi](sub-statement.md)
- [Get Deyimi](get-statement.md)
- [Set deyimleri](set-statement.md)
- [Operator Deyimi](operator-statement.md)
- [Property Deyimi](property-statement.md)
- [Exit Deyimi](exit-statement.md)
- [Try...Catch...Finally Deyimi](try-catch-finally-statement.md)
