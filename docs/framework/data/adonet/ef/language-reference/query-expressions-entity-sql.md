---
title: Sorgu Ifadeleri (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 4428286890f41573a02daf31a4593d0c8f9ad34b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249269"
---
# <a name="query-expressions-entity-sql"></a>Sorgu Ifadeleri (Entity SQL)
Sorgu ifadesi birçok farklı sorgu işlecini tek bir sözdizimi halinde birleştirir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Aşağıdakiler dahil olmak üzere çeşitli tür ifadeler sağlar: [değişmez değerler](literals-entity-sql.md), [Parametreler](parameters-entity-sql.md), [değişkenler](variables-entity-sql.md), işleçler, [işlevler](functions-entity-sql.md), set işleçleri, vb. Daha fazla bilgi için bkz. [Entity SQL başvurusu](entity-sql-reference.md).  
  
## <a name="clauses"></a>Tümceler  
 Sorgu ifadesi bir nesne koleksiyonuna art arda işlemler uygulayan bir dizi yan tümcelerden oluşur. Standart a SQL SELECT ifadesinde bulunan aynı yan tümceleri temel alır: [Select](select-entity-sql.md), [from](from-entity-sql.md), [WHERE](where-entity-sql.md), [Group By](group-by-entity-sql.md), [HAVING](having-entity-sql.md)ve [order by](order-by-entity-sql.md).  
  
## <a name="scope"></a>Kapsam  
 FROM yan tümcesinde tanımlanan adlar, KIMDEN kapsamında, soldan sağa doğru bir şekilde tanıtılmıştır. JOIN listesinde, ifadeler listede daha önce tanımlanan adlara başvurabilir. FROM yan tümcesinde tanımlanan öğelerin ortak özellikleri FROM kapsamına eklenmez: Her zaman diğer ad-nitelenmiş ad aracılığıyla başvurulmalıdır. Normal olarak, SELECT ifadesinin tüm parçaları FROM kapsamı içinde değerlendirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
