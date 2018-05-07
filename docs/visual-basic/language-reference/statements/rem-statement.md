---
title: REM Deyimi (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 3bd526b08e1ba3be856e1e823cf8ef49ea9b6c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [Code’daki Açıklamalar](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
