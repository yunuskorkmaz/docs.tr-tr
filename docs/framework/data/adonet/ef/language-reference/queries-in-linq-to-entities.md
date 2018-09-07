---
title: LINQ to Entities sorguları
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: b6dc38951107b0d3833e1060c23962a43936bf4d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44048263"
---
# <a name="queries-in-linq-to-entities"></a>LINQ to Entities sorguları
Bir sorgu, verileri bir veri kaynağından alır bir ifadedir. Sorgular genellikle ilişkisel veritabanları için SQL ve XML için XQuery gibi bir özel sorgu dilinde ifade edilir. Bu nedenle, geliştiriciler, her veri kaynağı veya veri biçimi, bunlar sorgu türü için yeni bir sorgu dili öğrenmek zorunda kalmışlardır. Dil ile tümleşik sorgu (LINQ), çeşitli veri kaynakları ve biçimler arasında verilerle çalışmak için daha basit ve tutarlı bir modeli sunar. Bir LINQ Sorgu her zaman nesneleri programlama ile çalışırsınız.  
  
 Bir LINQ Sorgu işlemi üç eylemden oluşur: sorguyu veri kaynağından veya kaynaklarından elde etmek ve sorgu oluşturun.  
  
 Veri kaynakları uygulayan <xref:System.Collections.Generic.IEnumerable%601> genel arabirim veya <xref:System.Linq.IQueryable%601> genel arabirim LINQ sorgulanabilir. Genel örneklerini <xref:System.Data.Objects.ObjectQuery%601> genel uygulayan sınıf <xref:System.Linq.IQueryable%601> arabirimi, veri kaynağı görevi gören [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular. <xref:System.Data.Objects.ObjectQuery%601> Genel bir sınıf, sıfır veya daha fazla yazılan nesnelerin bir koleksiyonunu döndüren bir sorgu temsil eder. Ayrıca C# anahtar sözcüğünü kullanarak bir varlık türü derleyicinin sağlayabilirsiniz `var` (Visual Basic'te Dim).  
  
 Sorgu, veri kaynağından almak istediğiniz bilgi tam olarak belirtin. Bir sorgu, ayrıca nasıl bu bilgileri sıralanmış, gruplandırılmış ve döndürülmeden önce şeklinde belirtebilirsiniz. LINQ içinde bir sorgu bir değişkende depolanır. Sorgu değerler döndürürse, sorgu değişkeni sorgulanabilir tür olmalıdır. Bu sorgu değişkeni hiç eylem almaması ve veri döndürmemesidir; yalnızca, sorgu bilgileri depolar. Bir sorguyu oluşturduktan sonra herhangi bir veri almak için bu sorguyu yürütmeniz gerekir.  
  
## <a name="query-syntax"></a>Sorgu söz dizimi  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular iki farklı sözdizimini oluşan: sorgu ifadesi söz dizimi ve metot tabanlı sorgu söz dizimi. Sorgu ifadesi söz dizimi, C# 3.0 ve Visual Basic 9.0 yenidir ve yan tümceleri Transact-SQL veya XQuery benzer bir bildirim temelli söz yazılan bir dizi oluşur. Ancak, [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] ortak dil çalışma zamanı (CLR), sorgu ifade sözdizimi kendisini okuyamıyor. Bu nedenle, derleme zamanında sorgu ifadeleri CLR anlayan bir şey için çevrilmiş: yöntemi çağırır. Bu yöntemleri olarak bilinen *standart sorgu işleçleri*. Bir geliştirici olarak, doğrudan sorgu söz dizimi yerine yöntem sözdizimi kullanarak çağırma seçeneğiniz vardır. Daha fazla bilgi için [sorgu sözdizimi ve yöntem sözdizimi LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Sorgu ifadesi söz dizimi  
 Sorgu ifadeleri bir bildirim temelli bir sorgu söz dizimi var. Sorgular, Transact-SQL'e benzer biçimlendirilmiş üst düzey bir dilde yazmak bir geliştirici bu söz dizimi sağlar. Sorgu ifadesi söz dizimi kullanarak daha karmaşık filtreleme, sıralama ve gruplandırma işlemleri olabildiğince az kodla veri kaynaklarında gerçekleştirebilirsiniz. Daha fazla bilgi için [temel sorgu işlemleri (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Sorgu ifadesi söz dizimi kullanmayı gösteren örnekler için aşağıdaki konulara bakın:  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Projeksiyon](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Filtreleme](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Sıralama](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Toplu İşleçler](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Bölümleme](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Birleşim İşleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Öğe İşleçleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: Gruplandırma](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
-   [Sorgu İfadesi Söz Dizimi Örnekleri: İlişkilerde Gezinme](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Metot tabanlı sorgu söz dizimi  
 Oluşturmak için başka bir yolu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgulardır yöntem temelli sorgular kullanarak. Metot tabanlı sorgu söz dizimi, lambda ifadeleri parametre olarak geçirmeyi LINQ işleci yöntemlerinin doğrudan yöntem çağrılarının bir dizidir. Daha fazla bilgi için [Lambda ifadeleri](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Yöntem tabanlı sözdizimi kullanmayı gösteren örnekler için aşağıdaki konulara bakın:  
  
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
 [Visual Basic'te lınq'e Başlarken](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Entity Framework birleştirme seçeneklerini ve derlenmiş sorgular](https://go.microsoft.com/fwlink/?LinkId=199591)
