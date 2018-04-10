---
title: Dil ile tümleşik sorgu (LINQ) (C#)
ms.custom: ''
ms.date: 02/02/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0a721bba36eb1ed4ae94b99e25a1dcce33faef6e
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2018
---
# <a name="language-integrated-query-linq"></a>Dil ile tümleşik sorgu (LINQ)

Dil ile tümleşik sorgu (LINQ) C# dili doğrudan sorgu özellikleri tümleştirme temel teknoloji adıdır. Geleneksel olarak, veri sorguları zaman veya IntelliSense desteği tür adresindeki denetlemesi olmadan basit dizeler derleme olarak ifade edilir. Ayrıca, her veri kaynağı türü için farklı sorgu dili öğrenmeniz gerekir: SQL veritabanları, XML belgeleri, çeşitli Web Hizmetleri ve benzeri. LINQ ile bir sorgu sınıfları, yöntemleri, olayları gibi bir birinci sınıf dil yapısı ' dir.

Sorguları Yazar bir geliştirici için en görünür "dil ile tümleşik" LINQ sorgu ifadesi bir parçasıdır. Sorgu ifadeleri bir tanımlayıcı yazılır *sorgu sözdizimi*. Sorgu sözdizimi kullanılarak filtreleme, sıralama ve kod en az veri kaynaklarında gruplandırma işlemleri gerçekleştirebilir. Aynı temel sorgu ifade desenleri sorgu ve veri SQL veritabanları, ADO .NET veri kümeleri, .NET koleksiyonları, XML belgelerini ve akışlar dönüştürmek için kullanın.

Aşağıdaki örnekte, tam bir sorgu işlemi gösterilmektedir. Veri kaynağı oluşturma, sorgu ifadesi tanımlama ve sorgu yürütme işlemi tamamlamak içeren bir `foreach` deyimi.

[!code-csharp[csProgGuideLINQ#11](../../../../../samples/snippets/csharp/concepts/linq/index_1.cs)]

## <a name="query-expression-overview"></a>Sorgu ifadesi genel bakış

-   Sorgu ifadeleri, sorgu ve tüm LINQ etkin veri kaynağı dönüştürmek için kullanılabilir. Örneğin, tek bir sorgu, bir SQL veritabanından veri almak ve bir XML akışı çıktı olarak üretir.  
  
-   Sorgu ifadeleri tanıdık birçok C# dil yapıları kullandığından ana kolaydır.  
  
-   Çoğu durumda derleyici Infer çünkü türü açıkça sağlamanız gerekmez ancak bir sorgu ifadesinde değişkenleri tüm kesinlikle, yazılmalıdır. Daha fazla bilgi için bkz: [tür ilişkileri LINQ Sorgu işlemleri](type-relationships-in-linq-query-operations.md).  
  
-   Sorgu değişkeni yineleme kadar bir sorgu yürütülmedi Örneğin, bir `foreach` deyimi. Daha fazla bilgi için bkz: [LINQ sorgularına giriş](introduction-to-linq-queries.md).  
  
-   Derleme zamanında sorgu ifadeleri standart sorgu işleci yöntem çağrılarını İleri C# belirtiminde ayarlamak kurallarına göre dönüştürülür. Sorgu sözdizimi kullanılarak ifade herhangi bir sorgu yöntem sözdizimi kullanılarak da belirtilebilir. Bununla birlikte, çoğu durumda, daha okunabilir ve kısa sorgu sözdizimi. Daha fazla bilgi için bkz: [C# dil belirtimi](../../../language-reference/language-specification/index.md) ve [standart sorgu işleçlerine genel bakış](standard-query-operators-overview.md).  
  
-   LINQ sorguları yazma, bir kural olarak, mümkün olduğunda sorgu sözdizimi ve yöntem sözdizimi gerektiğinde kullanmanızı öneririz. Yoksa Hayır anlamsal veya performans iki farklı form arasında fark. Sorgu ifadeleri olan genellikle daha yöntemi sözdiziminde yazılan eşdeğer ifadeleri daha okunabilir.  
  
-   Bazı sorgu işlemleri gibi <xref:System.Linq.Enumerable.Count%2A> veya <xref:System.Linq.Enumerable.Max%2A>, hiçbir eşdeğer sorgu ifadesi yan tümcesi varsa ve bu nedenle bir yöntem çağrısı ifade edilmesi gerekir. Çeşitli şekillerde sorgu sözdizimi ile yöntem sözdizimi birleştirilebilir. Daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](query-syntax-and-method-syntax-in-linq.md).  
  
-   Sorgu ifadeleri ifade ağaçları veya sorgu uygulandığı türüne bağlı olarak temsilciler derlenebilir. <xref:System.Collections.Generic.IEnumerable%601> sorguları temsilcileri derlenir. <xref:System.Linq.IQueryable> ve <xref:System.Linq.IQueryable%601> sorgular için ifade ağaçları derlenir. Daha fazla bilgi için bkz: [ifade ağaçları](../../../expression-trees.md).  

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla ayrıntı LINQ hakkında bilgi edinmek için bazı temel kavramları hakkında bilgi sahibi olma olarak Başlat [sorgu ifadesi Temelleri](../../../linq/query-expression-basics.md), ve hangi, ilgi LINQ teknolojisi belgelerine bakın:   
-   XML belgeleri: [LINQ-XML](linq-to-xml.md)  
  
-   ADO.NET Entity Framework: [LINQ to entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)  
  
-   .NET koleksiyonları, dosyaları, dizeleri vb.: [nesnelere LINQ](linq-to-objects.md)

Bir daha derin LINQ genel olarak anlaşılması için bkz: [C# üzerinde LINQ](../../../linq/linq-in-csharp.md).

C# üzerinde LINQ ile çalışmaya başlamak için öğretici bkz [LINQ ile çalışma](../../../tutorials/working-with-linq.md).



