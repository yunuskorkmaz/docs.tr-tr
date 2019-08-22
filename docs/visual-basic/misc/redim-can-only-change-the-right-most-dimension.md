---
title: "' ReDim ' yalnızca en sağdaki boyutu değiştirebilir"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: f38bcb99b682ace497859b67fe3bb829bbc80c4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664415"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>' ReDim ' yalnızca en sağdaki boyutu değiştirebilir
Bir `ReDim` ifade, son boyut olmayan `Preserve` bir dizinin boyutunu değiştirmek için anahtar sözcüğünü kullanmayı denedi. Kullanırken `Preserve`, yalnızca bir dizinin en son boyutunu yeniden boyutlandırabilirsiniz. Diğer tüm boyutlar için, var olan dizi için aynı boyutu belirtmeniz gerekir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `Preserve` Anahtar sözcüğünü kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'te Diziler](../programming-guide/language-features/arrays/index.md)
- [Visual Basic dizi boyutları](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim Deyimi](../../visual-basic/language-reference/statements/redim-statement.md)
- [Dim Deyimi](../../visual-basic/language-reference/statements/dim-statement.md)
