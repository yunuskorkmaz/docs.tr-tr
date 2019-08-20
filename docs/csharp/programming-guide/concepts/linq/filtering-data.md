---
title: Verileri filtreleme (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 17d3a65b6042c9679a263eff0048f5360c4aa546
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594399"
---
# <a name="filtering-data-c"></a>Verileri filtreleme (C#)
Filtreleme, sonuç kümesini yalnızca belirtilen bir koşulu karşılayan öğeleri içerecek şekilde kısıtlama işlemini ifade eder. Seçim olarak da bilinir.  
  
 Aşağıdaki çizimde, bir karakter dizisinin filtrelenmesi sonuçları gösterilmektedir. Filtreleme işleminin koşulu, karakterin ' A ' olması gerektiğini belirtir.  
  
 ![LINQ filtreleme işlemini gösteren diyagram](./media/filtering-data/linq-filter-operation.png)  
  
 Seçimi gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C#Sorgu Ifadesi söz dizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|Belirtilen türe atama becerisine bağlı olarak değerleri seçer.|Geçerli değildir.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Where|Bir koşul işlevini temel alan değerleri seçer.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
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
- [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)
- [where yan tümcesi](../../../language-reference/keywords/where-clause.md)
- [Nasıl yapılır: Çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [Nasıl yapılır: Bir derlemenin meta verilerini yansıma ile sorgulama (LINQ) (C#)](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Nasıl yapılır: Belirtilen bir özniteliğe veya ada (C#) sahip dosyaları sorgula](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Nasıl yapılır: Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
