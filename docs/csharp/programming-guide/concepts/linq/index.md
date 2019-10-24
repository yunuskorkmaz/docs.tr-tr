---
title: Dil ile tümleşik sorgu (LINQ) (C#)
ms.date: 02/02/2017
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
ms.openlocfilehash: d75c34cd63eb439203ef6757e62e18936eb3606a
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773915"
---
# <a name="language-integrated-query-linq"></a>Dil ile Tümleşik Sorgu (LINQ)

Dil ile tümleşik sorgu (LINQ), sorgu yeteneklerinin doğrudan C# dile tümleştirilmesine dayalı bir teknoloji kümesinin adıdır. Geleneksel olarak, verilere karşı sorgular derleme zamanında veya IntelliSense desteğiyle tür denetlemesi olmadan basit dizeler olarak ifade edilir. Ayrıca, her veri kaynağı türü için farklı bir sorgu dili öğrenirsiniz: SQL veritabanları, XML belgeleri, çeşitli Web Hizmetleri ve benzeri. LINQ ile sorgu, sınıflar, Yöntemler ve olaylar gibi birinci sınıf bir dil yapısıdır. Dil anahtar sözcükleri ve tanıdık işleçleri kullanarak, türü kesin belirlenmiş nesne koleksiyonlara karşı sorgular yazarsınız. LINQ teknolojileri, nesneler (LINQ to Objects), ilişkisel veritabanları (LINQ to SQL) ve XML (LINQ to XML) için tutarlı bir sorgu deneyimi sağlar.

Sorgu yazan bir geliştirici için, LINQ 'nin en görünür "dil ile tümleşik" bir kısmı sorgu ifadesidir. Sorgu ifadeleri bildirime dayalı bir *sorgu söz dizimine*yazılır. Sorgu söz dizimini kullanarak veri kaynaklarında en az kodla filtreleme, sıralama ve gruplama işlemlerini gerçekleştirebilirsiniz. SQL veritabanlarındaki verileri sorgulamak ve dönüştürmek için aynı temel sorgu ifadesi desenlerini, ADO .NET veri kümelerini, XML belgelerini ve akışlarını ve .NET koleksiyonlarını kullanırsınız.

SQL Server veritabanları, XML belgeleri, C# ADO.NET veri kümeleri ve <xref:System.Collections.IEnumerable> ya da genel <xref:System.Collections.Generic.IEnumerable%601> arabirimini destekleyen herhangi bir nesne KOLEKSIYONU için LINQ sorguları yazabilirsiniz. Ayrıca, LINQ desteği birçok Web hizmeti ve diğer veritabanı uygulamaları için üçüncü taraflar tarafından da sağlanır.

Aşağıdaki örnek, tüm sorgu işlemini gösterir. Tamamlanmış işlem, bir veri kaynağı oluşturmayı, sorgu ifadesini tanımlamayı ve sorguyu `foreach` deyiminde yürütmeyi içerir.

[!code-csharp[csProgGuideLINQ#11](~/samples/snippets/csharp/concepts/linq/index_1.cs)]

Visual Studio 'dan aşağıdaki çizimde, hem SQL Server hem C# de tam tür denetimi ve ıntellisense desteğiyle Visual Basic bir veritabanına karşı kısmen tamamlanmış bir LINQ sorgusu gösterilmektedir:

![IntelliSense ile bir LINQ sorgusu gösteren diyagram.](./media/introduction-to-linq/linq-query-intellisense.png)

## <a name="query-expression-overview"></a>Sorgu ifadesine genel bakış

- Sorgu ifadeleri, LINQ özellikli herhangi bir veri kaynağından verileri sorgulamak ve dönüştürmek için kullanılabilir. Örneğin, tek bir sorgu bir SQL veritabanından veri alabilir ve çıkış olarak bir XML akışı üretebilir.
- Sorgu ifadeleri çok tanıdık C# dil yapıları kullandıkları için kolayca ana öğe kullanmaktır.
- Bir sorgu ifadesindeki değişkenlerin hepsi kesin olarak türlidir, ancak çoğu durumda derleyici onu çıkardığı için türü açıkça sağlamak zorunda değilsiniz. Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](type-relationships-in-linq-query-operations.md).
- Sorgu değişkeni üzerinde yineleme yapana kadar sorgu yürütülmez, örneğin, bir `foreach` bildiriminde. Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş](introduction-to-linq-queries.md).
- Derleme zamanında sorgu ifadeleri, C# belirtimde belirtilen kurallara göre standart sorgu operatörü yöntemi çağrılarına dönüştürülür. Sorgu söz dizimi kullanılarak ifade edilebilir herhangi bir sorgu, yöntem sözdizimi kullanılarak da ifade edilebilir. Ancak çoğu durumda sorgu sözdizimi daha okunabilir ve kısadır. Daha fazla bilgi için bkz [ C# . dil belirtimi](~/_csharplang/spec/expressions.md#query-expressions) ve [Standart sorgu işleçlerine genel bakış](standard-query-operators-overview.md).
- LINQ sorguları yazdığınızda bir kural olarak, gerektiğinde sorgu söz dizimini ve Yöntem sözdizimini kullanmanızı öneririz. İki farklı form arasında anlam veya performans farkı yoktur. Sorgu ifadeleri genellikle yöntem sözdiziminde yazılan denk ifadelerden daha okunabilir.
- @No__t_0 veya <xref:System.Linq.Enumerable.Max%2A> gibi bazı sorgu işlemlerinde denk bir sorgu ifadesi yan tümcesi yoktur ve bu nedenle bir yöntem çağrısı olarak ifade edilmesi gerekir. Yöntem sözdizimi, sorgu söz dizimi ile çeşitli şekillerde birleştirilebilir. Daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](query-syntax-and-method-syntax-in-linq.md).
- Sorgu ifadeleri, sorgu uygulanmış türe bağlı olarak ifade ağaçlarına veya temsilcilere derlenebilir. <xref:System.Collections.Generic.IEnumerable%601> sorguları temsilcilere derlenir. <xref:System.Linq.IQueryable> ve <xref:System.Linq.IQueryable%601> sorguları, ifade ağaçlarına derlenir. Daha fazla bilgi için bkz. [ifade ağaçları](../../../expression-trees.md).

## <a name="next-steps"></a>Sonraki adımlar

LINQ hakkında daha fazla bilgi edinmek için [sorgu ifadesi temel](../../../linq/query-expression-basics.md)kavramları konusundaki bazı temel kavramları öğrenerek başlayın ve ardından ilgilendiğiniz LINQ teknolojisinin belgelerini okuyun:

- XML belgeleri: [LINQ to XML](linq-to-xml.md)  
- ADO.NET Entity Framework: [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)
- .NET koleksiyonları, dosyalar, dizeler ve benzeri: [LINQ to Objects](linq-to-objects.md)

Genel olarak LINQ hakkında daha ayrıntılı bilgi edinmek için bkz. [LINQ ın C# ](../../../linq/linq-in-csharp.md).

LINQ C#ile çalışmaya başlamak için bkz. [LINQ ile çalışma](../../../tutorials/working-with-linq.md)öğreticisi.
