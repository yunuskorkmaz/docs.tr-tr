---
title: "LINQ to Entities sorguları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6fe20fd26b78bde19ed73e2415b1b5c283a0d1f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="queries-in-linq-to-entities"></a>LINQ to Entities sorguları
Bir sorgu veri kaynağından verileri alan bir ifadedir. Sorguları genellikle ilişkisel veritabanları için SQL ve XML için XQuery gibi bir özel sorgu dili ifade edilir. Bu nedenle, geliştiricilerin her veri kaynağı veya bunlar sorgu veri biçimi türü için yeni bir sorgu dili öğrenin gerekirdi. Dil ile tümleşik sorgu (LINQ) çeşitli veri kaynakları ve biçimleri arasında verilerle çalışmak için daha basit ve tutarlı bir modeli sunar. LINQ Sorgu içinde her zaman nesneleri programlama ile çalışırsınız.  
  
 LINQ Sorgu işlemi üç eylemlerini oluşur: veri kaynağı veya kaynakları edinme, sorguyu oluşturmak ve sorgu yürütün.  
  
 Veri kaynakları uygulayan <xref:System.Collections.Generic.IEnumerable%601> genel arabirim veya <xref:System.Linq.IQueryable%601> genel arabirimi LINQ sorgulanan. Genel örneklerini <xref:System.Data.Objects.ObjectQuery%601> genel uygulayan sınıf <xref:System.Linq.IQueryable%601> arabirim, veri kaynağı olarak hizmet [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular. <xref:System.Data.Objects.ObjectQuery%601> Genel sınıfı, sıfır veya daha fazla yazılan nesnelerin koleksiyonu döndüren bir sorgu temsil eder. Ayrıca C# anahtar sözcüğünü kullanarak bir varlık türünü Infer derleyici sağlayabilirsiniz `var` (Visual Basic'te Dim).  
  
 Sorgu, tam olarak veri kaynağından almak istediğiniz bilgileri belirtin. Bir sorgu de nasıl bu bilgileri sıralanmış, gruplandırılmış ve, döndürülmeden önce şeklinde belirtebilirsiniz. LINQ, sorgu bir değişkende depolanır. Sorgu değerleri dizisi döndürürse, sorgu değişkeni sorgulanabilir bir türü olmalıdır. Bu sorgu değişkeni hiçbir eylemde bulunmaz ve hiçbir veri döndürür; yalnızca, sorgu bilgileri depolar. Bir sorgu oluşturduktan sonra herhangi bir veri almak için bu sorguyu yürütmeniz gerekir.  
  
## <a name="query-syntax"></a>Sorgu sözdizimi  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]sorgu içinde iki farklı sözdizimi birleştirilebilen: Sorgu ifade sözdizimi ve yöntem temelli sorgu sözdizimi. C# 3.0 ve Visual Basic 9.0 sorgu ifade sözdizimi yenidir ve Transact-SQL veya XQuery benzer bir tanımlayıcı sözdizimi yazılmış yan tümceleri kümesinden oluşur. Ancak, [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] ortak dil çalışma zamanı (CLR), sorgu ifade sözdizimi kendisini okuyamıyor. Bu nedenle, derleme zamanında sorgu ifadeleri bir şeye CLR anlamak çevrilebilir: yöntem çağrıları. Bu yöntemleri olarak bilinen *standart sorgu işleçleri*. Bir geliştirici olarak doğrudan sorgu sözdizimini kullanarak yerine yöntemi sözdizimini kullanarak çağırma seçeneğiniz vardır. Daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Sorgu ifade sözdizimi  
 Sorgu ifadeleri bildirim temelli sorgu söz dizimi ' dir. Bu sözdiziminin sorguları Transact-SQL benzeyen üst düzey bir dilde yazmak bir geliştirici sağlar. Sorgu ifade sözdizimini kullanarak, daha karmaşık filtreleme, sıralama ve veri kaynaklarında çok az kod ile gruplandırma işlemleri gerçekleştirebilir. Daha fazla bilgi için [temel sorgu işlemleri (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Sorgu ifade sözdizimi kullanımını göstermektedir örnekler için aşağıdaki konulara bakın:  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Projeksiyon](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Filtreleme](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Sıralama](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Toplu İşleçler](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Bölümleme](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Birleşim İşleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Öğe İşleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Gruplandırma](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: İlişkilerde Gezinme](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Yöntem temelli sorgu söz dizimi  
 Oluşturmak için başka bir yolu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorguları kullanmaktır yöntem temelli sorgular. Yöntem temelli sorgu sözdizimini doğrudan yöntem çağrılarının lambda ifadeleri parametre olarak geçirme LINQ işleci yöntemlerine bir dizidir. Daha fazla bilgi için bkz: [Lambda ifadeleri](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Yöntem temelli sözdizimi kullanımını göstermektedir örnekler için aşağıdaki konulara bakın:  
  
-   [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Projeksiyon](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-projection.md)  
  
-   [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Filtreleme](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-filtering.md)  
  
-   [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Sıralama](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-ordering.md)  
  
-   [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Toplu İşleçler](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Bölümleme](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-partitioning.md)  
  
-   [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Dönüştürme](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-conversion.md)  
  
-   [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleşim İşleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-join-operators.md)  
  
-   [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Öğe İşleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-element-operators.md)  
  
-   [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Gruplandırma](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-grouping.md)  
  
-   [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: İlişkilerde Gezinme](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [C#'de LINQ Kullanmaya Başlama](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Visual Basic'te Lınq'e Başlarken](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Entity Framework birleştirme seçeneklerini ve derlenmiş sorguları](http://go.microsoft.com/fwlink/?LinkId=199591)
