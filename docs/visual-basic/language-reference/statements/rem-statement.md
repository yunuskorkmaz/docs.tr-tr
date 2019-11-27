---
title: REM Deyimi
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
ms.openlocfilehash: bdde4beae242c3175b02cd2af252babb850416f6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346725"
---
# <a name="rem-statement-visual-basic"></a>REM Deyimi (Visual Basic)
Bir programın kaynak kodunda açıklayıcı açıklamalar eklemek için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Bölümler  
 `comment`  
 İsteğe bağlı. Dahil etmek istediğiniz açıklamanın metni. `REM` anahtar sözcüğü ve `comment`arasında bir boşluk olması gerekir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `REM` ifadesini tek başına bir satıra koyabilirsiniz ya da başka bir deyimden sonraki bir satıra koyabilirsiniz. `REM` deyimin satırdaki son ifade olması gerekir. Başka bir deyimden sonra `REM`, bu deyimden bir boşluk ile ayrılmalıdır.  
  
 `REM`yerine tek tırnak işareti (`'`) kullanabilirsiniz. Bu, yorumunuz aynı satırdaki başka bir deyime veya bir satırda tek başına oturduğunda geçerlidir.  
  
> [!NOTE]
> Bir satır devamlılık sırası (`_`) kullanarak `REM` bildirimine devam edemezsiniz. Bir yorum başladıktan sonra derleyici, özel anlam için karakterleri denetlemez. Birden çok satırlık bir açıklama için, her satırda başka bir `REM` ifadesini veya bir açıklama sembolünü (`'`) kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir programda açıklayıcı açıklamaları dahil etmek için kullanılan `REM` ifadesini gösterir. Ayrıca, `REM`yerine tek tırnak işareti karakteri (`'`) kullanmanın alternatifini gösterir.  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kod Açıklamaları](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
