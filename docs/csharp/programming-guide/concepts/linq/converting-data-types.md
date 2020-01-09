---
title: Veri türlerini dönüştürme (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 328c790a1a360907c91f69b3b6330b0b25eb414b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347198"
---
# <a name="converting-data-types-c"></a>Veri türlerini dönüştürme (C#)
Dönüştürme yöntemleri giriş nesnelerinin türünü değiştirir.

 LINQ sorgularındaki dönüştürme işlemleri çeşitli uygulamalarda yararlıdır. Aşağıda bazı örnekler verilmiştir:

- <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> yöntemi, bir türün standart sorgu işlecinin özel uygulamasını gizlemek için kullanılabilir.

- <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> yöntemi, LINQ sorgulaması için parametreli olmayan koleksiyonları etkinleştirmek üzere kullanılabilir.

- <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri, sorgu numaralandırılana kadar, sorgu yürütmeye zorlamak yerine hemen bu işlemi yapmak için kullanılabilir.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda, veri türü dönüştürmeleri gerçekleştiren standart sorgu işleci yöntemleri listelenmektedir.

 Bu tablodaki, adları "as" ile başlayan dönüştürme yöntemleri, kaynak koleksiyonun statik türünü değiştirir ancak onu numaralandırmaz. Adları "to" ile başlayan Yöntemler, kaynak koleksiyonu numaralandırır ve öğeleri karşılık gelen koleksiyon türüne koyar.

|Yöntem adı|Açıklama|C#Sorgu Ifadesi söz dizimi|Daha fazla bilgi|
|-----------------|-----------------|---------------------------------|----------------------|
|Asılabilir|<xref:System.Collections.Generic.IEnumerable%601>olarak yazılan girişi döndürür.|Yok.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|AsQueryable|Bir (genel) <xref:System.Collections.IEnumerable> bir (genel) <xref:System.Linq.IQueryable>dönüştürür.|Yok.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|Cast|Bir koleksiyonun öğelerini belirtilen bir türe yayınlar.|Açıkça yazılmış bir Aralık değişkeni kullanın. Örneğin:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|OfType|Değerleri, belirli bir türe atama becerisine bağlı olarak filtreler.|Yok.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|toArray|Bir koleksiyonu bir diziye dönüştürür. Bu yöntem sorgu yürütmeyi zorlar.|Yok.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|ToDictionary|Öğeleri bir anahtar Seçici işlevine göre <xref:System.Collections.Generic.Dictionary%602> koyar. Bu yöntem sorgu yürütmeyi zorlar.|Yok.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|toList|Bir koleksiyonu bir <xref:System.Collections.Generic.List%601>dönüştürür. Bu yöntem sorgu yürütmeyi zorlar.|Yok.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|ToLookup|Öğeleri bir anahtar Seçici işlevine göre bir <xref:System.Linq.Lookup%602> (bire çok sözlüğüne) koyar. Bu yöntem sorgu yürütmeyi zorlar.|Yok.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Sorgu Ifadesi söz dizimi örneği

Aşağıdaki kod örneği, yalnızca alt tür üzerinde kullanılabilir olan bir üyeye erişmeden önce bir türü bir alt türe dönüştürmek için açıkça yazılmış bir Aralık değişkeni kullanır.

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

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)
- [from yan tümcesi](../../../language-reference/keywords/from-clause.md)
- [LINQ sorgu Ifadeleri](../../../linq/index.md)
- [LINQ (C#) ile ArrayList 'i sorgulama](./how-to-query-an-arraylist-with-linq.md)
