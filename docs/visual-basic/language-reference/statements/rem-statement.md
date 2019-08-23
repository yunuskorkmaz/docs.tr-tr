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
ms.openlocfilehash: 16149ce42e3476cf07a62298f83734fee9ec7253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957766"
---
# <a name="rem-statement-visual-basic"></a>REM Deyimi (Visual Basic)
Bir programın kaynak kodunda açıklayıcı açıklamalar eklemek için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Bölümler  
 `comment`  
 İsteğe bağlı. Dahil etmek istediğiniz açıklamanın metni. `REM` Anahtar sözcüğü ve `comment`arasında bir boşluk gereklidir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `REM` ifadeyi tek başına bir satıra koyabilirsiniz ya da başka bir deyimden sonraki bir satıra koyabilirsiniz. `REM` Deyimin satırdaki son ifade olması gerekir. Başka bir bildirime `REM` uygunsa, bu deyimden bir boşluk ile ayrılması gerekir.  
  
 Yerine tek tırnak işareti (`'`) kullanabilirsiniz. `REM` Bu, yorumunuz aynı satırdaki başka bir deyime veya bir satırda tek başına oturduğunda geçerlidir.  
  
> [!NOTE]
> Bir satır devamlılık `REM` sırası (`_`) kullanarak bir deyime devam edemezsiniz. Bir yorum başladıktan sonra derleyici, özel anlam için karakterleri denetlemez. Birden çok satırlık bir açıklama için, her satırda `REM` başka bir ifade veya bir açıklama`'`simgesi () kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir programa `REM` açıklayıcı açıklamalar eklemek için kullanılan ifadesini gösterir. Ayrıca,`'` `REM`yerine tek tırnak işareti karakteri () kullanmanın alternatifini de gösterir.  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Code’daki Açıklamalar](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
