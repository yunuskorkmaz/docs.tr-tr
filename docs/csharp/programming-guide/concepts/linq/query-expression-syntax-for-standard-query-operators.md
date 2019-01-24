---
title: Standart sorgu işleçleri (C#) için sorgu ifade sözdizimi
ms.date: 07/20/2015
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
ms.openlocfilehash: 232793e63673ef51b650d8188fea5733d02fd1b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501782"
---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a>Standart sorgu işleçleri (C#) için sorgu ifade sözdizimi
Bazı daha sık kullanılan standart sorgu işleçlerinin bir parçası olarak çağrılacak tanıyan C# dil anahtar sözcüğü sözdizimi adanmış bir *sorgu ifadesi*. Sorgu ifadesi ifade değerinden bir sorgu, farklı, daha okunabilir bir form olan kendi *yöntemi tabanlı* eşdeğer. Sorgu ifadesi tümceleri sorgu yöntemlere yapılan çağrılar derleme zamanında çevrilir.  
  
## <a name="query-expression-syntax-table"></a>Sorgu ifadesi söz dizimi tablosu  
 Aşağıdaki tabloda eşdeğer sorgu ifadesi tümceleri sahip standart sorgu işleçleri listelenir.  
  
|Yöntem|C# sorgu ifade sözdizimi|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|Örneğin, bir açık olarak aralık değişkeni kullanın:<br /><br /> `from int i in numbers`<br /><br /> (Daha fazla bilgi için [from yan tümcesinde](../../../../csharp/language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> -veya-<br /><br /> `group … by … into …`<br /><br /> (Daha fazla bilgi için [group yan tümcesi](../../../../csharp/language-reference/keywords/group-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> (Daha fazla bilgi için [JOIN yan tümcesi](../../../../csharp/language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> (Daha fazla bilgi için [JOIN yan tümcesi](../../../../csharp/language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> (Daha fazla bilgi için [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> (Daha fazla bilgi için [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> (Daha fazla bilgi için [select yan tümcesi](../../../../csharp/language-reference/keywords/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Birden çok `from` yan tümceleri.<br /><br /> (Daha fazla bilgi için [from yan tümcesinde](../../../../csharp/language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> (Daha fazla bilgi için [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> (Daha fazla bilgi için [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> (Daha fazla bilgi için [burada yan tümcesi](../../../../csharp/language-reference/keywords/where-clause.md).)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart sorgu işleçlerinin yöntemine göre sınıflandırılması yürütme (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
