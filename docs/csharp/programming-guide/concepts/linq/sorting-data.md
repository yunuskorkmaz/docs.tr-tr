---
title: Verileri sıralama (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 6a7f687895385bfb77d2a1e3e785742a794bb1b6
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275177"
---
# <a name="sorting-data-c"></a>Verileri sıralama (C#)
Sıralama işlemi bir veya daha fazla özniteliklerine dayalı bir dizinin öğeleri sıralar. İlk sıralama ölçütü öğelerde birincil sıralama gerçekleştirir. İkinci bir sıralama ölçütünü belirterek, her birincil sıralama grup içindeki öğeleri sıralayabilirsiniz.  
  
 Aşağıdaki çizimde, bir dizi karakter bir alfabetik sıralama işlemi sonuçlarını gösterir.  
  
 ![Sıralama işlemi LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")  
  
 Verileri sıralama standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OrderBy|Artan değerleri sıralar.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Değerleri azalan düzende sıralar.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|İkincil bir sıralama, azalan sırada gerçekleştirir.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|İkincil bir sıralama, azalan sırada gerçekleştirir.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|geriye doğru|Bir koleksiyondaki öğelerin sırasını tersine çevirir.|Yok.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifadesi söz dizimi örnekleri  
  
### <a name="primary-sort-examples"></a>Birincil sıralama örnekleri  
  
#### <a name="primary-ascending-sort"></a>Birincil artan sıralama  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `orderby` artan düzende dize uzunluğu, dizi dizeleri sıralamak için bir LINQ sorgu yan tümcesi.  
  
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
 Sonraki örnek nasıl kullanılacağını gösterir `orderby descending` azalan düzende, ilk harfini dizeleri sıralamak için bir LINQ sorgu yan tümcesi.  
  
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
 Aşağıdaki örnek nasıl kullanılacağını gösterir `orderby` bir dizide dize birincil ve ikincil bir sıralama gerçekleştirmek için bir LINQ sorgu yan tümcesi. Dizeleri öncelikle uzunluğu ve ürüne göre ilk harfini dize hem artan düzende sıralanır.  
  
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
 Sonraki örnek nasıl kullanılacağını gösterir `orderby descending` birincil bir sıralama düzeni ve ikincil bir sıralama, azalan düzende, artan düzende gerçekleştirmek için bir LINQ sorgu yan tümcesi. Dizeleri öncelikle uzunluğu ve ürüne dizenin ilk harfini sıralanır.  
  
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

- <xref:System.Linq>  
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [orderby yan tümcesi](../../../../csharp/language-reference/keywords/orderby-clause.md)  
- [Nasıl yapılır: Join tümcesinin sonuçlarını sıralama](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
- [Nasıl yapılır: herhangi bir sözcük veya alana (LINQ) (C#) göre filtre metin verilerini sıralama veya](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
