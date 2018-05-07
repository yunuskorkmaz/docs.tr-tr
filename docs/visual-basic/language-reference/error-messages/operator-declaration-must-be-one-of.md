---
title: 'İşleç bildirimi şunlardan biri olmalıdır: +,-, *,-, -, ^, &amp;, Like, Mod ve, Or, Xor, değil, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;= &gt; , &gt;=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: eb1e7e8088ec8661be2469aff043c0f1a96e4d01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a>İşleç bildirimi şunlardan biri olmalıdır: +,-, *,\,/, ^, &amp;, Like, Mod ve, Or, Xor, değil, &lt; &lt;, &gt; &gt;...
Aşırı yükleme için uygun olan bir işleç bildirebilirsiniz. Aşağıdaki tabloda bildirebilirsiniz işleçleri listeler.  
  
|Tür|İşleçler|  
|----------|---------------|  
|Birli|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|İkili|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Dönüştürme (tekli)|`CType`|  
  
 Unutmayın `=` işlecidir ikili listesinde atama işleci karşılaştırma işleci.  
  
 **Hata Kimliği:** BC33000  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Fazla yüklenebilir işleçler kümesinden bir işleç seçin.  
  
2.  Doğrudan tekrar yükleyemez bir işleç aşırı yüklemesi işlevselliğini ihtiyacınız varsa oluşturma bir `Function` uygun parametreleri alır ve uygun değer döndüren bir yordam.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [İşleç Yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Nasıl yapılır: İşleç Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
