---
title: Entity SQL’e Genel Bakış
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 8f40a34f361669d2b8d89b63b3187cae6bf705d2
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854490"
---
# <a name="entity-sql-overview"></a>Entity SQL’e Genel Bakış
[!INCLUDE[esql](../../../../../../includes/esql-md.md)], Entity Framework kavramsal modelleri sorgulamanızı sağlayan bir SQL benzeri dildir. Kavramsal modeller verileri varlıklar ve ilişkiler olarak temsil eder ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu varlıkları ve ilişkileri SQL kullanan kullanıcılara tanıdık bir biçimde sorgulamanızı sağlar.  
      
 Entity Framework, genel [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olarak depolamaya özgü sorgulara çevirmek için depolama 'ya özgü veri sağlayıcılarıyla birlikte kullanılabilir. EntityClient sağlayıcısı bir varlık modeline karşı bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] komut yürütmek ve skaler sonuçlar, sonuç kümeleri ve nesne grafikleri dahil zengin veri türlerini döndürmek için bir yol sağlar. Nesneleri oluştururken, <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> özelliğine bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu dizesi atayarak bir saklı yordam adı veya bir sorgu metni belirtebilirsiniz. <xref:System.Data.EntityClient.EntityCommand> , <xref:System.Data.EntityClient.EntityDataReader> Bir<xref:System.Data.EntityClient.EntityCommand> EDM için yürütme sonuçlarını sunar. <xref:System.Data.EntityClient.EntityDataReader>Öğesini döndüren komutunu yürütmek için çağrısı <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>yapın.  
  
 EntityClient sağlayıcısına ek olarak Entity Framework, sorguları kavramsal bir modele karşı yürütmek ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] verileri varlık türlerinin örnekleri olan kesin türü belirtilmiş CLR nesneleri olarak döndürmek için kullanmanıza olanak sağlar. Daha fazla bilgi için bkz. [nesneleriyle çalışma](../working-with-objects.md).  
  
 Bu bölüm hakkında [!INCLUDE[esql](../../../../../../includes/esql-md.md)]kavramsal bilgiler sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity SQL ile Transact-SQL Arasındaki Farklar](how-entity-sql-differs-from-transact-sql.md)  
  
 [Entity SQL Hızlı Başvurusu](entity-sql-quick-reference.md)  
  
 [Tür Sistemi](type-system-entity-sql.md)  
  
 [Tür Tanımları](type-definitions-entity-sql.md)  
  
 [Oluşturma Türleri](constructing-types-entity-sql.md)  
  
 [Sorgu Planını Önbelleğe Alma](query-plan-caching-entity-sql.md)  
  
 [Ad Alanları](namespaces-entity-sql.md)  
  
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
- [CSDL, SSDL ve MSL Belirtimleri](csdl-ssdl-and-msl-specifications.md)
