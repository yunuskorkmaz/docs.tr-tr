---
title: Skip While Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 380372d6aaf8df3050e0ba8606b74eb3834dec67
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972605"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While Tümcesi (Visual Basic)
Belirtilen bir koşulu olduğu sürece bir koleksiyondaki öğeleri atlar `true` ve kalan öğeleri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gerekli. Test etmek için öğeleri için bir koşulu temsil eden bir ifade. İfade döndürmelidir bir `Boolean` değer veya bir işlev eşdeğer gibi bir `Integer` olarak değerlendirilecek bir `Boolean`.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Skip While` Yan tümcesi bir sorgu sonucunun başına sağlanan kadar öğeleri atlar `expression` döndürür `false`. Sonra `expression` döndürür `false`, sorgunun kalan tüm öğeleri döndürür. `expression` Kalan sonuçları göz ardı edilir.  
  
 `Skip While` Yan tümcesi farklıdır `Where` yan tümcesinde, `Where` yan tümcesi, belirli bir koşulu karşılamayan bir sorgudan tüm öğeleri hariç tutmak için kullanılabilir. `Skip While` Yan tümcesi koşulu karşılanmadı yalnızca ilk kez kadar öğeleri hariç tutar. `Skip While` Bir sıralı sorgu sonucu ile çalışırken yan tümcesi en kullanışlı.  
  
 Kullanarak bir sorgu sonucunun baştan sonuçları belirli sayıda atlayabilir `Skip` yan tümcesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Skip While` Amerika Birleşik Devletleri ilk müşteriden bulunana kadar sonuçları atlamak için yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Skip Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take While Yan Tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
