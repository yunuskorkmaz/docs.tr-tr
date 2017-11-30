---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c192cdb4ac43ad614fbfb663079c03ddc6c358c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Bağımsız değişken çağrılan yordamı veya özellik çağıran kodu değişkeninde temel bir değişkenin değerini değiştiremezsiniz şekilde geçirilir belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `ByVal` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanımını gösteren `ByVal` parametre bir başvuru türü bağımsız değişkeniyle mekanizması geçirme. Örnekte, bağımsız değişken değer `c1`, sınıfının bir örneği `Class1`. `ByVal`başvuru bağımsız değişkeni, temel alınan değeri değiştirmelerini yordamları kodda `c1`, erişilebilir alanlarını ve özelliklerini korumaz ancak `c1`.  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Bağımsız değişkenleri değere ve başvuruya göre geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
