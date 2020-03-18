---
title: Standart Sorgu Operatörleri için Sorgu İfade Sözdizimi (C#)
ms.date: 07/20/2015
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
ms.openlocfilehash: dac63ae165b88924cb0e91336571173f764569ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591432"
---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a>Standart Sorgu Operatörleri için Sorgu İfade Sözdizimi (C#)
Daha sık kullanılan standart sorgu işleçlerinden bazıları, sorgu *ifadesinin*bir parçası olarak çağrılmasını sağlayan C# dili anahtar kelime sözdizimini adadı. Sorgu ifadesi, bir sorgunun *yöntem tabanlı* eşdeğerinden farklı ve daha okunabilir bir ifade biçimidir. Sorgu ifade yan tümceleri derleme zamanında sorgu yöntemlerine çağrılara çevrilir.  
  
## <a name="query-expression-syntax-table"></a>Sorgu İfade sözdizimi tablosu  
 Aşağıdaki tabloda eşdeğer sorgu ifade yan tümceleri olan standart sorgu işleçleri listelenmiştir.  
  
|Yöntem|C# Sorgu İfade Sözdizimi|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|Örneğin, açıkça yazılan bir aralık değişkeni kullanın:<br /><br /> `from int i in numbers`<br /><br /> (Daha fazla bilgi için, [yan tümceye](../../../language-reference/keywords/from-clause.md)bakın.)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> -veya-<br /><br /> `group … by … into …`<br /><br /> (Daha fazla bilgi için [grup yan tümcesi'ne](../../../language-reference/keywords/group-clause.md)bakın.)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> (Daha fazla bilgi [için, join yan tümcesi](../../../language-reference/keywords/join-clause.md)bakın.)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> (Daha fazla bilgi [için, join yan tümcesi](../../../language-reference/keywords/join-clause.md)bakın.)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> (Daha fazla bilgi için [bkz.](../../../language-reference/keywords/orderby-clause.md)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> (Daha fazla bilgi için [bkz.](../../../language-reference/keywords/orderby-clause.md)|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> (Daha fazla bilgi için [bkz.](../../../language-reference/keywords/select-clause.md)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Birden `from` fazla yan tümce.<br /><br /> (Daha fazla bilgi için, [yan tümceye](../../../language-reference/keywords/from-clause.md)bakın.)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> (Daha fazla bilgi için [bkz.](../../../language-reference/keywords/orderby-clause.md)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> (Daha fazla bilgi için [bkz.](../../../language-reference/keywords/orderby-clause.md)|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> (Daha fazla bilgi için [bkz.](../../../language-reference/keywords/where-clause.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [Standart Sorgu Operatörlerinin Yürütme Şekline Göre Sınıflandırılması (C#)](./classification-of-standard-query-operators-by-manner-of-execution.md)
