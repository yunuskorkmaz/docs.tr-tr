---
title: Verileri filtreleme (C#)
description: Seçim olarak da bilinen filtreleme, bir koşula bağlı olarak sonuçları kısıtlar. C# ' de, filtre uygulayan standart sorgu işleci yöntemleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 51bf9f930ba67ba07c7c0f357910d5e36014138d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186048"
---
# <a name="filtering-data-c"></a>Verileri filtreleme (C#)

Filtreleme, sonuç kümesini yalnızca belirtilen bir koşulu karşılayan öğeleri içerecek şekilde kısıtlama işlemini ifade eder. Seçim olarak da bilinir.  
  
 Aşağıdaki çizimde, bir karakter dizisinin filtrelenmesi sonuçları gösterilmektedir. Filtreleme işleminin koşulu, karakterin ' A ' olması gerektiğini belirtir.  
  
 ![LINQ filtreleme işlemini gösteren diyagram](./media/filtering-data/linq-filter-operation.png)  
  
 Seçimi gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu Ifadesi sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|Belirtilen türe atama becerisine bağlı olarak değerleri seçer.|Geçerli değildir.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Konum|Bir koşul işlevini temel alan değerleri seçer.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu Ifadesi söz dizimi örneği  

 Aşağıdaki örnek, `where` belirli bir uzunluğa sahip dizelerin bulunduğu bir diziden filtrelemek için yan tümcesini kullanır.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (C#)](./standard-query-operators-overview.md)
- [WHERE yan tümcesi](../../../language-reference/keywords/where-clause.md)
- [Çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (C#)](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Belirtilen bir özniteliğe veya ada sahip dosyaları sorgulama (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
