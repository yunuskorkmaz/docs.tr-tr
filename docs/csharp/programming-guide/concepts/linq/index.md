---
title: Dil-Tümleşik Sorgu (LINQ) (C#)
ms.date: 02/02/2017
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
ms.openlocfilehash: a2e53d6c7f4d24fd57b1f91c1428b8341386b6f9
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463893"
---
# <a name="language-integrated-query-linq"></a>Dil ile Tümleşik Sorgu (LINQ)

Dil-Tümleşik Sorgu (LINQ), sorgu yeteneklerinin doğrudan C# diline entegrasyonuna dayalı bir dizi teknolojinin adıdır. Geleneksel olarak, verilere karşı sorgular derleme zamanında veya IntelliSense desteğinde tür denetimi olmadan basit dizeleri olarak ifade edilir. Ayrıca, her veri kaynağı türü için farklı bir sorgu dili öğrenmeniz gerekir: SQL veritabanları, XML belgeleri, çeşitli Web hizmetleri ve benzeri. LINQ ile sorgu, sınıflar, yöntemler, olaylar gibi birinci sınıf bir dil yapısıdır. Dil anahtar kelimeleri ve tanıdık işleçler kullanarak nesnelerin güçlü bir şekilde yazılan koleksiyonlarına karşı sorgular yazarsınız. LINQ teknoloji ailesi nesneler (LINQ to Objects), ilişkisel veritabanları (LINQ-SQL) ve XML (LINQ-XML) için tutarlı bir sorgu deneyimi sağlar.

Sorgu yazan bir geliştirici için LINQ'nun en görünür "dil tümleşik" bölümü sorgu ifadesidir. Sorgu ifadeleri bildirimsel sorgu *sözdiziminde*yazılır. Sorgu sözdizimini kullanarak, veri kaynaklarında en az kodla filtreleme, sıralama ve gruplandırma işlemleri gerçekleştirebilirsiniz. SQL veritabanlarında, veri kümelerinde, XML belgeleri ve akışlarına ve .NET koleksiyonlarına ADO.NET verileri sorgulamak ve dönüştürmek için aynı temel sorgu ifade desenlerini kullanırsınız.

SQL Server veritabanları, XML belgeleri, ADO.NET Datasets ve destekleyen <xref:System.Collections.IEnumerable> nesnelerin veya genel <xref:System.Collections.Generic.IEnumerable%601> arabirimin herhangi bir koleksiyon için C# linq sorguları yazabilirsiniz. LINQ desteği, birçok Web hizmeti ve diğer veritabanı uygulamaları için üçüncü taraflarca da sağlanır.

Aşağıdaki örnekte tam sorgu işlemi gösterilmektedir. Tam işlem, bir veri kaynağı oluşturmayı, sorgu ifadesini tanımlamayı `foreach` ve bir deyimdeki sorguyu yürütmeyi içerir.

[!code-csharp[csProgGuideLINQ#11](~/samples/snippets/csharp/concepts/linq/index_1.cs)]

Visual Studio'dan alınan aşağıdaki resimde, tam tür denetimi ve IntelliSense desteğiyle hem C# hem de Visual Basic veritabanında bir SQL Server veritabanına karşı kısmen tamamlanmış bir LINQ sorgusu gösterilmektedir:

![Intellisense ile linq sorgusunu gösteren diyagram.](./media/introduction-to-linq/linq-query-intellisense.png)

## <a name="query-expression-overview"></a>Sorgu ifadeye genel bakış

- Sorgu ifadeleri, linq özellikli herhangi bir veri kaynağından gelen verileri sorgulamak ve dönüştürmek için kullanılabilir. Örneğin, tek bir sorgu bir SQL veritabanından veri alabilir ve çıktı olarak bir XML akışı üretebilir.
- Sorgu ifadelerinde ustalaşmak kolaydır, çünkü birçok tanıdık C# dil yapısı kullanırlar.
- Bir sorgu ifadesindeki değişkenlerin tümü güçlü bir şekilde yazılır, ancak çoğu durumda derleyici bunu çıkarabileceğinden türü açıkça sağlamanız gerekmez. Daha fazla bilgi için [LINQ sorgu işlemlerinde tür ilişkileri'ne](type-relationships-in-linq-query-operations.md)bakın.
- Bir sorgu, örneğin bir `foreach` deyimdeki sorgu değişkeni üzerinde yinelene kadar yürütülmez. Daha fazla bilgi için [LINQ sorgularına giriş etüt ünt.'e](introduction-to-linq-queries.md)bakın.
- Derleme zamanında, sorgu ifadeleri C# belirtiminde belirtilen kurallara göre Standart Sorgu Operatörü yöntemi çağrılarına dönüştürülür. Sorgu sözdizimi kullanılarak ifade edilebilen herhangi bir sorgu, yöntem sözdizimi kullanılarak da ifade edilebilir. Ancak, çoğu durumda sorgu sözdizimi daha okunabilir ve kısadır. Daha fazla bilgi için [C# dil belirtimi](~/_csharplang/spec/expressions.md#query-expressions) ve [Standart sorgu operatörlerine genel bakış alabakın.](standard-query-operators-overview.md)
- KURAL olarak LINQ sorgularını yazarken, sorgu sözdizimini mümkün olduğunda kullanmanızı ve gerektiğinde sözdizimini kullanmanızı öneririz. İki farklı form arasında anlamsal veya performans farkı yoktur. Sorgu ifadeleri genellikle yöntem sözdiziminde yazılmış eşdeğer ifadelerden daha okunabilir.
- Bazı sorgu işlemleri, <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Max%2A>gibi veya , eşdeğer sorgu ifade yan tümcesi var ve bu nedenle bir yöntem çağrısı olarak ifade edilmelidir. Yöntem sözdizimi sorgu sözdizimi ile çeşitli şekillerde birleştirilebilir. Daha fazla bilgi için [LINQ'daki Sorgu sözdizimi ve yöntem sözdizimi'ne](query-syntax-and-method-syntax-in-linq.md)bakın.
- Sorgu ifadeleri, sorgunun uygulandığı türe bağlı olarak ifade ağaçlarına veya temsilcilere derlenebilir. <xref:System.Collections.Generic.IEnumerable%601>sorgular temsilcilere derlenir. <xref:System.Linq.IQueryable>ve <xref:System.Linq.IQueryable%601> sorgular ifade ağaçları için derlenir. Daha fazla bilgi için Bkz. [İfade ağaçları.](../../../expression-trees.md)

## <a name="next-steps"></a>Sonraki adımlar

LINQ hakkında daha fazla bilgi edinmek için Sorgu [ifade temelleri'ndeki](../../../linq/query-expression-basics.md)bazı temel kavramlara aşina olarak başlayın ve ardından ilgilendiğiniz LINQ teknolojisine ait belgeleri okuyun:

- XML belgeleri: [LINQ xml için](linq-to-xml-overview.md)  
- ADO.NET Entity Framework: [LINQ varlıklara](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)
- .NET koleksiyonları, dosyalar, dizeleri vb: [LINQ nesnelere](linq-to-objects.md)

Genel olarak LINQ hakkında daha derin bir anlayış kazanmak için [C# 'daki LINQ'ya](../../../linq/linq-in-csharp.md)bakın.

C#'da LINQ ile çalışmaya başlamak için, [LINQ ile çalışma](../../../tutorials/working-with-linq.md)öğreticisine bakın.
