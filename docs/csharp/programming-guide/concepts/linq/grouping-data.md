---
title: Verileri gruplandırma (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 7ef3d3c9097d7a9478605565518ac8975feb9fe2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635749"
---
# <a name="grouping-data-c"></a>Verileri gruplandırma (C#)
Gruplandırma, her bir gruptaki öğelerin ortak bir özniteliği paylaşması için verileri gruplara yerleştirme işlemini ifade eder.  
  
 Aşağıdaki çizimde, bir karakter dizisini gruplandırmanın sonuçları gösterilmektedir. Her grup için anahtar karakterdir.  
  
 ![LINQ gruplama işlemini gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 Veri öğelerini gruplamak için kullanılan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C#Sorgu Ifadesi söz dizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|GroupBy|Ortak bir özniteliği paylaşan öğeleri gruplandırır. Her grup <xref:System.Linq.IGrouping%602> nesne tarafından temsil edilir.|`group … by`<br /><br /> veya<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|Bir anahtar Seçici işlevine dayalı olarak bir <xref:System.Linq.Lookup%602> (bire çok sözlüğüne) öğe ekler.|Yok.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu Ifadesi söz dizimi örneği  
 Aşağıdaki kod örneği, bir listedeki tamsayıları, hatta veya tek olup olmadığına göre gruplamak için `group by` yan tümcesini kullanır.  
  
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
- [İç içe geçmiş grup oluşturma](../../../linq/create-a-nested-group.md)
- [Dosyaları uzantıya göre gruplama (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)
- [Sorgu sonuçlarını gruplandırma](../../../linq/group-query-results.md)
- [Gruplandırma işleminde alt sorgu gerçekleştirme](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [Grupları (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (LINQ) (C#)](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
