---
title: Veri türlerini dönüştürme (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 54ef612ad4e92058d9af4d96b7b3cde9732b2f9c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743592"
---
# <a name="converting-data-types-c"></a>Veri türlerini dönüştürme (C#)
Dönüştürme yöntemleri giriş nesnelerin türünü değiştirin.  
  
 LINQ sorguları dönüştürme işlemlerinde, çeşitli uygulamalar kullanışlıdır. Bazı örnekler aşağıda verilmiştir:  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Yöntemi, standart sorgu işleci bir türün özel uygulanışı gizlemek için kullanılabilir.  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Yöntemi, LINQ sorgusu için koleksiyonları forceseek etkinleştirmek için kullanılabilir.  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, Ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri ve sorgu numaralandırılana kadar bu erteleniyor yerine anlık sorgu yürütme zorlamak için kullanılabilir.  
  
## <a name="methods"></a>Yöntemler  
 Aşağıdaki tabloda veri türü dönüşümleri gerçekleştirmek standart sorgu işleci yöntemleri listeler.  
  
 "Statik kaynak toplama türünü değiştirebilirsiniz ancak bunu numaralandırmak değil olarak" adları ile başlayan dönüştürme yöntemleri bu tablodaki. Adları ile kaynak derlemesini öğeleri ilgili koleksiyona eklediğiniz "" başlayın ve yöntemi yazın.  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|AsEnumerable|Giriş olarak yazılan döndürür <xref:System.Collections.Generic.IEnumerable%601>.|Uygulanamaz.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|(Genel) dönüştürür <xref:System.Collections.IEnumerable> (Genel) <xref:System.Linq.IQueryable>.|Uygulanamaz.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Cast|Belirli bir koleksiyonun öğeleri çevirir.|Açıkça yazılmış bir aralık değişkeni kullanın. Örneğin:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|Değerleri belirtilen bir türe yayınlanması için kendi yeteneği bağlı olarak filtreler.|Uygulanamaz.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|ToArray|Bir koleksiyonu bir diziye dönüştürür. Bu yöntem, sorgu yürütme zorlar.|Uygulanamaz.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|ToDictionary|Bu öğeleri eklemek koyar bir <xref:System.Collections.Generic.Dictionary%602> anahtar Seçici işleve göre. Bu yöntem, sorgu yürütme zorlar.|Uygulanamaz.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|ToList|Bir koleksiyona dönüştürür bir <xref:System.Collections.Generic.List%601>. Bu yöntem, sorgu yürütme zorlar.|Uygulanamaz.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|Bu öğeleri eklemek koyar bir <xref:System.Linq.Lookup%602> (bire çok bir sözlük) tabanlı bir anahtar Seçici işlevdir. Bu yöntem, sorgu yürütme zorlar.|Uygulanamaz.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu ifade sözdizimi örneği  
 Aşağıdaki kod örneği bir açıkça yazılmış bir aralık değişkeni bir alt yalnızca alt türü üzerinde kullanılabilir olan bir üye erişmeden önce türüne için kullanır.  
  
```csharp  
class Plant  
{  
    public string Name { get; set; }  
}  
  
class CarnivorousPlant : Plant  
{  
    public string TrapType { get; set; }  
}  
  
static void Cast()  
{  
    Plant[] plants = new Plant[] {  
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },  
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },  
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },  
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }  
    };  
  
    var query = from CarnivorousPlant cPlant in plants  
                where cPlant.TrapType == "Snap Trap"  
                select cPlant;  
  
    foreach (Plant plant in query)  
        Console.WriteLine(plant.Name);  
  
    /* This code produces the following output:  
  
        Venus Fly Trap  
        Waterwheel Plant  
    */  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Linq>  
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [from yan tümcesi](../../../../csharp/language-reference/keywords/from-clause.md)  
- [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [Nasıl yapılır: LINQ (C#) ile ArrayList sorgulama](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
