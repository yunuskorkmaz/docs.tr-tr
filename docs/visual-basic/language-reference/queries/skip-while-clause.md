---
title: "Skip While Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f447a6d9b2eb58fa546ced6c96b987caf68fb3e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="skip-while-clause-visual-basic"></a>Skip While Tümcesi (Visual Basic)
Belirtilen bir koşul olduğu sürece bir koleksiyondaki öğelerin atlar `true` ve kalan öğeleri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gerekli. Öğeleri için test etmek için bir koşul temsil eden bir ifade. İfade döndürmelidir bir `Boolean` değeri veya işlevsel bir eşdeğer gibi bir `Integer` olarak değerlendirilecek bir `Boolean`.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Skip While` Yan tümcesi atlar sağlanan kadar bir sorgu sonucunun başından öğeleri `expression` döndürür `false`. Sonra `expression` döndürür `false`, kalan tüm öğeleri sorgu döndürür. `expression` İçin kalan sonuçları göz ardı edilir.  
  
 `Skip While` Yan tümcesini farklı olarak `Where` yan tümcesinde, `Where` yan tümcesi, belirli bir koşula karşılamayan bir sorgudan tüm öğeleri dışlamak için kullanılabilir. `Skip While` Yan tümcesi koşula uyulmadığını yalnızca ilk kez kadar öğeleri dışlar. `Skip While` Sıralı sorgu sonucu ile çalışırken yan tümcesi en kullanışlıdır.  
  
 Kullanarak bir sorgu sonucunun sonuçları başlangıçtan itibaren belirli sayıda atlayabilir `Skip` yan tümcesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Skip While` Amerika Birleşik Devletleri ilk müşteriden bulunana kadar sonuçları atlamak için yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorguları](../../../visual-basic/language-reference/queries/queries.md)  
 [Select tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From yan tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Skip tümcesi](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take While tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Burada yan tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
