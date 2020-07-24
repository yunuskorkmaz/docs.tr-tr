---
title: Dil ile tümleşik sorgu (LINQ) (C#)
description: Dil ile tümleşik sorgular (LINQs) hakkında bilgi edinin ve tam sorgu işleminin bir örneğini gözden geçirin.
ms.date: 02/02/2017
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
ms.openlocfilehash: 6c8844c387177ce858b63a52b1f5c7246b570beb
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103420"
---
# <a name="language-integrated-query-linq"></a>Dil ile Tümleşik Sorgu (LINQ)

Dil ile tümleşik sorgu (LINQ), sorgu yeteneklerinin doğrudan C# dilinde tümleştirilmesini temel alan bir teknoloji kümesinin adıdır. Geleneksel olarak, verilere karşı sorgular derleme zamanında veya IntelliSense desteğiyle tür denetlemesi olmadan basit dizeler olarak ifade edilir. Ayrıca, her veri kaynağı türü için farklı bir sorgu dili öğrenirsiniz: SQL veritabanları, XML belgeleri, çeşitli Web Hizmetleri ve benzeri. LINQ ile sorgu, sınıflar, Yöntemler ve olaylar gibi birinci sınıf bir dil yapısıdır. Dil anahtar sözcükleri ve tanıdık işleçleri kullanarak, türü kesin belirlenmiş nesne koleksiyonlara karşı sorgular yazarsınız. LINQ teknolojileri, nesneler (LINQ to Objects), ilişkisel veritabanları (LINQ to SQL) ve XML (LINQ to XML) için tutarlı bir sorgu deneyimi sağlar.

Sorgu yazan bir geliştirici için, LINQ 'nin en görünür "dil ile tümleşik" bir kısmı sorgu ifadesidir. Sorgu ifadeleri bildirime dayalı bir *sorgu söz dizimine*yazılır. Sorgu söz dizimini kullanarak veri kaynaklarında en az kodla filtreleme, sıralama ve gruplama işlemlerini gerçekleştirebilirsiniz. SQL veritabanlarındaki verileri sorgulamak ve dönüştürmek için aynı temel sorgu ifade desenlerini kullanın, ADO.NET veri kümeleri, XML belgeleri ve akışlar ve .NET koleksiyonları.

SQL Server veritabanları, XML belgeleri, ADO.NET veri kümeleri ve ya da genel arabirimi destekleyen herhangi bir nesne koleksiyonu Için C# dilinde LINQ sorguları yazabilirsiniz <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> . Ayrıca, LINQ desteği birçok Web hizmeti ve diğer veritabanı uygulamaları için üçüncü taraflar tarafından da sağlanır.

Aşağıdaki örnek, tüm sorgu işlemini gösterir. Tamamlanmış işlem, bir veri kaynağı oluşturmayı, sorgu ifadesini tanımlamayı ve sorguyu bir deyimde yürütmeyi içerir `foreach` .

[!code-csharp[csProgGuideLINQ#11](~/samples/snippets/csharp/concepts/linq/index_1.cs)]

Visual Studio 'dan aşağıdaki çizimde, hem C# ' de SQL Server veritabanında hem de tam tür denetimi ve IntelliSense desteğiyle Visual Basic kısmen tamamlanmış bir LINQ sorgusu gösterilmektedir:

![IntelliSense ile bir LINQ sorgusu gösteren diyagram.](./media/introduction-to-linq/linq-query-intellisense.png)

## <a name="query-expression-overview"></a>Sorgu ifadesine genel bakış

- Sorgu ifadeleri, LINQ özellikli herhangi bir veri kaynağından verileri sorgulamak ve dönüştürmek için kullanılabilir. Örneğin, tek bir sorgu bir SQL veritabanından veri alabilir ve çıkış olarak bir XML akışı üretebilir.
- Sorgu ifadeleri çok tanıdık C# dil yapılarını kullandığından, kolayca ana öğe kullanmaktır.
- Bir sorgu ifadesindeki değişkenlerin hepsi kesin olarak türlidir, ancak çoğu durumda derleyici onu çıkardığı için türü açıkça sağlamak zorunda değilsiniz. Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](type-relationships-in-linq-query-operations.md).
- Sorgu değişkeni üzerinde yineleme yapana kadar sorgu yürütülmez, örneğin bir `foreach` ifadede. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş](introduction-to-linq-queries.md).
- Derleme zamanında sorgu ifadeleri, C# belirtiminde belirtilen kurallara göre standart sorgu operatörü yöntemi çağrılarına dönüştürülür. Sorgu söz dizimi kullanılarak ifade edilebilir herhangi bir sorgu, yöntem sözdizimi kullanılarak da ifade edilebilir. Ancak çoğu durumda sorgu sözdizimi daha okunabilir ve kısadır. Daha fazla bilgi için bkz. [C# dil belirtimi](~/_csharplang/spec/expressions.md#query-expressions) ve [Standart sorgu işleçlerine genel bakış](standard-query-operators-overview.md).
- LINQ sorguları yazdığınızda bir kural olarak, gerektiğinde sorgu söz dizimini ve Yöntem sözdizimini kullanmanızı öneririz. İki farklı form arasında anlam veya performans farkı yoktur. Sorgu ifadeleri genellikle yöntem sözdiziminde yazılan denk ifadelerden daha okunabilir.
- Veya gibi bazı sorgu işlemlerinin <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Max%2A> eşdeğer sorgu ifadesi yan tümcesi yoktur ve bu nedenle bir yöntem çağrısı olarak ifade edilmesi gerekir. Yöntem sözdizimi, sorgu söz dizimi ile çeşitli şekillerde birleştirilebilir. Daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](query-syntax-and-method-syntax-in-linq.md).
- Sorgu ifadeleri, sorgu uygulanmış türe bağlı olarak ifade ağaçlarına veya temsilcilere derlenebilir. <xref:System.Collections.Generic.IEnumerable%601>sorgular temsilcilere derlenir. <xref:System.Linq.IQueryable>ve <xref:System.Linq.IQueryable%601> sorguları ifade ağaçlarına derlenir. Daha fazla bilgi için bkz. [ifade ağaçları](../../../expression-trees.md).

## <a name="next-steps"></a>Sonraki adımlar

LINQ hakkında daha fazla bilgi edinmek için [sorgu ifadesi temel](../../../linq/query-expression-basics.md)kavramları konusundaki bazı temel kavramları öğrenerek başlayın ve ardından ilgilendiğiniz LINQ teknolojisinin belgelerini okuyun:

- XML belgeleri: [LINQ to XML](linq-to-xml-overview.md)  
- ADO.NET Entity Framework: [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)
- .NET koleksiyonları, dosyalar, dizeler ve benzeri: [LINQ to Objects](linq-to-objects.md)

Genel olarak LINQ hakkında daha ayrıntılı bilgi edinmek için bkz. [C# ' de LINQ](../../../linq/linq-in-csharp.md).

C# ' de LINQ ile çalışmaya başlamak için bkz. [LINQ Ile çalışma](../../../tutorials/working-with-linq.md)öğreticisi.
