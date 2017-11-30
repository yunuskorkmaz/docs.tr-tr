---
title: "Veri sıralama (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f5756c87f50e759542d0d1ccbb71710ad9eb6e27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-c"></a>Veri sıralama (C#)
Sıralama işlemi bir veya daha fazla özniteliklerini temel alarak bir sıradaki sıralar. İlk sıralama ölçütü birincil sıralama öğeleri gerçekleştirir. İkinci bir sıralama ölçütü belirterek, her birincil sıralama grup içindeki öğeleri sıralama yapabilirsiniz.  
  
 Aşağıdaki çizimde bir dizi karakterden oluşan bir alfabetik sıralama işlemi sonuçlarını gösterir.  
  
 ![Sıralama işlemi LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")  
  
 Verileri sıralama standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OrderBy|Artan düzende değerlerini sıralar.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Azalan düzende değerlerini sıralar.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|İkincil bir sıralama artan düzende gerçekleştirir.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|İkincil bir sıralamayı azalan sırada gerçekleştirir.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Ters Çevir|Bir koleksiyondaki öğelerin sırasını tersine çevirir.|Yok.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifade sözdizimi örnekleri  
  
### <a name="primary-sort-examples"></a>Birincil sıralama örnekleri  
  
#### <a name="primary-ascending-sort"></a>Birincil artan sıralama  
 Aşağıdaki örnekte nasıl kullanılacağı ortaya `orderby` dize uzunluğu, artan bir dizi dizelerde sıralamak için bir LINQ sorgu yan tümcesinde.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a>Birincil azalan sıralama  
 Sonraki örnek nasıl kullanılacağı ortaya `orderby``descending` azalan sırada kendi ilk harfi dizeleri sıralamak için bir LINQ sorgu yan tümcesinde.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a>İkincil sıralama örnekleri  
  
#### <a name="secondary-ascending-sort"></a>İkincil artan sıralama  
 Aşağıdaki örnekte nasıl kullanılacağı ortaya `orderby` dizeleri birincil ve ikincil bir tür bir dizide gerçekleştirmek için bir LINQ sorgu yan tümcesinde. Dizeleri öncelikle uzunluğu ve ürüne ilk harfini dizesinin hem artan düzende sıralanır.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a>İkincil azalan sıralama  
 Sonraki örnek nasıl kullanılacağı ortaya `orderby``descending` birincil bir sıralama düzeni ve azalan bir ikincil sıralama artan düzende gerçekleştirmek için bir LINQ sorgu yan tümcesinde. Dizeleri öncelikle uzunluğu ve ürüne dizenin ilk harfini sıralanır.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [OrderBy yan tümcesi](../../../../csharp/language-reference/keywords/orderby-clause.md)  
 [Nasıl yapılır: Join tümcesinin sonuçlarını sıralama](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [Nasıl yapılır: sıralama veya filtre metni verilerle herhangi bir sözcük veya alana (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
