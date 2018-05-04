---
title: Sorgu ifadeleri (varlık SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: d721f54486845847ec86253356e7a605f882722b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="query-expressions-entity-sql"></a>Sorgu ifadeleri (varlık SQL)
Bir sorgu ifadesi tek bir sözdizimi birçok farklı sorgu işleçleri birleştirir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifadeler, aşağıdakiler dahil çeşitli sağlar: [değişmez değerleri](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parametreleri](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [değişkenleri](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), işleçler, [işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)ayarlamak işleçler ve benzeri. Daha fazla bilgi için bkz: [varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).  
  
## <a name="clauses"></a>Tümceler  
 Bir sorgu ifadesi art arda işlemleri için nesneler koleksiyonunu uygulamak yan tümceleri bir dizi oluşur. Standart bir SQL select deyimi bulunan aynı yan tümceleri üzerinde temel alır: [seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [nerede](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [Sahip](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), ve [sıralama ölçütü](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  
  
## <a name="scope"></a>Kapsam  
 FROM yan tümcesinde tanımlanan adları soldan sağa görünümünü FROM kapsamı içine sunulur. BİRLEŞİM listesinde ifadeleri listede daha önce tanımlanan adlarını başvurabilir. FROM yan tümcesinde tanımlanan öğelerin ortak özellikleri FROM kapsama eklenmedi: diğer tam adının her zaman başvurulmalıdır. Normalde, select ifadesi tüm parçalarını FROM kapsamında olarak kabul edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
