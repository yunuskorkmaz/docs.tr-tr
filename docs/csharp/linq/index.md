---
title: "C 'de dil ile tümleşik sorgu (LINQ) #"
description: C# içinde dil ile tümleşik sorgu (LINQ) sağlar.
ms.date: 11/30/2016
ms.assetid: 007cc736-f5cf-4919-b99b-0c00ab2814ce
ms.openlocfilehash: b39aeffa4871d523679162497a7a4e81cf1293ca
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545962"
---
# <a name="language-integrated-query-linq"></a>Dil ile Tümleşik Sorgu (LINQ)

Dil ile tümleşik sorgu (LINQ), sorgu yeteneklerinin doğrudan C# dilinde tümleştirilmesini temel alan bir teknoloji kümesinin adıdır. Geleneksel olarak, verilere karşı sorgular derleme zamanında veya IntelliSense desteğiyle tür denetlemesi olmadan basit dizeler olarak ifade edilir. Ayrıca, her veri kaynağı türü için farklı bir sorgu dili öğrenirsiniz: SQL veritabanları, XML belgeleri, çeşitli Web Hizmetleri ve benzeri. LINQ ile sorgu, sınıflar, Yöntemler ve olaylar gibi birinci sınıf bir dil yapısıdır.

Sorgu yazan bir geliştirici için, LINQ 'nin en görünür "dil ile tümleşik" bir kısmı sorgu ifadesidir. Sorgu ifadeleri bildirime dayalı bir *sorgu söz dizimine*yazılır. Sorgu söz dizimini kullanarak veri kaynaklarında en az kodla filtreleme, sıralama ve gruplama işlemlerini gerçekleştirebilirsiniz. SQL veritabanlarındaki verileri sorgulamak ve dönüştürmek için aynı temel sorgu ifadesi desenlerini, ADO .NET veri kümelerini, XML belgelerini ve akışlarını ve .NET koleksiyonlarını kullanırsınız.

Aşağıdaki örnek, tüm sorgu işlemini gösterir. Tamamlanmış işlem, bir veri kaynağı oluşturmayı, sorgu ifadesini tanımlamayı ve sorguyu bir deyimde yürütmeyi içerir `foreach` .

[!code-csharp[csProgGuideLINQ#11](~/samples/snippets/csharp/concepts/linq/index_1.cs)]

## <a name="query-expression-overview"></a>Sorgu ifadesine genel bakış

- Sorgu ifadeleri, LINQ özellikli herhangi bir veri kaynağından verileri sorgulamak ve dönüştürmek için kullanılabilir. Örneğin, tek bir sorgu bir SQL veritabanından veri alabilir ve çıkış olarak bir XML akışı üretebilir.

- Sorgu ifadeleri çok tanıdık C# dil yapılarını kullandığından, kolayca ana öğe kullanmaktır.

- Bir sorgu ifadesindeki değişkenlerin hepsi kesin olarak türlidir, ancak çoğu durumda derleyici onu çıkardığı için türü açıkça sağlamak zorunda değilsiniz. Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

- Sorgu değişkeni üzerinde yineleme yapana kadar sorgu yürütülmez, örneğin bir `foreach` ifadede. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

- Derleme zamanında sorgu ifadeleri, C# belirtiminde belirtilen kurallara göre standart sorgu operatörü yöntemi çağrılarına dönüştürülür. Sorgu söz dizimi kullanılarak ifade edilebilir herhangi bir sorgu, yöntem sözdizimi kullanılarak da ifade edilebilir. Ancak çoğu durumda sorgu sözdizimi daha okunabilir ve kısadır. Daha fazla bilgi için bkz. [C# dil belirtimi](~/_csharplang/spec/expressions.md#query-expressions) ve [Standart sorgu işleçlerine genel bakış](../programming-guide/concepts/linq/standard-query-operators-overview.md).

- LINQ sorguları yazdığınızda bir kural olarak, gerektiğinde sorgu söz dizimini ve Yöntem sözdizimini kullanmanızı öneririz. İki farklı form arasında anlam veya performans farkı yoktur. Sorgu ifadeleri genellikle yöntem sözdiziminde yazılan denk ifadelerden daha okunabilir.

- Veya gibi bazı sorgu işlemlerinin <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Max%2A> eşdeğer sorgu ifadesi yan tümcesi yoktur ve bu nedenle bir yöntem çağrısı olarak ifade edilmesi gerekir. Yöntem sözdizimi, sorgu söz dizimi ile çeşitli şekillerde birleştirilebilir. Daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

- Sorgu ifadeleri, sorgu uygulanmış türe bağlı olarak ifade ağaçlarına veya temsilcilere derlenebilir. <xref:System.Collections.Generic.IEnumerable%601> sorgular temsilcilere derlenir. <xref:System.Linq.IQueryable> ve <xref:System.Linq.IQueryable%601> sorguları ifade ağaçlarına derlenir. Daha fazla bilgi için bkz. [ifade ağaçları](../expression-trees.md).

## <a name="next-steps"></a>Sonraki adımlar

LINQ hakkında daha fazla bilgi edinmek için [sorgu ifadesi temel](query-expression-basics.md)kavramları konusundaki bazı temel kavramları öğrenerek başlayın ve ardından ilgilendiğiniz LINQ teknolojisinin belgelerini okuyun:

- XML belgeleri: [LINQ to XML](../../standard/linq/linq-xml-overview.md)

- ADO.NET Entity Framework: [LINQ to Entities](../../framework/data/adonet/ef/language-reference/linq-to-entities.md)

- .NET koleksiyonları, dosyalar, dizeler ve benzeri: [LINQ to Objects](../programming-guide/concepts/linq/linq-to-objects.md)

Genel olarak LINQ hakkında daha ayrıntılı bilgi edinmek için bkz. [C# ' de LINQ](linq-in-csharp.md).

C# ' de LINQ ile çalışmaya başlamak için bkz. [LINQ Ile çalışma](../tutorials/working-with-linq.md)öğreticisi.
