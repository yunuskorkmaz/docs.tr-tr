---
title: Desteklenmeyen Ifadeler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: 956fe117eb0c59392c3999046bc70deaed268ac6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248775"
---
# <a name="unsupported-expressions"></a>Desteklenmeyen ifadeler

Bu konuda ' de [!INCLUDE[esql](../../../../../../includes/esql-md.md)]desteklenmeyen Transact-SQL ifadeleri açıklanmaktadır. Daha fazla bilgi için bkz. [Entity SQL Transact-SQL öğesinden farklı](how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Niceleştirilmiş koşullar

Transact-SQL aşağıdaki formun yapılarına izin verir:

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Ancak, bu tür yapıları desteklemez. Denk ifadeler ' de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki gibi yazılabilir:

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>* işleci

Transact-SQL, tüm sütunların yansıtıldığını göstermek için SELECT yan tümcesinde * işlecinin kullanımını destekler. Bu, içinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)]desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [Entity SQL ile Transact-SQL Arasındaki Farklar](how-entity-sql-differs-from-transact-sql.md)
