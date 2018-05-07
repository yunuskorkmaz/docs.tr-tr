---
title: orderby tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 1fd0036e8bd3c838fe92ca27635cd7638d59ef1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [group yan tümcesi](../../../csharp/language-reference/keywords/group-clause.md)  
 [C#'de LINQ Kullanmaya Başlama](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
