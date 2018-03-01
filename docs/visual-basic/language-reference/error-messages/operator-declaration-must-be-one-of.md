---
title: "İşleç bildirimi şunlardan biri olmalıdır: +,-, *,-, -, ^, &amp;, Like, Mod ve, Or, Xor, değil, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;= &gt; , &gt;=, CType, IsTrue, IsFalse"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80c8358dd13105c18e73e94735a51b02d5bd22c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [İşleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Nasıl yapılır: bir işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Nasıl yapılır: bir dönüşüm işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
