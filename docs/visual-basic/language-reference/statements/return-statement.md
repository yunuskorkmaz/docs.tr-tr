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
ms.openlocfilehash: 2f614045be1b91b9c747d961cdefd526ba1bab98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="return-statement-visual-basic"></a>Return Deyimi (Visual Basic)
Denetim adlı kodu döndürür bir `Function`, `Sub`, `Get`, `Set`, veya `Operator` yordamı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Bölümü  
 `expression`  
 Gerekli bir `Function`, `Get`, veya `Operator` yordamı. Çağrıyı yapan kod döndürülecek değer temsil eden ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 İçinde bir `Sub` veya `Set` yordamı, `Return` açıklamadır eşdeğer bir `Exit Sub` veya `Exit Property` deyimi, ve `expression` sağlanmadı gerekir.  
  
 İçinde bir `Function`, `Get`, veya `Operator` yordamı, `Return` deyimi içermelidir `expression`, ve `expression` yordamı dönüş türüne dönüştürülebilir bir veri türü olarak değerlendirilmelidir. İçinde bir `Function` veya `Get` yordamı, oluşturmuş olmanız da dönüş değeri olarak hizmet vermek için yordam adı bir ifade atamak ve ardından yürütme alternatif bir `Exit Function` veya `Exit Property` deyimi. İçinde bir `Operator` yordamı kullanmalıdır `Return``expression`.  
  
 Kadar içerebilir `Return` deyimleri aynı yordamı uygun olarak.  
  
> [!NOTE]
>  Kodda bir `Finally` blok sonra çalışan bir `Return` deyiminde bir `Try` veya `Catch` blok karşılaşıldı, ancak önce `Return` deyimini yürütür. A `Return` deyimi yer olamaz bir `Finally` bloğu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Return` deyimi yordamı başka bir şey yapmama gerek var çağıran kodu döndürülecek birkaç kez.  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Get Deyimi](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set Deyimi](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
