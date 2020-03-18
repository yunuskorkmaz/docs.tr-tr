---
title: Veri Filtreleme (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346987"
---
# <a name="filtering-data-c"></a>Veri Filtreleme (C#)
Filtreleme, yalnızca belirli bir koşulu karşılayan öğeleri içerecek şekilde ayarlanan sonucu kısıtlama işlemini ifade eder. Seçim olarak da bilinir.  
  
 Aşağıdaki resimde, bir karakter dizisini filtrelemenin sonuçları gösterilmektedir. Filtreleme işleminin yüklemi, karakterin 'A' olması gerektiğini belirtir.  
  
 ![LINQ filtreleme işlemini gösteren diyagram](./media/filtering-data/linq-filter-operation.png)  
  
 Seçimi gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem Adı|Açıklama|C# Sorgu İfade Sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Oftype|Belirli bir türe döküm yeteneğine bağlı olarak değerleri seçer.|Geçerli değildir.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Konum|Yüklem işlevini temel alan değerleri seçer.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu İfadesözdizimi Örneği  
 Aşağıdaki örnek, `where` belirli bir uzunluğa sahip dizeleri bir diziden filtrelemek için yan tümceyi kullanır.  
  
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
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [where tümcesi](../../../language-reference/keywords/where-clause.md)
- [Çalışma zamanında koşul filtrelerini dinamik olarak belirtme](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Yansıma (LINQ) (C#) ile bir derlemenin meta verisi nasıl sorgulanır?](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Belirli bir öznitelik veya ada sahip dosyalar için sorgulama (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Metin verilerini herhangi bir sözcüğe veya alana göre sıralama veya filtreleme (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
