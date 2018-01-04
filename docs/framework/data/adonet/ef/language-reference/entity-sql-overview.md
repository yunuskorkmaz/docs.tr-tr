---
title: "Varlık SQL genel bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f77e3a5d0073cb13d1904f802c4d6760fc52caa9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="entity-sql-overview"></a>Varlık SQL genel bakış
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]kavramsal modellerde sorgu olanak tanıyan bir SQL benzeri bir dildir [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Kavramsal modeller varlıkları ve ilişkileri, verilerini temsil eden ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu varlıkları ve ilişkileri SQL kullanmış olan olanlar için tanıdık bir biçimde sorgu olanak tanır.  
  
 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Çalışır genel çevirmek için depolama özgü veri sağlayıcılarıyla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] içine depolama özgü sorgular. EntityClient sağlayıcısı yürütmek için bir yol sağlayan bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] komutu karşı bir varlık modeli ve zengin skaler sonuçları, sonuç kümeleri ve nesne grafiklerinin dahil olmak üzere veri türlerini döndürür. Oluşturduğunuzda <xref:System.Data.EntityClient.EntityCommand> nesneleri belirtebilirsiniz bir saklı yordam adı veya bir sorgu metnini atayarak bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu dizesi için kendi <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> özelliği. <xref:System.Data.EntityClient.EntityDataReader> Yürütme sonuçlarını gösterir bir <xref:System.Data.EntityClient.EntityCommand> EDM karşı. Döndürür komutu çalıştırmak için <xref:System.Data.EntityClient.EntityDataReader>, çağrı <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.  
  
 EntityClient sağlayıcısı yanı sıra [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] kullanmanıza olanak tanır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kavramsal model sorgu yürütebilir ve varlık türleri örneklerini kesin türü belirtilmiş CLR nesneler veri döndürmek için. Daha fazla bilgi için bkz: [nesneleriyle çalışma](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Bu bölümde hakkında kavramsal bilgiler verilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity SQL ile Transact-SQL Arasındaki Farklar](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [Entity SQL Hızlı Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [Tür Sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [Tür Tanımları](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [Oluşturma Türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [Sorgu Planını Önbelleğe Alma](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [Ad Alanları](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [Tanımlayıcılar](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [Parametreler](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [Değişkenler](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [Desteklenmeyen İfadeler](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [Değişmez Değerler](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [Null Değişmez Değerler ve Tür Çıkarımı](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [Giriş Karakter Kümesi](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [İşleç Önceliği](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [Disk Belleği](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [Karşılaştırma Semantiği](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [İç İçe Geçmiş Entity SQL Sorguları Oluşturma](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [Null Değer Atanabilir Yapılandırılmış Türler](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL Dili](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [CSDL, SSDL ve MSL Belirtimleri](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
