---
title: Desteklenmeyen ifadeleri (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: bf20bb92010d5031e973cb1cc004b6b8f13d0091
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="unsupported-expressions"></a><span data-ttu-id="00325-102">Desteklenmeyen ifadeler</span><span class="sxs-lookup"><span data-stu-id="00325-102">Unsupported expressions</span></span>

<span data-ttu-id="00325-103">Bu konuda açıklanmaktadır [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] desteklenmez ifadeler [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00325-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="00325-104">Daha fazla bilgi için bkz: [varlık SQL farklı Transact-SQL olarak](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="00325-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="00325-105">Quantified koşulları</span><span class="sxs-lookup"><span data-stu-id="00325-105">Quantified predicates</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="00325-106"> aşağıdaki biçimde yapıları sağlar:</span><span class="sxs-lookup"><span data-stu-id="00325-106"> allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="00325-107">, ancak böyle yapıları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="00325-107">, however, does not support such constructs.</span></span> <span data-ttu-id="00325-108">Eşdeğer ifade yazılabilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] gibi:</span><span class="sxs-lookup"><span data-stu-id="00325-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="00325-109">\* işleci</span><span class="sxs-lookup"><span data-stu-id="00325-109">\* operator</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="00325-110"> kullanımını destekleyen \* tüm sütunları kullanıma öngörülen belirtmek için SELECT yan tümcesinde işleci. Bu desteklenmeyen [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00325-110"> supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="00325-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00325-111">See also</span></span>

[<span data-ttu-id="00325-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="00325-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[<span data-ttu-id="00325-113">Entity SQL ile Transact-SQL Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="00325-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
