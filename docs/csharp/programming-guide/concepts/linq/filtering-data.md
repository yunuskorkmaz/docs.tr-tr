---
title: Verileri filtreleme (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 61d80674fd858063e77749342a33d714e3a57c6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826073"
---
# <a name="filtering-data-c"></a>Verileri filtreleme (C#)
Filtreleme işlemi yalnızca belirli bir koşulu karşılayan öğeleri içeren sonuç kısıtlama ifade eder. Olarak da bilinir, seçim değildir.  
  
 Aşağıdaki çizimde bir karakter dizisi filtreleme sonuçlarını gösterir. Filtreleme işlemi için koşulu karakter 'A' olması gerektiğini belirtir.  
  
 ![Filtreleme işlemi bir LINQ gösteren diyagram](./media/filtering-data/linq-filter-operation.png)  
  
 Seçimi gerçekleştirmek standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|Değerleri belirtilen bir türe yayınlanması için kendi yeteneği bağlı olarak seçer.|Geçerli değildir.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Where|Bir koşul işlevini temel alan değerleri seçer.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu ifade sözdizimi örneği  
 Aşağıdaki örnekte `where` bir diziden belirli bir uzunluğa sahip Bu dizelerin filtrelemek için yan tümcesi.  
  
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
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [where yan tümcesi](../../../../csharp/language-reference/keywords/where-clause.md)
- [Nasıl yapılır: Çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [Nasıl yapılır: Bir derlemenin meta verilerini (LINQ) yansıma ile sorgulama (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Nasıl yapılır: Belirtilen öznitelik veya ada sahip dosyaları sorgulama (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Nasıl yapılır: Herhangi bir sözcük veya alana (LINQ) göre filtre metin verilerini sıralama veya (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
