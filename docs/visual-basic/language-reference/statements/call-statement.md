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
ms.openlocfilehash: e706650ac6da84d9b4e77fc549811e731be61b92
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594167"
---
# <a name="call-statement-visual-basic"></a>Call Deyimi (Visual Basic)
Aktarımı denetlemek için bir `Function`, `Sub`, veya dinamik bağlantı kitaplığı (DLL) yordam.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Bölümler  
|||
|---|---|
|`procedureName`|Gerekli. Çağrılacak yordamın adı.|
|`argumentList`|İsteğe bağlı. Değişkenlerin veya onu çağrıldığında yönteme bağımsız değişkenlerini temsil eden ifadelerin listesi. Birden çok bağımsız değişkeni virgülle ayrılır. Eklerseniz `argumentList`, parantez içine almalısınız.|
|||
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Call` bir yordamı çağırdığınızda anahtar sözcüğü. Yordam çağrıları için bu anahtar sözcüğünü kullanmanız gerekmez.  
  
 Tipik olarak kullandığınız `Call` adlı ifade bir tanımlayıcıyla başlatılamadığında anahtar sözcüğü. Kullanım `Call` anahtar sözcüğü diğer kullanımlar için önerilmez.  
  
 Yordamı bir değer döndürürse `Call` deyimi atar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod iki örnek gösterir. burada `Call` bir yordam çağırmak anahtar sözcüğü gereklidir. Örneklerin her ikisi de adlı ifade bir tanımlayıcı ile başlamıyor.  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
