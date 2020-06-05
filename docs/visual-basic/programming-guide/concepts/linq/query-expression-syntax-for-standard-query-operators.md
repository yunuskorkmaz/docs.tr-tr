---
title: Standart Sorgu İşleçleri için Sorgu İfade Sözdizimi
ms.date: 07/20/2015
ms.assetid: eb978d86-d3b5-497b-95ce-a054bea8f510
ms.openlocfilehash: 69bb50007c04bf8d1ee1553a37aca542afbffab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396291"
---
# <a name="query-expression-syntax-for-standard-query-operators-visual-basic"></a>Standart sorgu Işleçleri için sorgu Ifadesi sözdizimi (Visual Basic)
Daha sık kullanılan standart sorgu işleçlerinden bazılarının, bir *sorgu ifadesinin*parçası olarak çağrılmasına olanak tanıyan Visual Basic Language anahtar sözcüğü sözdizimi vardır. Sorgu ifadesi, sorgu *yöntemi tabanlı* eşinden farklı bir sorgu ifade eden farklı, daha okunabilir bir formdur. Sorgu ifadesi yan tümceleri, derleme zamanında sorgu yöntemlerine yapılan çağrılara çevrilir.  
  
## <a name="query-expression-syntax-table"></a>Sorgu Ifadesi söz dizimi tablosu  
 Aşağıdaki tabloda denk sorgu ifadesi yan tümceleri olan standart sorgu işleçleri listelenmektedir.  
  
|Yöntem|Sorgu Ifadesi söz dizimini Visual Basic|  
|------------|------------------------------------------|  
|<xref:System.Linq.Enumerable.All%2A>|`Aggregate … In … Into All(…)`<br /><br /> (Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Any%2A>|`Aggregate … In … Into Any()`<br /><br /> (Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Average%2A>|`Aggregate … In … Into Average()`<br /><br /> (Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Cast%2A>|`From … As …`<br /><br /> (Daha fazla bilgi için bkz. [from tümcesi](../../../language-reference/queries/from-clause.md).)|  
|<xref:System.Linq.Enumerable.Count%2A>|`Aggregate … In … Into Count()`<br /><br /> (Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Distinct%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|`Distinct`<br /><br /> (Daha fazla bilgi için bkz. [DISTINCT tümcesi](../../../language-reference/queries/distinct-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`Group … By … Into …`<br /><br /> (Daha fazla bilgi için bkz. [Group by yan tümcesi](../../../language-reference/queries/group-by-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`Group Join … In … On …`<br /><br /> (Daha fazla bilgi için bkz. [Group JOIN yan tümcesi](../../../language-reference/queries/group-join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`From x In …, y In … Where x.a = b.a`<br /><br /> -veya-<br /><br /> `Join … [As …]In … On …`<br /><br /> (Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../language-reference/queries/join-clause.md).)|  
|<xref:System.Linq.Enumerable.LongCount%2A>|`Aggregate … In … Into LongCount()`<br /><br /> (Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Max%2A>|`Aggregate … In … Into Max()`<br /><br /> (Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Min%2A>|`Aggregate … In … Into Min()`<br /><br /> (Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By`<br /><br /> (Daha fazla bilgi için bkz. [order by yan tümcesi](../../../language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By … Descending`<br /><br /> (Daha fazla bilgi için bkz. [order by yan tümcesi](../../../language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`Select`<br /><br /> (Daha fazla bilgi için bkz. [Select yan tümcesi](../../../language-reference/queries/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Birden çok `From` yan tümce<br /><br /> (Daha fazla bilgi için bkz. [from tümcesi](../../../language-reference/queries/from-clause.md).)|  
|<xref:System.Linq.Enumerable.Skip%2A>|`Skip`<br /><br /> (Daha fazla bilgi için bkz. [Skip tümcesi](../../../language-reference/queries/skip-clause.md).)|  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|`Skip While`<br /><br /> (Daha fazla bilgi için bkz. [Skip While tümcesi](../../../language-reference/queries/skip-while-clause.md).)|  
|<xref:System.Linq.Enumerable.Sum%2A>|`Aggregate … In … Into Sum()`<br /><br /> (Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md).)|  
|<xref:System.Linq.Enumerable.Take%2A>|`Take`<br /><br /> (Daha fazla bilgi için bkz. [Take tümcesi](../../../language-reference/queries/take-clause.md).)|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>|`Take While`<br /><br /> (Daha fazla bilgi için bkz. [Take While tümcesi](../../../language-reference/queries/take-while-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, …`<br /><br /> (Daha fazla bilgi için bkz. [order by yan tümcesi](../../../language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`Order By …, … Descending`<br /><br /> (Daha fazla bilgi için bkz. [order by yan tümcesi](../../../language-reference/queries/order-by-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`Where`<br /><br /> (Daha fazla bilgi için bkz. [WHERE tümcesi](../../../language-reference/queries/where-clause.md).)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [Standart sorgu Işleçleri yürütme yöntemine göre sınıflandırma (Visual Basic)](classification-of-standard-query-operators-by-manner-of-execution.md)
