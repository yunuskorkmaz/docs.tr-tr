---
title: Verileri sıralama (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 28cf4025d0b9bca841695c9873a0ff7972726b98
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591047"
---
# <a name="sorting-data-c"></a>Verileri sıralama (C#)
Sıralama işlemi bir veya daha fazla özniteliğe göre bir sıranın öğelerini sıralar. İlk sıralama ölçütü öğeler üzerinde birincil bir sıralama gerçekleştirir. İkinci bir sıralama ölçütü belirterek, her birincil sıralama grubu içindeki öğeleri sıralayabilirsiniz.  
  
 Aşağıdaki çizimde, bir karakter dizisi üzerinde alfabetik bir sıralama işleminin sonuçları gösterilmektedir: 
  
 ![Alfabetik bir sıralama işlemini gösteren grafik.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 Verileri sıralayan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C#Sorgu Ifadesi söz dizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OrderBy|Değerleri artan düzende sıralar.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Değerleri azalan düzende sıralar.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|Artan sırada ikincil bir sıralama gerçekleştirir.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|Azalan sırada ikincil bir sıralama gerçekleştirir.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Tersini|Bir koleksiyondaki öğelerin sırasını tersine çevirir.|Geçerli değildir.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu Ifadesi söz dizimi örnekleri  
  
### <a name="primary-sort-examples"></a>Birincil sıralama örnekleri  
  
#### <a name="primary-ascending-sort"></a>Birincil artan sıralama  
 Aşağıdaki örnek, bir dizideki dizeleri dize uzunluğuna `orderby` göre artan sırada sıralamak için bir LINQ sorgusunda yan tümcesinin nasıl kullanılacağını gösterir.  
  
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
 Sonraki örnekte, bir LINQ sorgusunda, dizeyi `orderby descending` azalan sırada ilk harfine göre sıralamak için yan tümcesinin nasıl kullanılacağı gösterilmektedir.  
  
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
 Aşağıdaki örnek, bir dizideki dizelerin birincil ve `orderby` ikincil sıralamasını gerçekleştirmek için bir LINQ sorgusunda yan tümcesinin nasıl kullanılacağını gösterir. Dizeler birincil olarak length ve secondarily ile dizenin ilk harfine göre, her ikisi de artan düzende sıralanır.  
  
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
 Sonraki örnekte, bir LINQ sorgusunda `orderby descending` yan tümcesinin nasıl kullanılacağı gösterilmektedir ve azalan düzende bir birincil sıralama, artan sırada ve ikincil bir sıralama işlemleri yapılır. Dizeler öncelikle dizenin ilk harfine göre uzunluğa ve secondarily göre sıralanır.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)
- [orderby yan tümcesi](../../../language-reference/keywords/orderby-clause.md)
- [Nasıl yapılır: JOIN yan tümcesinin sonuçlarını sıralama](../../linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)
- [Nasıl yapılır: Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
