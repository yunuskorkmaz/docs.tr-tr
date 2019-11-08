---
title: Entity SQL’e Genel Bakış
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: e0f154ab2d9db1a1fdbaba8c72bc7e43ad71ee0b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738493"
---
# <a name="entity-sql-overview"></a>Entity SQL’e Genel Bakış
[!INCLUDE[esql](../../../../../../includes/esql-md.md)], Entity Framework kavramsal modelleri sorgulamanızı sağlayan bir SQL benzeri dildir. Kavramsal modeller verileri varlıklar ve ilişkiler olarak temsil eder ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu varlıkları ve ilişkileri SQL kullanan kullanıcılara tanıdık bir biçimde sorgulamanızı sağlar.  
      
 Entity Framework, genel [!INCLUDE[esql](../../../../../../includes/esql-md.md)] depolamaya özgü sorgulara çevirmek için depolamaya özgü veri sağlayıcılarıyla birlikte kullanılabilir. EntityClient sağlayıcısı bir varlık modelinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] komutu yürütmek ve skaler sonuçlar, sonuç kümeleri ve nesne grafikleri dahil zengin veri türlerini döndürmek için bir yol sağlar. <xref:System.Data.EntityClient.EntityCommand> nesneleri oluşturduğunuzda, <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> özelliğine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir sorgu dizesi atayarak bir saklı yordam adı veya bir sorgu metni belirtebilirsiniz. <xref:System.Data.EntityClient.EntityDataReader>, bir EDM 'ye karşı <xref:System.Data.EntityClient.EntityCommand> yürütme sonuçlarını gösterir. <xref:System.Data.EntityClient.EntityDataReader>döndüren komutu yürütmek için, <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>çağırın.  
  
 Entity Framework EntityClient sağlayıcısına ek olarak, bir kavramsal modelde sorgu yürütmek ve verileri varlık türlerinin örnekleri olan kesin türü belirtilmiş CLR nesneleri olarak döndürmek için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kullanmanıza olanak sağlar. Daha fazla bilgi için bkz. [nesneleriyle çalışma](../working-with-objects.md).  
  
 Bu bölüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)]hakkında kavramsal bilgiler sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity SQL ile Transact-SQL Arasındaki Farklar](how-entity-sql-differs-from-transact-sql.md)  
  
 [Entity SQL Hızlı Başvurusu](entity-sql-quick-reference.md)  
  
 [Tür Sistemi](type-system-entity-sql.md)  
  
 [Tür Tanımları](type-definitions-entity-sql.md)  
  
 [Oluşturma Türleri](constructing-types-entity-sql.md)  
  
 [Sorgu Planını Önbelleğe Alma](query-plan-caching-entity-sql.md)  
  
 [Ad alanları](namespaces-entity-sql.md)  
  
 [Tanımlayıcılar](identifiers-entity-sql.md)  
  
 [Parametreler](parameters-entity-sql.md)  
  
 [Değişkenler](variables-entity-sql.md)  
  
 [Desteklenmeyen İfadeler](unsupported-expressions-entity-sql.md)  
  
 [Değişmez Değerler](literals-entity-sql.md)  
  
 [Null Değişmez Değerler ve Tür Çıkarımı](null-literals-and-type-inference-entity-sql.md)  
  
 [Giriş Karakter Kümesi](input-character-set-entity-sql.md)  
  
 [Sorgu İfadeleri](query-expressions-entity-sql.md)  
  
 [İşlevler](functions-entity-sql.md)  
  
 [İşleç Önceliği](operator-precedence-entity-sql.md)  
  
 [Disk Belleği](paging-entity-sql.md)  
  
 [Karşılaştırma Semantiği](comparison-semantics-entity-sql.md)  
  
 [İç İçe Geçmiş Entity SQL Sorguları Oluşturma](composing-nested-entity-sql-queries.md)  
  
 [Null Değer Atanabilir Yapılandırılmış Türler](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL Dili](entity-sql-language.md)
- [CSDL, SSDL ve MSL Belirtimleri](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
