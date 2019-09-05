---
title: Entity SQL’e Genel Bakış
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 4d7db9c6a7aaeef900132663a5b0aa7420afe668
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251065"
---
# <a name="entity-sql-overview"></a>Entity SQL’e Genel Bakış
[!INCLUDE[esql](../../../../../../includes/esql-md.md)], [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]içinde kavramsal modeller sorgulamanızı sağlayan bir SQL benzeri dildir. Kavramsal modeller verileri varlıklar ve ilişkiler olarak temsil eder ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu varlıkları ve ilişkileri SQL kullanan kullanıcılara tanıdık bir biçimde sorgulamanızı sağlar.  
  
 , [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Genel[!INCLUDE[esql](../../../../../../includes/esql-md.md)] olarak depolamaya özgü sorgulara çevirmek için depolamaya özgü veri sağlayıcılarıyla birlikte çalışarak. EntityClient sağlayıcısı bir varlık modeline karşı bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] komut yürütmek ve skaler sonuçlar, sonuç kümeleri ve nesne grafikleri dahil zengin veri türlerini döndürmek için bir yol sağlar. Nesneleri oluştururken, <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> özelliğine bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu dizesi atayarak bir saklı yordam adı veya bir sorgu metni belirtebilirsiniz. <xref:System.Data.EntityClient.EntityCommand> , <xref:System.Data.EntityClient.EntityDataReader> Bir<xref:System.Data.EntityClient.EntityCommand> EDM için yürütme sonuçlarını sunar. <xref:System.Data.EntityClient.EntityDataReader>Öğesini döndüren komutunu yürütmek için çağrısı <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>yapın.  
  
 EntityClient sağlayıcısına ek olarak, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] bir kavramsal modelde sorgu yürütmek ve verileri varlık türlerinin örnekleri olan kesin türü belirtilmiş CLR nesneleri olarak döndürmek [!INCLUDE[esql](../../../../../../includes/esql-md.md)] için kullanmanızı sağlar. Daha fazla bilgi için bkz. [nesneleriyle çalışma](../working-with-objects.md).  
  
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
