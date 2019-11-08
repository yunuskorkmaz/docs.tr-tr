---
title: LINQ to Entities Sorguları
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 52f48fcacd6fbd92e4fd0531c5e1fa3577496941
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738472"
---
# <a name="queries-in-linq-to-entities"></a>LINQ to Entities Sorguları
Sorgu, veri kaynağından veri alan bir ifadedir. Sorgular, genellikle ilişkisel veritabanları için SQL gibi özel bir sorgu dilinde ifade edilir ve XML için XQuery. Bu nedenle, geliştiricilerin sorgutıkları her bir veri kaynağı türü veya veri biçimi için yeni bir sorgu dili öğrenmeleri gerekiyordu. Dil ile tümleşik sorgu (LINQ), çeşitli veri kaynakları ve biçimlerdeki verilerle çalışmaya yönelik daha basit ve tutarlı bir model sunar. Bir LINQ sorgusunda, her zaman programlama nesneleriyle çalışırsınız.  
  
 Bir LINQ sorgu işlemi üç eylemden oluşur: veri kaynağını veya kaynaklarını alın, sorguyu oluşturun ve sorguyu yürütün.  
  
 <xref:System.Collections.Generic.IEnumerable%601> genel arabirimini veya <xref:System.Linq.IQueryable%601> genel arabirimini uygulayan veri kaynakları LINQ aracılığıyla sorgulanabilir. Genel <xref:System.Linq.IQueryable%601> arabirimini uygulayan genel <xref:System.Data.Objects.ObjectQuery%601> sınıfının örnekleri LINQ to Entities sorguları için veri kaynağı olarak görev yapar. <xref:System.Data.Objects.ObjectQuery%601> genel sınıfı, sıfır veya daha fazla yazılmış nesne koleksiyonunu döndüren bir sorguyu temsil eder. Ayrıca derleyicinin `var` C# anahtar sözcüğünü kullanarak bir varlığın türünü çıkarmasına izin verebilirsiniz (Visual Basic karartma).  
  
 Sorguda, tam olarak veri kaynağından almak istediğiniz bilgileri belirtirsiniz. Bir sorgu, döndürülmeden önce bu bilgilerin nasıl sıralanacağını, gruplanacağını ve şekillendirilmiş olduğunu da belirtebilir. LINQ içinde, bir sorgu bir değişkende depolanır. Sorgu bir değer dizisi döndürürse, sorgu değişkeni bir sorgulanabilir tür olmalıdır. Bu sorgu değişkeni hiçbir eylemde bulunmaz ve veri döndürmez; yalnızca sorgu bilgilerini depolar. Bir sorgu oluşturduktan sonra, verileri almak için bu sorguyu yürütmeniz gerekir.  
  
## <a name="query-syntax"></a>Sorgu söz dizimi  
 LINQ to Entities sorguları iki farklı Sözdizimde olabilir: sorgu ifadesi sözdizimi ve Yöntem tabanlı sorgu söz dizimi. Sorgu ifadesi söz dizimi 3,0 ve C# Visual Basic 9,0 ' de yenidir ve Transact-SQL veya XQuery ile benzer bir bildirime dayalı sözdiziminde yazılmış bir tümce kümesinden oluşur. Ancak, .NET Framework ortak dil çalışma zamanı (CLR) sorgu ifadesi sözdiziminin kendisini okuyamıyor. Bu nedenle, derleme zamanında sorgu ifadeleri CLR 'nin anlayabileceği bir şeye çevrilir: Yöntem çağrıları. Bu yöntemler *Standart sorgu işleçleri*olarak bilinir. Bir geliştirici olarak, sorgu sözdizimini kullanmak yerine, bunları doğrudan yöntem sözdizimini kullanarak çağırma seçeneğiniz vardır. Daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](../../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Sorgu Ifadesi söz dizimi  
 Sorgu ifadeleri bildirime dayalı bir sorgu sözdizimidir. Bu sözdizimi, bir geliştiricinin Transact-SQL ile benzer şekilde biçimlendirilen üst düzey bir dilde sorgu yazmasını sağlar. Sorgu ifadesi söz dizimini kullanarak, çok az kodlu veri kaynakları üzerinde bile karmaşık filtreleme, sıralama ve gruplama işlemleri gerçekleştirebilirsiniz. Daha fazla bilgi için [temel sorgu işlemleri (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Sorgu ifadesi sözdiziminin nasıl kullanılacağını gösteren örnekler için aşağıdaki konulara bakın:  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Projeksiyon](query-expression-syntax-examples-projection.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Filtreleme](query-expression-syntax-examples-filtering.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Sıralama](query-expression-syntax-examples-ordering.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Toplu İşleçler](query-expression-syntax-examples-aggregate-operators.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Bölümleme](query-expression-syntax-examples-partitioning.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Birleşim İşleçleri](query-expression-syntax-examples-join-operators.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Öğe İşleçleri](query-expression-syntax-examples-element-operators.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Gruplandırma](query-expression-syntax-examples-grouping.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: İlişkilerde Gezinme](query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Yöntem tabanlı sorgu söz dizimi  
 LINQ to Entities sorguları oluşturmanın başka bir yolu da Yöntem tabanlı sorgular kullanmaktır. Yöntem tabanlı sorgu söz dizimi, LINQ operatörü yöntemlerine doğrudan yöntem çağrılarının bir dizidir ve Lambda ifadelerini parametreler olarak geçirerek. Daha fazla bilgi için bkz. [lambda ifadeleri](../../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Yöntem tabanlı sözdiziminin nasıl kullanılacağını gösteren örnekler için aşağıdaki konulara bakın:  
  
- [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Projeksiyon](method-based-query-syntax-examples-projection.md)  
  
- [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Filtreleme](method-based-query-syntax-examples-filtering.md)  
  
- [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Sıralama](method-based-query-syntax-examples-ordering.md)  
  
- [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Toplu İşleçler](method-based-query-syntax-examples-aggregate-operators.md)  
  
- [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Bölümleme](method-based-query-syntax-examples-partitioning.md)  
  
- [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Dönüştürme](method-based-query-syntax-examples-conversion.md)  
  
- [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleşim İşleçleri](method-based-query-syntax-examples-join-operators.md)  
  
- [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Öğe İşleçleri](method-based-query-syntax-examples-element-operators.md)  
  
- [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Gruplandırma](method-based-query-syntax-examples-grouping.md)  
  
- [Metot Tabanlı Sorgu Söz Dizimi Örnekleri: İlişkilerde Gezinme](method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities](linq-to-entities.md)
- [C#'de LINQ Kullanmaya Başlama](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Visual Basic LINQ ile çalışmaya başlama](../../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Entity Framework birleştirme seçenekleri ve derlenmiş sorgular](https://go.microsoft.com/fwlink/?LinkId=199591)
