---
title: Standart sorgu Işleçleri için sorgu Ifadesi sözdizimi (C#)
description: Standart sorgu işleçleri için sorgu ifadesi söz dizimi hakkında bilgi edinin. Denk sorgu ifadesi yan tümcelerine sahip standart sorgu işleçleri listesini görüntüleyin.
ms.date: 07/20/2015
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
ms.openlocfilehash: f85563de496eaf423ea7a43c6d7100bb93eae5b1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195531"
---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a>Standart sorgu Işleçleri için sorgu Ifadesi sözdizimi (C#)

Daha sık kullanılan standart sorgu işleçlerinden bazılarının, bir *sorgu ifadesinin*parçası olarak çağrılmasına olanak tanıyan özel C# Language anahtar sözcüğü sözdizimi vardır. Sorgu ifadesi, sorgu *yöntemi tabanlı*  eşinden farklı bir sorgu ifade eden farklı, daha okunabilir bir formdur. Sorgu ifadesi yan tümceleri, derleme zamanında sorgu yöntemlerine yapılan çağrılara çevrilir.  
  
## <a name="query-expression-syntax-table"></a>Sorgu Ifadesi söz dizimi tablosu  

 Aşağıdaki tabloda denk sorgu ifadesi yan tümceleri olan standart sorgu işleçleri listelenmektedir.  
  
|Yöntem|C# sorgu Ifadesi sözdizimi|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|Açıkça yazılmış bir Aralık değişkeni kullanın, örneğin:<br /><br /> `from int i in numbers`<br /><br /> (Daha fazla bilgi için bkz. [from tümcesi](../../../language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> -veya-<br /><br /> `group … by … into …`<br /><br /> (Daha fazla bilgi için bkz. [Grup tümcesi](../../../language-reference/keywords/group-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> (Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> (Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> (Daha fazla bilgi için bkz. [OrderBy tümcesi](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> (Daha fazla bilgi için bkz. [OrderBy tümcesi](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> (Daha fazla bilgi için bkz. [Select yan tümcesi](../../../language-reference/keywords/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Birden çok `from` yan tümce.<br /><br /> (Daha fazla bilgi için bkz. [from tümcesi](../../../language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> (Daha fazla bilgi için bkz. [OrderBy tümcesi](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> (Daha fazla bilgi için bkz. [OrderBy tümcesi](../../../language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> (Daha fazla bilgi için bkz. [WHERE tümcesi](../../../language-reference/keywords/where-clause.md).)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Standart sorgu Işleçlerine genel bakış (C#)](./standard-query-operators-overview.md)
- [Standart sorgu Işleçlerinin yürütme yöntemine göre sınıflandırılması (C#)](./classification-of-standard-query-operators-by-manner-of-execution.md)
