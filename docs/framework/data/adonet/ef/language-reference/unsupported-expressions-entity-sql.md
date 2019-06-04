---
title: Desteklenmeyen ifadeler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: af0e00f470584883b6a65b63f2650c1c359b404c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489862"
---
# <a name="unsupported-expressions"></a>Desteklenmeyen ifadeler

Bu konu, desteklenmeyen Transact-SQL deyimleri açıklar [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Daha fazla bilgi için [varlık SQL farkı Transact-SQL'in](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Sayısal doğrulamaları

Transact-SQL, yapıları aşağıdaki biçime sağlar:

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)], ancak bu yapıları desteklemez. Eşdeğer ifade yazılabilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] gibi:

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>* işleci

Transact-SQL kullanılmasını desteklediği * tüm sütunları dışarı öngörülen olduğunu belirtmek için SELECT yan tümcesinde işleci. Bu desteklenmeyen [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Entity SQL ile Transact-SQL Arasındaki Farklar](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
