---
title: Verileri Sıralama (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 29a5e3e685bdc73536961b7783f4986796b46bdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167913"
---
# <a name="sorting-data-c"></a>Verileri Sıralama (C#)
Sıralama işlemi, bir veya daha fazla özöğeyi temel alan bir dizinin öğelerini sıralar. İlk sıralama ölçütü öğeler üzerinde birincil sıralama gerçekleştirir. İkinci bir sıralama ölçütü belirterek, her birincil sıralama grubundaki öğeleri sıralayabilirsiniz.  
  
 Aşağıdaki resimde, bir karakter dizisi üzerinde alfabetik sıralama işleminin sonuçları gösterilmektedir:
  
 ![Alfabetik sıralama işlemi gösteren grafik.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 Verileri sıralayan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem Adı|Açıklama|C# Sorgu İfade Sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Orderby|Değerleri artan sırada sıralar.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|Orderbydescending|Değerleri azalan sırada sıralar.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|Thenby|Artan sırada ikincil bir sıralama gerçekleştirir.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|Thenbydescending|Azalan sırada ikincil bir sıralama gerçekleştirir.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Reverse|Koleksiyondaki öğelerin sırasını tersine çevirir.|Geçerli değildir.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu İfadesözdizimi Örnekleri  
  
### <a name="primary-sort-examples"></a>Birincil Sıralama Örnekleri  
  
#### <a name="primary-ascending-sort"></a>Birincil Artan Sıralama  
 Aşağıdaki örnek, bir dizideki `orderby` dizeleri artan sırada dize uzunluğuna göre sıralamak için BIR LINQ sorgusunda yan tümcenin nasıl kullanılacağını gösterir.  
  
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
  
#### <a name="primary-descending-sort"></a>Birincil Azalan Sıralama  
 Sonraki örnek, dizeleri azalan `orderby descending` sırada ilk harflerine göre sıralamak için bir LINQ sorgusunda yan tümcenin nasıl kullanılacağını gösterir.  
  
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
  
### <a name="secondary-sort-examples"></a>İkincil Sıralama Örnekleri  
  
#### <a name="secondary-ascending-sort"></a>İkincil Artan Sıralama  
 Aşağıdaki örnek, bir dizideki `orderby` dizeleri birincil ve ikincil bir tür gerçekleştirmek için bir LINQ sorgusunda yan tümceyi nasıl kullanılacağını gösterir. Dizeleri öncelikle uzunluk ve ikinci olarak dize ilk harfi, her ikisi de artan sırada sıralanır.  
  
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
  
#### <a name="secondary-descending-sort"></a>İkincil Azalan Sıralama  
 Sonraki örnek, bir birincil `orderby descending` sıralama gerçekleştirmek için bir LINQ sorgusunda yan tümcesinin nasıl kullanılacağını, artan sırada ve ikincil sıralamayı azalan sırada gösterir. Dizeleri öncelikle uzunluk ve ikinci olarak dize ilk harfi tarafından sıralanır.  
  
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
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [orderby yan tümcesi](../../../language-reference/keywords/orderby-clause.md)
- [Join yan tümcesinin sonuçlarını sıralama](../../../linq/order-the-results-of-a-join-clause.md)
- [Metin verilerini herhangi bir sözcüğe veya alana göre sıralama veya filtreleme (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
