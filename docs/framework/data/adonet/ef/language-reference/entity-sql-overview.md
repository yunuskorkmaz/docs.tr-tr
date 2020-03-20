---
title: Entity SQL’e Genel Bakış
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 880b81f2b6d4c4b893d28c919490f88dfb2a42e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150382"
---
# <a name="entity-sql-overview"></a>Entity SQL’e Genel Bakış
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Varlık Çerçevesi'ndeki kavramsal modelleri sorgulamanızı sağlayan SQL benzeri bir dildir. Kavramsal modeller verileri varlıklar ve ilişkiler [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olarak temsil ediyor ve bu varlıkları ve ilişkileri SQL kullananlara tanıdık bir biçimde sorgulamanızı sağlar.  

 Varlık Çerçevesi, genel [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olarak depolamaya özgü sorgulara çevirmek için depolamaya özgü veri sağlayıcılarıyla birlikte çalışır. EntityClient sağlayıcısı, bir varlık [!INCLUDE[esql](../../../../../../includes/esql-md.md)] modeline karşı bir komut yürütmek ve skaler sonuçlar, sonuç kümeleri ve nesne grafikleri de dahil olmak üzere zengin veri türlerini döndürmek için bir yol sağlar. Nesneleri oluşturduğunuzda, <xref:System.Data.EntityClient.EntityCommand> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> bir sorgu dizesi atayarak depolanmış yordam adı veya sorgu metnini belirtebilirsiniz. Bir <xref:System.Data.EntityClient.EntityDataReader> EDM'ye karşı <xref:System.Data.EntityClient.EntityCommand> bir uygulamanın sonuçlarını ortaya çıkarır. Döndüren komutu <xref:System.Data.EntityClient.EntityDataReader>yürütmek <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>için , çağrı .  
  
 EntityClient sağlayıcısına ek olarak, Entity Framework, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguları kavramsal bir modele karşı yürütmek ve verileri varlık türlerinin örnekleri olan güçlü bir şekilde yazılan CLR nesneleri olarak döndürmek için kullanmanıza olanak tanır. Daha fazla bilgi için [bkz.](../working-with-objects.md)  
  
 Bu bölümde. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity SQL ile Transact-SQL Arasındaki Farklar](how-entity-sql-differs-from-transact-sql.md)  
  
 [Entity SQL Hızlı Başvurusu](entity-sql-quick-reference.md)  
  
 [Tür Sistemi](type-system-entity-sql.md)  
  
 [Tür Tanımları](type-definitions-entity-sql.md)  
  
 [Oluşturma Türleri](constructing-types-entity-sql.md)  
  
 [Sorgu Planını Önbelleğe Alma](query-plan-caching-entity-sql.md)  
  
 [Ad Alanları](namespaces-entity-sql.md)  
  
 [Tanımlayıcılar](identifiers-entity-sql.md)  
  
 [Parametre](parameters-entity-sql.md)  
  
 [Değişkenler](variables-entity-sql.md)  
  
 [Desteklenmeyen İfadeler](unsupported-expressions-entity-sql.md)  
  
 [Sabit değerler](literals-entity-sql.md)  
  
 [Null Değişmez Değerler ve Tür Çıkarımı](null-literals-and-type-inference-entity-sql.md)  
  
 [Giriş Karakter Kümesi](input-character-set-entity-sql.md)  
  
 [Sorgu İfadeleri](query-expressions-entity-sql.md)  
  
 [Işlev](functions-entity-sql.md)  
  
 [İşleç Önceliği](operator-precedence-entity-sql.md)  
  
 [Sayfalama](paging-entity-sql.md)  
  
 [Karşılaştırma Semantiği](comparison-semantics-entity-sql.md)  
  
 [İç İçe Geçmiş Entity SQL Sorguları Oluşturma](composing-nested-entity-sql-queries.md)  
  
 [Null Değer Atanabilir Yapılandırılmış Türler](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL Dili](entity-sql-language.md)
- [CSDL, SSDL ve MSL Belirtimleri](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
