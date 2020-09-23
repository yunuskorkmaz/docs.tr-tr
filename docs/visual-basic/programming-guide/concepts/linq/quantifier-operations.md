---
title: Niceleyici İşlemleri
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0c1c69cb36ac16126454dc0c24cd84fc85b0b218
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075310"
---
# <a name="quantifier-operations-visual-basic"></a>Nicelik belirteci Işlemleri (Visual Basic)

Nicelik belirteci işlemleri bir <xref:System.Boolean> dizideki öğelerin bazılarının veya tümünün bir koşulu karşılayıp karşılamadığını belirten bir değer döndürür.  
  
 Aşağıdaki çizimde iki farklı kaynak dizisi üzerinde iki farklı belirleyici işlem gösterilmektedir. İlk işlem, bir veya daha fazla öğenin ' A ' karakteri olup olmadığını sorar ve sonuç olur `true` . İkinci işlem, tüm öğelerin ' A ' karakteri olup olmadığını ve sonucun olduğunu sorar `true` .  
  
 ![LINQ nicelik belirteci Işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Belirleyici işlemler gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Description|Sorgu Ifadesi söz dizimini Visual Basic|Daha Fazla Bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Tümü|Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Herhangi biri|Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Contains|Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.|Geçerli değildir.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu Ifadesi söz dizimi örnekleri  

 Bu örnekler, `Aggregate` BIR LINQ sorgusunda filtreleme koşulunun bir parçası olarak Visual Basic yan tümcesini kullanır.  
  
 Aşağıdaki örnek, `Aggregate` <xref:System.Linq.Enumerable.All%2A> pelleri belirtilen bir Age den daha eski olan kişilerden gelen bir koleksiyondan geri dönmek için yan tümcesini ve genişletme yöntemini kullanır.  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 Sonraki örnekte, belirli bir `Aggregate` <xref:System.Linq.Enumerable.Any%2A> yaşından daha eski olan en az bir evcil hayvan olan kişilerden gelen bir koleksiyondan geri dönmek için yan tümce ve genişletme yöntemi kullanılmaktadır.  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [Aggregate Yan Tümcesi](../../../language-reference/queries/aggregate-clause.md)
- [Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
