---
title: 'İşleç bildirimi şunlardan biri olmalıdır: +,-, *,-,-, ^, &amp; , LIKE, mod, and, or, XOR, Not,  <<,  >>, =,  <>, <, <=, >, >=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: c388b1b0762dd7475ca365a8a62228d0b5d59414
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873608"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a>İşleç bildirimi şunlardan biri olmalıdır: +,-, *, \, /, ^, &amp; , LIKE, mod, and, or, XOR, Not, \<\<, >>...

Yalnızca aşırı yükleme için uygun bir işleç bildirebilirsiniz. Aşağıdaki tabloda, bildirebilmeniz için kullanabileceğiniz işleçler listelenmektedir.  
  
|Tür|İşleçler|  
|----------|---------------|  
|Birli|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|İkili|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Dönüştürme (birli)|`CType`|  
  
 `=`İkili listedeki işlecin atama işleci değil karşılaştırma operatörü olduğunu unutmayın.  
  
 **Hata kimliği:** BC33000  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Fazla yüklenebilir işleçler kümesinden bir işleç seçin.  
  
2. Doğrudan aşırı yükleyemez olmayan bir işleci aşırı yükleme işlevselliğine ihtiyacınız varsa, `Function` uygun parametreleri alan ve uygun değeri döndüren bir yordam oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Operator Deyimi](../statements/operator-statement.md)
- [İşleç Yordamları](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Nasıl yapılır: İşleç Tanımlama](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Function Deyimi](../statements/function-statement.md)
