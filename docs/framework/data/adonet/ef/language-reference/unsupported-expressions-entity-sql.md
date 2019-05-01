---
title: Desteklenmeyen ifadeler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: a47ff46ca99a84500bc5dfecc19bb31652e9b4b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034079"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="51ab0-102">Desteklenmeyen ifadeler</span><span class="sxs-lookup"><span data-stu-id="51ab0-102">Unsupported expressions</span></span>

<span data-ttu-id="51ab0-103">Bu konu başlığı altında açıklanır [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] desteklenmeyen ifadeler [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51ab0-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="51ab0-104">Daha fazla bilgi için [varlık SQL farkı Transact-SQL'in](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="51ab0-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="51ab0-105">Sayısal doğrulamaları</span><span class="sxs-lookup"><span data-stu-id="51ab0-105">Quantified predicates</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="51ab0-106">aşağıdaki biçimde yapıları sağlar:</span><span class="sxs-lookup"><span data-stu-id="51ab0-106">allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="51ab0-107">, ancak bu yapıları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="51ab0-107">, however, does not support such constructs.</span></span> <span data-ttu-id="51ab0-108">Eşdeğer ifade yazılabilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] gibi:</span><span class="sxs-lookup"><span data-stu-id="51ab0-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="51ab0-109">\* işleci</span><span class="sxs-lookup"><span data-stu-id="51ab0-109">\* operator</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="51ab0-110">destekler \* tüm sütunları dışarı öngörülen olduğunu belirtmek için SELECT yan tümcesinde işleci. Bu desteklenmeyen [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51ab0-110">supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="51ab0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51ab0-111">See also</span></span>

- [<span data-ttu-id="51ab0-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="51ab0-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="51ab0-113">Entity SQL ile Transact-SQL Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="51ab0-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
