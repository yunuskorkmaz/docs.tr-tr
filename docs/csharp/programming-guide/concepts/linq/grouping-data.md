---
title: Verileri gruplandırma (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 15dafdb144ee9fd4184d4c8281d041e03161a16b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594195"
---
# <a name="grouping-data-c"></a>Verileri gruplandırma (C#)
Gruplandırma, her bir gruptaki öğelerin ortak bir özniteliği paylaşması için verileri gruplara yerleştirme işlemini ifade eder.  
  
 Aşağıdaki çizimde, bir karakter dizisini gruplandırmanın sonuçları gösterilmektedir. Her grup için anahtar karakterdir.  
  
 ![LINQ gruplama işlemini gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 Veri öğelerini gruplamak için kullanılan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C#Sorgu Ifadesi söz dizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Ölçütü|Ortak bir özniteliği paylaşan öğeleri gruplandırır. Her grup bir <xref:System.Linq.IGrouping%602> nesne tarafından temsil edilir.|`group … by`<br /><br /> -veya-<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|Bir <xref:System.Linq.Lookup%602> anahtar Seçici işlevine göre öğeleri (bire çok sözlüğüne) ekler.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu Ifadesi söz dizimi örneği  
 Aşağıdaki kod örneği, bir listedeki `group by` tamsayıları, hatta veya tek olup olmadığına göre gruplamak için yan tümcesini kullanır.  
  
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
- [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)
- [group yan tümcesi](../../../language-reference/keywords/group-clause.md)
- [Nasıl yapılır: Iç Içe geçmiş grup oluşturma](../../linq-query-expressions/how-to-create-a-nested-group.md)
- [Nasıl yapılır: Dosyaları uzantıya göre Gruplandır (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)
- [Nasıl yapılır: Sorgu sonuçlarını gruplandırma](../../linq-query-expressions/how-to-group-query-results.md)
- [Nasıl yapılır: Gruplandırma Işleminde alt sorgu gerçekleştirme](../../linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
- [Nasıl yapılır: Grupları (LINQ) kullanarak bir dosyayı çok sayıda dosyaya bölme (LINQC#) ()](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
