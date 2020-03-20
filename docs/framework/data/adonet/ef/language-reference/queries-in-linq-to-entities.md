---
title: LINQ to Entities Sorguları
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 3144796dfb1a970152d8ae56424aa37592d5da09
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848788"
---
# <a name="queries-in-linq-to-entities"></a>LINQ to Entities Sorguları
Sorgu, veri kaynağından veri alabilecek bir ifadedir. Sorgular genellikle ilişkisel veritabanları için SQL ve XML için XQuery gibi özel bir sorgu dilinde ifade edilir. Bu nedenle, geliştiriciler sorguladıkları her veri kaynağı veya veri biçimi türü için yeni bir sorgu dili öğrenmek zorunda kaldıklarını. Dil-Tümleşik Sorgu (LINQ), çeşitli veri kaynakları ve biçimleri arasında verilerle çalışmak için daha basit ve tutarlı bir model sunar. LINQ sorgusunda, her zaman programlama nesneleri ile çalışırsınız.  
  
 BIR LINQ sorgu işlemi üç eylemden oluşur: veri kaynağını veya kaynaklarını elde etmek, sorguyu oluşturmak ve sorguyu yürütmek.  
  
 <xref:System.Collections.Generic.IEnumerable%601> Genel arabirimi veya <xref:System.Linq.IQueryable%601> genel arabirimi uygulayan veri kaynakları LINQ aracılığıyla sorgulanabilir. Genel <xref:System.Linq.IQueryable%601> arabirimi <xref:System.Data.Objects.ObjectQuery%601> uygulayan genel sınıfın örnekleri, LINQ'nin Varlıklar sorgularına veri kaynağı olarak hizmet eder. Genel <xref:System.Data.Objects.ObjectQuery%601> sınıf, sıfır veya daha fazla yazılan nesne koleksiyonunu döndüren bir sorguyu temsil eder. Ayrıca, C# anahtar sözcük `var` (Visual Basic'te Dim) kullanarak derleyicinin varlığın türünü çıkarmasına da izin verebilirsiniz.  
  
 Sorguda, veri kaynağından almak istediğiniz bilgileri tam olarak belirtirsiniz. Sorgu, bu bilgilerin döndürülmeden önce nasıl sıralanmalı, gruplandırılmalı ve şekillendirilmesi gerektiğini de belirtebilir. LINQ'da, bir sorgu bir değişkende depolanır. Sorgu bir değer sırasını döndürürse, sorgu değişkeninin kendisi sorgulanabilir bir tür olmalıdır. Bu sorgu değişkeni hiçbir işlem almaz ve hiçbir veri döndürür; yalnızca sorgu bilgilerini depolar. Bir sorgu oluşturduktan sonra herhangi bir veri almak için bu sorguyürütmek gerekir.  
  
## <a name="query-syntax"></a>Sözdizimini Sorgula  
 LINQ to Varlıklar sorguları iki farklı sözdizimi nde oluşturulabilir: sorgu ifade sözdizimi ve yöntem tabanlı sorgu sözdizimi. Sorgu ifade sözdizimi C# 3.0 ve Visual Basic 9.0'da yenidir ve Transact-SQL veya XQuery'ye benzer bir bildirim sözdiziminde yazılmış bir dizi yan tümceden oluşur. Ancak, .NET Framework ortak dil çalışma zamanı (CLR) sorgu ifade sözdizimini kendisi okuyamaz. Bu nedenle, derleme zamanında, sorgu ifadeleri CLR'nin anladığı bir şeye çevrilir: yöntem çağrıları. Bu yöntemler standart *sorgu işleçleri*olarak bilinir. Geliştirici olarak, sorgu sözdizimini kullanmak yerine yöntem sözdizimini kullanarak bunları doğrudan arama seçeneğiniz olur. Daha fazla bilgi için [LINQ'da Sorgu Sözdizimi ve Yöntem Sözdizimi'ne](../../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)bakın.  
  
### <a name="query-expression-syntax"></a>Sorgu İfade Sözdizimi  
 Sorgu ifadeleri bildirimsel sorgu sözdizimidir. Bu sözdizimi, bir geliştiricinin Transact-SQL'e benzer biçimlendirilmiş üst düzey bir dilde sorgu yazmasına olanak tanır. Sorgu ifade sözdizimini kullanarak, en az kodla veri kaynaklarında karmaşık filtreleme, sıralama ve gruplandırma işlemleri bile gerçekleştirebilirsiniz. Daha fazla bilgi [için, Temel Sorgu İşlemleri (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Sorgu ifade sözdiziminin nasıl kullanılacağını gösteren örnekler için aşağıdaki konulara bakın:  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Projeksiyon](query-expression-syntax-examples-projection.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Filtreleme](query-expression-syntax-examples-filtering.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Sıralama](query-expression-syntax-examples-ordering.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Toplu İşleçler](query-expression-syntax-examples-aggregate-operators.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Bölümleme](query-expression-syntax-examples-partitioning.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Birleşim İşleçleri](query-expression-syntax-examples-join-operators.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Öğe İşleçleri](query-expression-syntax-examples-element-operators.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: Gruplandırma](query-expression-syntax-examples-grouping.md)  
  
- [Sorgu İfadesi Söz Dizimi Örnekleri: İlişkilerde Gezinme](query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Yöntem Tabanlı Sorgu Sözdizimi  
 Varlıklar sorgularına LINQ oluşturmanın başka bir yolu da yöntem tabanlı sorguları kullanmaktır. Yöntem tabanlı sorgu sözdizimi, lambda ifadelerini parametreler olarak geçen LINQ işleci yöntemlerine doğrudan yöntem çağrıları dizisidir. Daha fazla bilgi için [Lambda İfadeleri'ne](../../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)bakın. Yöntem tabanlı sözdiziminin nasıl kullanılacağını gösteren örnekler için aşağıdaki konulara bakın:  
  
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

- [LINQ - Varlıklar](linq-to-entities.md)
- [C#'de LINQ'e Başlarken](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Visual Basic'te LINQ'e Başlarken](../../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [EF Birleştirme Seçenekleri ve Derlenmiş Sorgular](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)
