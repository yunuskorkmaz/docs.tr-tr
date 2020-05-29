---
title: Entity SQL’e Genel Bakış
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: b4fe852847d8b1b4bc0b80e3ba8e1f5b4aae9ff7
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202256"
---
# <a name="entity-sql-overview"></a>Entity SQL’e Genel Bakış
[!INCLUDE[esql](../../../../../../includes/esql-md.md)], Entity Framework kavramsal modelleri sorgulamanızı sağlayan bir SQL benzeri dildir. Kavramsal modeller verileri varlıklar ve ilişkiler olarak temsil eder ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu varlıkları ve ılışkılerı SQL kullanan kullanıcılara tanıdık bir biçimde sorgulamanızı sağlar.  

 Entity Framework, genel olarak depolamaya özgü sorgulara çevirmek için depolama 'ya özgü veri sağlayıcılarıyla birlikte kullanılabilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . EntityClient sağlayıcısı bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] varlık modeline karşı bir komut yürütmek ve skaler sonuçlar, sonuç kümeleri ve nesne grafikleri dahil zengin veri türlerini döndürmek için bir yol sağlar. <xref:System.Data.EntityClient.EntityCommand>Nesneleri oluştururken, özelliğine bir sorgu dizesi atayarak bir saklı yordam adı veya bir sorgu metni belirtebilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> . , <xref:System.Data.EntityClient.EntityDataReader> BIR EDM için yürütme sonuçlarını sunar <xref:System.Data.EntityClient.EntityCommand> . Öğesini döndüren komutunu yürütmek için <xref:System.Data.EntityClient.EntityDataReader> çağrısı yapın <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A> .  
  
 EntityClient sağlayıcısına ek olarak Entity Framework, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguları kavramsal bir modele karşı yürütmek ve verileri varlık türlerinin örnekleri olan kesin türü BELIRTILMIŞ clr nesneleri olarak döndürmek için kullanmanıza olanak sağlar. Daha fazla bilgi için bkz. [nesneleriyle çalışma](../working-with-objects.md).  
  
 Bu bölüm hakkında kavramsal bilgiler sağlar [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity SQL ile Transact-SQL Arasındaki Farklar](how-entity-sql-differs-from-transact-sql.md)  
  
 [Entity SQL Hızlı Başvurusu](entity-sql-quick-reference.md)  
  
 [Tür sistemi](type-system-entity-sql.md)  
  
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
  
 [İşleç önceliği](operator-precedence-entity-sql.md)  
  
 [Sayfalama](paging-entity-sql.md)  
  
 [Karşılaştırma Semantiği](comparison-semantics-entity-sql.md)  
  
 [İç İçe Geçmiş Entity SQL Sorguları Oluşturma](composing-nested-entity-sql-queries.md)  
  
 [Null Değer Atanabilir Yapılandırılmış Türler](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL Dili](entity-sql-language.md)
- [CSDL, SSDL ve MSL Belirtimleri](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
