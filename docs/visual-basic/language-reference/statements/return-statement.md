---
title: Return Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b66d16a249164b8989f05f10c785b97055bfde9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Get deyimi](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set deyimi](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Try... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
