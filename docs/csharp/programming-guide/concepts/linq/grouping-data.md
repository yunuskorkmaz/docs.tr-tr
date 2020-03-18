---
title: Verileri Gruplandırma (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 7ef3d3c9097d7a9478605565518ac8975feb9fe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635749"
---
# <a name="grouping-data-c"></a>Verileri Gruplandırma (C#)
Gruplandırma, her gruptaki öğelerin ortak bir özniteliği paylaşabilmesi için verileri gruplara ayırma işlemini ifade eder.  
  
 Aşağıdaki resimde, bir karakter dizisini gruplandırmanın sonuçları gösterilmektedir. Her grup için anahtar karakterdir.  
  
 ![BIR LINQ Gruplandırma işlemini gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 Veri öğelerini gruplayan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem Adı|Açıklama|C# Sorgu İfade Sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|GroupBy|Ortak bir özniteliği paylaşan öğeleri grupla. Her grup bir <xref:System.Linq.IGrouping%602> nesne tarafından temsil edilir.|`group … by`<br /><br /> -veya-<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|Tolookup|Öğeleri anahtar seçici <xref:System.Linq.Lookup%602> işlevine dayalı bir (bir-çok sözlük) ekler.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu İfadesözdizimi Örneği  
 Aşağıdaki kod örneği, `group by` tamsayıları bir listede çift veya tek olup olmadıklarına göre gruplandırmak için yan tümceyi kullanır.  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [group yan tümcesi](../../../language-reference/keywords/group-clause.md)
- [İç içe geçmiş grup oluşturma](../../../linq/create-a-nested-group.md)
- [Uzantıya göre dosya gruplandırma (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)
- [Sorgu sonuçlarını gruplandırma](../../../linq/group-query-results.md)
- [Gruplandırma işleminde alt sorgu gerçekleştirme](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [Grupları kullanarak bir dosyayı birçok dosyaya bölme (LINQ) (C#)](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
