---
title: Call Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 2074f44aedf59f1570e73c898a9bf64e57034923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603398"
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
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
