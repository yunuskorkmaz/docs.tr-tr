---
title: Sorgu ifadeleri (varlık SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 5f89028b9c501dd840f1dc9445418e4757967db8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146919"
---
# <a name="query-expressions-entity-sql"></a>Sorgu ifadeleri (varlık SQL)
Sorgu ifadesi içinde tek bir söz dizimi farklı sorgu işleçlerinin çoğu birleştirir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifadeler, aşağıdakiler dahil çeşitli sağlar: [değişmez değerleri](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parametreleri](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [değişkenleri](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), işleçler, [işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)işleçleri ayarlama ve benzeri. Daha fazla bilgi için [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).  
  
## <a name="clauses"></a>Tümceler  
 Bir sorgu ifadesinde, bir dizi art arda işlemlerin nesnelerden oluşan bir koleksiyon için geçerli olan yan tümceleri oluşur. Bunlar, standart bir SQL select deyimi bulunan aynı yan tümceleri üzerinde temel alır: [SEÇİN](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [burada](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GRUPLANDIRMA ölçütü](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), ve [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  
  
## <a name="scope"></a>Kapsam  
 Adları FROM yan tümcesinde tanımlı FROM kapsama Görünüm soldan sağa sırasına göre sunulmuştur. Birleştirme listesinde ifadeleri listede daha önce tanımlanan adları başvurabilir. FROM yan tümcesinde belirtilen öğelerin ortak özellikleri FROM kapsama eklenmez. Diğer adla nitelenmiş ad her zaman başvurulmalıdır. Normalde, select deyimini tüm parçalarını FROM kapsamında değerlendirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
