---
title: 'İşleç bildirimi şunlardan biri olmalıdır: +,-, *,-, -, ^, &amp;, Like, Mod ve, Or, Xor, Not, <<>>,, <> =, <, < =, >, > =, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 7acec56be60f88147bac1ba4179ad0234ea1c6e1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270062"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a>İşleç bildirimi şunlardan biri olmalıdır: +,-, *,\,/, ^, &amp;, Like, Mod ve, Or, Xor, Not, \< \<, >>...
Aşırı yükleme için uygun olan bir işleç bildirebilirsiniz. Aşağıdaki tabloda bildirebilirsiniz işleçleri listelenir.  
  
|Tür|İşleçler|  
|----------|---------------|  
|Birli|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|İkili|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Dönüştürme (tekli)|`CType`|  
  
 Unutmayın `=` işlecidir ikili listesinde karşılaştırma işleci atama işleci.  
  
 **Hata Kimliği:** BC33000  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Fazla yüklenebilir işleçler kümesinden bir işleç seçin.  
  
2.  Doğrudan aşırı yüklenemez operatör aşırı yüklemesi işlevselliğini gerekiyorsa, oluşturun bir `Function` uygun parametreleri alır ve uygun bir değer döndüren yordam.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)
- [İşleç Yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Nasıl yapılır: Bir işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Nasıl yapılır: Bir dönüşüm işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
