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
ms.openlocfilehash: 220416aa4e282cb342ee6080d9040f9f4818fbf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
-   [Sorgu ifade sözdizimi örnekleri: projeksiyonu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
-   [Sorgu ifade sözdizimi örnekleri: filtreleme](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
-   [Sorgu ifade sözdizimi örnekleri: sıralama](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
-   [Sorgu ifade sözdizimi örnekleri: Toplama işleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [Sorgu ifade sözdizimi örnekleri: bölümlendirme](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
-   [Sorgu ifade sözdizimi örnekleri: Birleştirme işleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
-   [Sorgu ifade sözdizimi örnekleri: Öğesi işleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
-   [Sorgu ifade sözdizimi örnekleri: gruplandırma](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
-   [Sorgu ifade sözdizimi örnekleri: İlişkilerinde gezinme](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Yöntem temelli sorgu söz dizimi  
 Oluşturmak için başka bir yolu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorguları kullanmaktır yöntem temelli sorgular. Yöntem temelli sorgu sözdizimini doğrudan yöntem çağrılarının lambda ifadeleri parametre olarak geçirme LINQ işleci yöntemlerine bir dizidir. Daha fazla bilgi için bkz: [Lambda ifadeleri](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Yöntem temelli sözdizimi kullanımını göstermektedir örnekler için aşağıdaki konulara bakın:  
  
-   [Yöntem temelli sorgu sözdizimi örnekleri: projeksiyonu](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-projection.md)  
  
-   [Yöntem temelli sorgu sözdizimi örnekleri: filtreleme](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-filtering.md)  
  
-   [Yöntem temelli sorgu sözdizimi örnekleri: sıralama](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-ordering.md)  
  
-   [Yöntem temelli sorgu sözdizimi örnekler: Toplama işleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [Yöntem temelli sorgu sözdizimi örnekleri: bölümlendirme](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-partitioning.md)  
  
-   [Yöntem temelli sorgu sözdizimi örnekleri: dönüştürme](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-conversion.md)  
  
-   [Yöntem temelli sorgu sözdizimi örnekler: Birleştirme işleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-join-operators.md)  
  
-   [Yöntem temelli sorgu sözdizimi örnekler: Öğesi işleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-element-operators.md)  
  
-   [Yöntem temelli sorgu sözdizimi örnekleri: gruplandırma](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-grouping.md)  
  
-   [Yöntem temelli sorgu sözdizimi örnekler: İlişkilerinde gezinme](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-varlıklar](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [C# üzerinde LINQ ile çalışmaya başlama](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Visual Basic'te Lınq'e Başlarken](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Entity Framework birleştirme seçeneklerini ve derlenmiş sorguları](http://go.microsoft.com/fwlink/?LinkId=199591)
