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
ms.openlocfilehash: fe200add4e29fe4bbe0fdf335dcd94107b8ff1eb
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932598"
---
# <a name="return-statement-visual-basic"></a>Return Deyimi (Visual Basic)
Denetim çağıran koda döndürür bir `Function`, `Sub`, `Get`, `Set`, veya `Operator` yordamı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Bölümü  
 `expression`  
 Gerekli bir `Function`, `Get`, veya `Operator` yordamı. Çağrıldığı koda döndürülecek değeri temsil eden ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 İçinde bir `Sub` veya `Set` yordamı `Return` deyimi, bir `Exit Sub` veya `Exit Property` deyimi ve `expression` belirtilmemelidir.  
  
 İçinde bir `Function`, `Get`, veya `Operator` yordamı `Return` deyimi içermelidir `expression`, ve `expression` yordamın dönüş türüne dönüştürülebilir bir veri türü olarak değerlendirilmesi gerekir. İçinde bir `Function` veya `Get` yordamı,'iniz de alternatif yordam adı, dönüş değeri olarak görev yapacak bir ifade atayarak ve ardından yürütme bir `Exit Function` veya `Exit Property` deyimi. İçinde bir `Operator` yordamı kullanmalıdır `Return expression`.  
  
 Kadar içerebilir `Return` deyimleri aynı yordam içinde uygun şekilde.  
  
> [!NOTE]
>  Kodda bir `Finally` blok sonra çalışan bir `Return` deyiminde bir `Try` veya `Catch` bloğudur karşılaşıldı, ancak önce `Return` deyimi yürütür. A `Return` deyimi eklenemiyor bir `Finally` blok.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Return` deyimi yordamı başka bir şey yapmanız gerekmez, çağıran koda geri dönmek için birkaç kez.  
  
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
