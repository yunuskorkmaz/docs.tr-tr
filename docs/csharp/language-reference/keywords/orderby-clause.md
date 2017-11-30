---
title: "orderby tümcesi (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc688e7ba164dcca71d13b2d79d30f1373c4778e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="orderby-clause-c-reference"></a>orderby tümcesi (C# Başvurusu)
Bir sorgu ifadesinde `orderby` yan tümcesi döndürülen dizi veya değişkene (artan veya azalan düzende sıralanmış grup) neden olur. Birden çok anahtar, bir veya daha fazla ikincil sıralama işlemi gerçekleştirmek için belirtilebilir. Sıralama öğesi türü için varsayılan karşılaştırıcı tarafından gerçekleştirilir. Varsayılan sıralama düzeni artan. Özel bir karşılaştırıcı de belirtebilirsiniz. Ancak, yalnızca yöntemi tabanlı sözdizimini kullanarak kullanılabilir. Daha fazla bilgi için bkz: [veri sıralama](../../programming-guide/concepts/linq/sorting-data.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, ilk sorgu sözcükleri A'dan başlangıç alfabetik sırada sıralar ve ikinci sorguyu aynı sözcükler azalan düzende sıralar. ( `ascending` Anahtar sözcüğü varsayılan sıralama değerdir ve atlanabilir.)  
  
 [!code-csharp[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek ilk adlarını Öğrenciler son adları birincil sıralama ve ikincil bir sıralama gerçekleştirir.  
  
 [!code-csharp[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 Derleme zamanında `orderby` yan tümcesi için bir çağrı çevrilir <xref:System.Linq.Enumerable.OrderBy%2A> yöntemi. Birden çok anahtarlar `orderby` yan tümcesi çevirmek için <xref:System.Linq.Enumerable.ThenBy%2A> yöntem çağrıları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [Sorgu anahtar sözcükleri (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Group tümcesi](../../../csharp/language-reference/keywords/group-clause.md)  
 [C# üzerinde LINQ ile çalışmaya başlama](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
