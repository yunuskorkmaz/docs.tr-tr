---
title: Dönüştürme veri türleri (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 374ce15b8329c02c6b496a276a40fd9a60596e1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335828"
---
# <a name="converting-data-types-c"></a>Dönüştürme veri türleri (C#)
Dönüştürme yöntemleri giriş nesnelerin türünü değiştirin.  
  
 LINQ sorgularını dönüştürme işlemlerinde çeşitli uygulamalar yararlı olur. Bazı örnekler şunlardır:  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Yöntemi, bir türün özel bir standart sorgu işleci uyarlamasını gizlemek için kullanılabilir.  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Yöntemi, LINQ sorgusu için koleksiyonları parametresiz etkinleştirmek için kullanılabilir.  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, Ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri, sorgu numaralandırılan kadar yerine onu ertelemeyi hemen sorgu yürütme zorlamak için kullanılabilir.  
  
## <a name="methods"></a>Yöntemler  
 Aşağıdaki tabloda veri türü dönüşümleri gerçekleştirmek standart sorgu işleci yöntemlerini listeler.  
  
 Bu tabloda, adları "As" başlayın dönüştürme yöntemleri kaynak koleksiyonu statik türünü değiştirme ancak bunu numaralandırmak değil. "Kaynak toplamasını ve öğeleri karşılık gelen koleksiyona koymak için" ile adları başlayan yöntemleri yazın.  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|AsEnumerable|Olarak yazılan giriş döndürür <xref:System.Collections.Generic.IEnumerable%601>.|Yok.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|(Genel) dönüştürür <xref:System.Collections.IEnumerable> (Genel) <xref:System.Linq.IQueryable>.|Yok.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Cast|Belirtilen tür için bir koleksiyonun öğelerini çevirir.|Açıkça belirtilmiş aralık değişkeni kullanın. Örneğin:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|Değerleri yeteneklerini bir belirtilen türe göre filtreler.|Yok.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|ToArray|Bir koleksiyonu bir diziye dönüştürür. Bu yöntem, sorgu yürütme zorlar.|Yok.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|Todictionary öğesini|Öğeler haline getirir bir <xref:System.Collections.Generic.Dictionary%602> bir anahtar Seçici işlevine bağlı. Bu yöntem, sorgu yürütme zorlar.|Yok.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|ToList|Bir koleksiyona dönüştüren bir <xref:System.Collections.Generic.List%601>. Bu yöntem, sorgu yürütme zorlar.|Yok.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|Öğeler haline getirir bir <xref:System.Linq.Lookup%602> (bir-çok sözlük) dayalı bir anahtar Seçici işlevdir. Bu yöntem, sorgu yürütme zorlar.|Yok.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu ifade sözdizimi örneği  
 Aşağıdaki kod örneğinde açıkça belirtilmiş aralık değişkeni bir alt türü yalnızca alt üzerinde kullanılabilir üyesi erişmeden önce türe için kullanır.  
  
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
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [from yan tümcesi](../../../../csharp/language-reference/keywords/from-clause.md)  
 [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Nasıl yapılır: LINQ (C#) ile ArrayList sorgulama](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
