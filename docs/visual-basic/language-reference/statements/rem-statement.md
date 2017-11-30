---
title: REM Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d64ce970e3e74437f5e8c63c8a4d578900902192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="rem-statement-visual-basic"></a>REM Deyimi (Visual Basic)
Bir program kaynak kodunda açıklayıcı açıklamalar eklemek için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Bölümler  
 `comment`  
 İsteğe bağlı. Eklemek istediğiniz her türlü açıklamanın metin. Bir arasında gerekli bir alandır `REM` anahtar sözcüğü ve `comment`.  
  
## <a name="remarks"></a>Açıklamalar  
 Koyabilirsiniz bir `REM` deyimi bir satır veya, tek başına, başka bir deyiminden bir satıra koyabilir. `REM` Deyimi satırındaki son deyim olmalıdır. Başka bir ifade izliyorsa `REM` bu deyim bir boşlukla ayrılmalıdır.  
  
 Tek tırnak işareti kullanın (`'`) yerine `REM`. Bu, açıklamanızı aynı satırda başka bir ifade izleyen veya tek başına bir satıra bulunur geçerlidir.  
  
> [!NOTE]
>  Devam edilemiyor bir `REM` satır devamlılığı sırası kullanarak deyimi (`_`). Bir yorum başladıktan sonra derleyici özel bir anlamı karakter inceleyin değil. Birden çok satırlı açıklaması için başka kullanma `REM` deyimi veya açıklama simgesini (`'`) her satırda.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek gösterilmektedir `REM` bir programda açıklayıcı açıklamalar dahil etmek için kullanılan ifade. Ayrıca tek tırnak işareti karakteri kullanmanın alternatif gösterir (`'`) yerine `REM`.  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod açıklamaları](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [Nasıl yapılır: kodda deyimleri bölme ve birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
