---
title: "Standart sorgu işleçleri (C#) için sorgu ifade sözdizimi"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f662f23948f5d18c31a981a2f46d78f382ff5c96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a>Standart sorgu işleçleri (C#) için sorgu ifade sözdizimi
Bazı daha sık kullanılan standart sorgu işleçleri bunları parçası olarak çağrılacak etkinleştiren C# dili anahtar sözcüğü sözdizimini adanmış bir *sorgu ifadesi*. Bir sorgu ifadesi daha sorgu ifade, farklı, daha okunabilir bir form olan kendi *yöntemi tabanlı* eşdeğer. Sorgu ifadesi yan tümceleri derleme zamanında sorgu yöntemleri çağrıları içine çevrilir.  
  
## <a name="query-expression-syntax-table"></a>Sorgu ifade sözdizimi tablosu  
 Aşağıdaki tabloda eşdeğer sorgu ifadesi yan tümceleri sahip standart sorgu işleçleri listeler.  
  
|Yöntem|C# sorgu ifade sözdizimi|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|Örneğin bir açıkça belirtilmiş aralık değişkeni kullanın:<br /><br /> `from int i in numbers`<br /><br /> (Daha fazla bilgi için bkz: [from yan tümcesi](../../../../csharp/language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> veya<br /><br /> `group … by … into …`<br /><br /> (Daha fazla bilgi için bkz: [group yan tümcesi](../../../../csharp/language-reference/keywords/group-clause.md).)|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> (Daha fazla bilgi için bkz: [JOIN yan tümcesi](../../../../csharp/language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> (Daha fazla bilgi için bkz: [JOIN yan tümcesi](../../../../csharp/language-reference/keywords/join-clause.md).)|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> (Daha fazla bilgi için bkz: [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> (Daha fazla bilgi için bkz: [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> (Daha fazla bilgi için bkz: [select yan tümcesi](../../../../csharp/language-reference/keywords/select-clause.md).)|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|Birden çok `from` yan tümceleri.<br /><br /> (Daha fazla bilgi için bkz: [from yan tümcesi](../../../../csharp/language-reference/keywords/from-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> (Daha fazla bilgi için bkz: [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> (Daha fazla bilgi için bkz: [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).)|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> (Daha fazla bilgi için bkz: [burada yan tümcesi](../../../../csharp/language-reference/keywords/where-clause.md).)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Standart sorgu işleçleri yürütme (C#) yöntemine göre sınıflandırılması](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
