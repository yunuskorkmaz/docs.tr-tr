---
title: Dil ile tümleşik sorgu (LINQ) (C#)
ms.date: 02/02/2017
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
ms.openlocfilehash: fbd73d879a3e2fe4cc38d6c8548434d21ca06467
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64597078"
---
# <a name="language-integrated-query-linq"></a>Dil ile Tümleşik Sorgu (LINQ)

Dil ile tümleşik sorgu (LINQ) tümleştirmesini sorgu özellikleri doğrudan C# dilinin temel teknoloji kümesi adıdır. Geleneksel olarak, veri sorguları zaman veya IntelliSense desteği olmadan tür denetimini en basit dizeler derleme olarak ifade edilir. Ayrıca, her veri kaynağı türü için bir farklı bir sorgu dili öğrenmek zorunda: SQL veritabanlarını, XML belgeleri, çeşitli Web Hizmetleri ve benzeri. LINQ ile olduğu gibi sınıflar, yöntemler, olaylar bir birinci sınıf dil yapısı sorgu.

Sorguları Yazar bir geliştirici için en çok görünen "dil ile tümleşik" LINQ sorgu ifadesi parçasıdır. Sorgu ifadeleri bildirim temelli yazılır *sorgu söz dizimi*. Sorgu söz dizimi kullanarak, filtreleme, sıralama ve gruplandırma işlemlerinin en az veri kaynaklarında kod gerçekleştirebilirsiniz. Aynı temel sorgu ifade desenleri, sorgu ve veri SQL veritabanları, ADO .NET veri kümeleri, .NET koleksiyonları, XML belgeleri ve akışları dönüştürmek için kullanın.

Aşağıdaki örnek, tam bir sorgu işlemi gösterilmektedir. Veri kaynağı oluşturma, sorgu ifadesi tanımlama ve sorgu yürütme işlemi tamamlamak içeren bir `foreach` deyimi.

[!code-csharp[csProgGuideLINQ#11](../../../../../samples/snippets/csharp/concepts/linq/index_1.cs)]

## <a name="query-expression-overview"></a>Sorgu ifadesi genel bakış

- Sorgu ifadeleri, sorgulama ve herhangi bir LINQ özellikli veri kaynağından verileri dönüştürmek için kullanılabilir. Örneğin, tek bir sorgu, bir SQL veritabanından veri almak ve çıktı olarak bir XML akışı üretir.  
  
- Sorgu ifadeleri, alışık olduğunuz birçok C# dil yapılarının kullandıkları için ana kolaydır.  
  
- Çoğu durumda derleyici çıkarsayabilir türü açıkça sağlamanız gerekmez ancak bir sorgu ifadesinde değişkenleri tüm, kesin olarak belirlenmiştir. Daha fazla bilgi için [tür ilişkileri LINQ Sorgu işlemleri](type-relationships-in-linq-query-operations.md).  
  
- Sorgu değişkeni üzerinde yineleme kadar bir sorgu yürütülmedi Örneğin, bir `foreach` deyimi. Daha fazla bilgi için [LINQ sorgularına giriş](introduction-to-linq-queries.md).  
  
- Derleme zamanında sorgu ifadeleri C# belirtiminde ortaya konan kurallara göre standart sorgu işleci yöntem çağrılarını dönüştürülür. Sorgu söz dizimi kullanarak ifade edilebilir herhangi bir sorgu yöntemi söz dizimi kullanılarak da belirtilebilir. Ancak, çoğu durumda, daha okunabilir ve kısa sorgu söz dizimi. Daha fazla bilgi için [C# dil belirtimi](~/_csharplang/spec/expressions.md#query-expressions) ve [standart sorgu işleçlerine genel bakış](standard-query-operators-overview.md).  
  
- LINQ sorguları yazarken bir kural olarak, mümkün olduğunda sorgu sözdizimi ve yöntem sözdizimi gerektiğinde kullanmanızı öneririz. Yok Hayır anlam veya iki farklı formlar arasında performans farkı. Sorgu ifadeleri olan genellikle daha fazla eşdeğer ifadelerin yöntemi sözdizimi yazılan daha okunabilir.  
  
- Bazı sorgu işlemleri gibi <xref:System.Linq.Enumerable.Count%2A> veya <xref:System.Linq.Enumerable.Max%2A>, hiçbir eşdeğer sorgu ifade yan tümcesine sahip ve bu nedenle bir yöntem çağrısının ifade edilmelidir. Yöntem sözdizimi, çeşitli yollarla sorgu söz dizimi ile birleştirilebilir. Daha fazla bilgi için [sorgu sözdizimi ve yöntem sözdizimi LINQ](query-syntax-and-method-syntax-in-linq.md).  
  
- Sorgu ifadeleri, ifade ağaçları veya Temsilciler, sorgu uygulanan türüne bağlı olarak derlenebilir. <xref:System.Collections.Generic.IEnumerable%601> sorgular için temsilciler derlenir. <xref:System.Linq.IQueryable> ve <xref:System.Linq.IQueryable%601> sorguları, ifade ağaçlarına derlenir. Daha fazla bilgi için [ifade ağaçları](../../../expression-trees.md).  

## <a name="next-steps"></a>Sonraki adımlar

LINQ hakkında daha fazla bilgi edinmek için bazı temel kavramları hakkında bilgi sahibi olma Başlat [sorgu ifadesi Temelleri](../../../linq/query-expression-basics.md), ve ardından, olduğu ilgilenen LINQ teknolojisi için belgeleri okuyun:   
- XML belgeleri: [LINQ to XML](linq-to-xml.md)  
  
- ADO.NET varlık çerçevesi: [LINQ to entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)  
  
- .NET koleksiyonları, dosyaları, dizeleri ve bu şekilde devam eder: [Nesnelere LINQ](linq-to-objects.md)

Bir derin LINQ genel olarak anlaşılması için bkz: [C# üzerinde LINQ](../../../linq/linq-in-csharp.md).

C# üzerinde LINQ ile çalışmaya başlamak için öğreticiye bakın [LINQ ile çalışma](../../../tutorials/working-with-linq.md).
