---
description: 'Daha fazla bilgi edinin: Call deyimleri (Visual Basic)'
title: Call Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 70e6c109621c3710ad9476a952e9c384a142ba3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674018"
---
# <a name="call-statement-visual-basic"></a>Call Deyimi (Visual Basic)

Denetimi bir `Function` , `Sub` veya dinamik bağlantı KITAPLıĞı (dll) yordamına aktarır.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Bölümler  

|||
|---|---|
|`procedureName`|Gereklidir. Çağrılacak yordamın adı.|
|`argumentList`|İsteğe bağlı. Çağrıldığında yordama geçirilen bağımsız değişkenleri temsil eden değişkenlerin veya ifadelerin listesi. Birden çok bağımsız değişken virgülle ayrılır. Dahil ederseniz `argumentList` , parantez içine almanız gerekir.|
|||
  
## <a name="remarks"></a>Açıklamalar

 `Call`Bir yordamı çağırdığınızda anahtar sözcüğünü kullanabilirsiniz. Çoğu yordam çağrısı için bu anahtar sözcüğünü kullanmanız gerekmez.

 `Call`Çağrılan ifade bir tanımlayıcı ile başlamaksa, genellikle anahtar sözcüğünü kullanırsınız. `Call`Diğer kullanımlar için anahtar sözcüğünün kullanılması önerilmez.

 Yordam bir değer döndürürse, `Call` ifade onu atar.

## <a name="example"></a>Örnek

 Aşağıdaki kod, `Call` bir yordamı çağırmak için anahtar sözcüğünün gerekli olduğu iki örneği göstermektedir. Her iki örnekte de çağrılan ifade bir tanımlayıcı ile başlamaz.

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Function Deyimi](function-statement.md)
- [Sub Deyimi](sub-statement.md)
- [Declare Deyimi](declare-statement.md)
- [Lambda Ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md)
