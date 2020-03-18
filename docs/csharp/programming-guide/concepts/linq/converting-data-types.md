---
title: Veri Türlerini Dönüştürme (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 328c790a1a360907c91f69b3b6330b0b25eb414b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347198"
---
# <a name="converting-data-types-c"></a>Veri Türlerini Dönüştürme (C#)
Dönüştürme yöntemleri giriş nesnelerinin türünü değiştirir.

 LINQ sorgularında dönüşüm işlemleri çeşitli uygulamalarda yararlıdır. Aşağıda bazı örnekler verilmiştir:

- Yöntem, <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> bir türünün standart sorgu işlecinin özel uygulamasını gizlemek için kullanılabilir.

- Yöntem, <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> LINQ sorgusu için parametresiz koleksiyonları etkinleştirmek için kullanılabilir.

- <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> ve yöntemleri sorgu numaralandırılınkadar erteleyerek yerine hemen sorgu yürütme zorlamak için kullanılabilir.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda, veri türü dönüştürmeleri gerçekleştiren standart sorgu işleci yöntemleri listeleilmektedir.

 Adları "As" ile başlayan bu tablodaki dönüştürme yöntemleri kaynak koleksiyonun statik türünü değiştirir, ancak sıralamaz. Adları "To" ile başlayan yöntemler kaynak koleksiyonu nisbi olarak listeler ve öğeleri ilgili koleksiyon türüne koyar.

|Yöntem Adı|Açıklama|C# Sorgu İfade Sözdizimi|Daha Fazla Bilgi|
|-----------------|-----------------|---------------------------------|----------------------|
|Asenumerable|' olarak <xref:System.Collections.Generic.IEnumerable%601>yazılan girişi döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|Asqueryable|Bir (genel) <xref:System.Collections.IEnumerable> bir (genel) <xref:System.Linq.IQueryable>dönüştürür.|Geçerli değildir.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|Cast|Bir koleksiyonun öğelerini belirli bir türe atar.|Açıkça yazılan bir aralık değişkeni kullanın. Örnek:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|Oftype|Belirli bir türe döküm yeteneğine bağlı olarak değerleri filtreler.|Geçerli değildir.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|Toarray|Koleksiyonu bir diziye dönüştürür. Bu yöntem sorgu yürütmeyi zorlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|Todictionary|Öğeleri önemli <xref:System.Collections.Generic.Dictionary%602> bir seçici işlevine dayalı bir şekilde koyar. Bu yöntem sorgu yürütmeyi zorlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|Tolist|Bir koleksiyonu bir <xref:System.Collections.Generic.List%601>. Bu yöntem sorgu yürütmeyi zorlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|Tolookup|Öğeleri anahtar <xref:System.Linq.Lookup%602> seçici işlevini temel alan bir (bir-çok sözlük) içine koyar. Bu yöntem sorgu yürütmeyi zorlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Sorgu İfadesözdizimi Örneği

Aşağıdaki kod örneği, yalnızca alt türde kullanılabilen bir üyeye erişmeden önce bir türü bir alt türe atmak için açıkça yazılan bir aralık değişkeni kullanır.

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
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [fıkradan](../../../language-reference/keywords/from-clause.md)
- [LINQ Sorgu İfadeleri](../../../linq/index.md)
- [LINQ (C#) ile ArrayList nasıl sorgulanır?](./how-to-query-an-arraylist-with-linq.md)
