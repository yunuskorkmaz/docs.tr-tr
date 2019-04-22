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
ms.openlocfilehash: 3c63c5613b40cb2014c77a0a996e3acb2cc304d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817025"
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
 İsteğe bağlı. Dahil etmek istediğiniz herhangi bir yorum metni. Bir arasında gerekli bir alandır `REM` anahtar sözcüğü ve `comment`.  
  
## <a name="remarks"></a>Açıklamalar  
 Koyabilirsiniz bir `REM` bir satır veya, tek başına bildirimi, başka bir deyiminin sonrasındaki bir satıra koyabilir. `REM` Deyimi bir satırdaki son deyim olmalıdır. Başka bir ifade izliyorsa `REM` bu deyiminden boşluk tarafından ayrılmış olması gerekir.  
  
 Tek tırnak işareti kullanabilirsiniz (`'`) yerine `REM`. Bu, açıklamanızı aynı satırda başka bir ifade izleyen veya tek başına bir satırda yer alan geçerlidir.  
  
> [!NOTE]
>  Devam edemiyor bir `REM` satır devamlılığı sırası kullanarak deyimi (`_`). Bir yorum başladıktan sonra derleyici karakterler için özel bir anlamı incelemez. İçin birden çok satır yorum, başka kullanma `REM` deyimi veya bir yorum sembolü (`'`) her satırda.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterilmiştir `REM` deyimi bir programda açıklayıcı açıklamalar eklemek için kullanılır. Ayrıca, tek tırnak işareti karakteri kullanarak alternatif gösterir (`'`) yerine `REM`.  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Code’daki Açıklamalar](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
