---
title: Desteklenmeyen ifadeler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: a47ff46ca99a84500bc5dfecc19bb31652e9b4b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628028"
---
# <a name="unsupported-expressions"></a>Desteklenmeyen ifadeler

Bu konu başlığı altında açıklanır [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] desteklenmeyen ifadeler [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Daha fazla bilgi için [varlık SQL farkı Transact-SQL'in](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Sayısal doğrulamaları

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] aşağıdaki biçimde yapıları sağlar:

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

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] destekler * tüm sütunları dışarı öngörülen olduğunu belirtmek için SELECT yan tümcesinde işleci. Bu desteklenmeyen [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Entity SQL ile Transact-SQL Arasındaki Farklar](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
