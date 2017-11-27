---
title: "Take While Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c8add6c55bb9353bac3489e68f497cb32785aad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="take-while-clause-visual-basic"></a>Take While Tümcesi (Visual Basic)
Belirtilen bir koşul olduğu sürece bir koleksiyondaki öğeleri içeren `true` ve kalan öğeleri atlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gerekli. Öğeleri için test etmek için bir koşul temsil eden bir ifade. İfade döndürmelidir bir `Boolean` değeri veya işlevsel bir eşdeğer gibi bir `Integer` olarak değerlendirilecek bir `Boolean`.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Take While` Yan tümcesi bir sorgu sonucunun başından öğeleri sağlanan kadar içerir `expression` döndürür `false`. Sonra `expression` döndürür `false`, sorgu tüm kalan öğeleri atlayacaktır. `expression` İçin kalan sonuçları göz ardı edilir.  
  
 `Take While` Yan tümcesini farklı olarak `Where` yan tümcesinde, `Where` yan tümcesi, bir sorgudan belirli bir koşula tüm öğeleri dahil etmek için kullanılabilir. `Take While` Yan tümcesi koşula uyulmadığını yalnızca ilk kez kadar öğeleri içerir. `Take While` Sıralı sorgu sonucu ile çalışırken yan tümcesi en kullanışlıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Take While` siparişler olmadan ilk müşteri bulunana kadar sonuçları almak için yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorguları](../../../visual-basic/language-reference/queries/queries.md)  
 [Select tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From yan tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Take tümcesi](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Burada yan tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
