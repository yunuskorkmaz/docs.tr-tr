---
title: Verileri gruplandırma (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: a85babc43f673711fe1bdfa5cec1836a5073c785
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807777"
---
# <a name="grouping-data-c"></a>Verileri gruplandırma (C#)
Gruplandırma, böylece ortak bir özniteliği her gruptaki öğe paylaştırmak gruplar halinde veri yerleştirme işlemi için ifade eder.  
  
 Aşağıdaki çizimde, bir karakter dizisi gruplandırma sonuçlarını gösterir. Her grup için anahtar karakterdir.  
  
 ![LINQ gruplandırma işleminde gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 Veri öğeleri gruplayın standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Gruplandırma ölçütü|Sık kullanılan bir özniteliği paylaşan öğeleri gruplandırır. Her grubu tarafından temsil edilen bir <xref:System.Linq.IGrouping%602> nesne.|`group … by`<br /><br /> -veya-<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|İçine bir öğe ekler; bir <xref:System.Linq.Lookup%602> (bire çok bir sözlük) tabanlı bir anahtar Seçici işlevdir.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu ifade sözdizimi örneği  
 Aşağıdaki kod örneğinde `group by` yan tümcesi bir liste çift veya tek sayı olup olmadıkları göre grup dizisidir.  
  
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
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [group yan tümcesi](../../../../csharp/language-reference/keywords/group-clause.md)
- [Nasıl yapılır: İç içe geçmiş grup oluşturma](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)
- [Nasıl yapılır: Dosyaları (LINQ) uzantıya göre gruplama (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [Nasıl yapılır: Sorgu sonuçlarını gruplandırma](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)
- [Nasıl yapılır: Gruplandırma işleminde alt sorgu gerçekleştirme](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
- [Nasıl yapılır: Gruplar (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
