---
description: "Daha fazla bilgi edinin: ' ReDim ' yalnızca en sağdaki boyutu değiştirebilir"
title: "' ReDim ' yalnızca en sağdaki boyutu değiştirebilir"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 6816e5b2e9c7c079b78ce53e168f46b337831512
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454696"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>' ReDim ' yalnızca en sağdaki boyutu değiştirebilir

Bir `ReDim` ifade, `Preserve` son boyut olmayan bir dizinin boyutunu değiştirmek için anahtar sözcüğünü kullanmayı denedi. Kullanırken `Preserve` , yalnızca bir dizinin en son boyutunu yeniden boyutlandırabilirsiniz. Diğer tüm boyutlar için, var olan dizi için aynı boyutu belirtmeniz gerekir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `Preserve`Anahtar sözcüğünü kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'te Diziler](../programming-guide/language-features/arrays/index.md)
- [Visual Basic dizi boyutları](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim Deyimi](../language-reference/statements/redim-statement.md)
- [Dim Deyimi](../language-reference/statements/dim-statement.md)
