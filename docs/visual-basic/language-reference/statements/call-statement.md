---
title: Call Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72450fd6f931f36f640d3e384a6fd38d57a7a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="call-statement-visual-basic"></a>Call Deyimi (Visual Basic)
Aktarır denetlemek için bir `Function`, `Sub`, veya dinamik bağlantı kitaplığı (DLL) yordamı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Bölümler  
 `procedureName`  
 Gerekli. Çağrılacak yordamın adı.  
  
 `argumentList`  
 İsteğe bağlı. Değişkenleri ya da çağrıldığında yordamına geçirilen bağımsız değişkenlerini temsil eden ifadeleri listesi. Birden çok bağımsız değişkenleri virgülle ayrılır. Dahil ederseniz `argumentList`, parantez içine almanız gerekir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Call` bir yordam çağırdığınızda anahtar sözcüğü. Yordam çağrıları için bu anahtar sözcük kullanmak için gerekli değildir.  
  
 Tipik olarak kullandığınız `Call` çağrılan ifadesi bir tanımlayıcı ile başlatılamadığında anahtar sözcüğü. Kullanımı `Call` anahtar sözcüğü diğer kullanımlar için önerilmez.  
  
 Yordam bir değer döndürürse `Call` deyimi atar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod iki örnek gösterir nerede `Call` bir yordam çağrısı anahtar sözcüğü gereklidir. Her iki örneklerde, çağrılan ifadesi bir tanımlayıcı ile başlamıyor.  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
