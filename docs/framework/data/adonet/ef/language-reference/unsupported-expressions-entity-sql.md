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
# <a name="unsupported-expressions"></a><span data-ttu-id="0434b-102">Desteklenmeyen ifadeler</span><span class="sxs-lookup"><span data-stu-id="0434b-102">Unsupported expressions</span></span>

<span data-ttu-id="0434b-103">Bu konu, desteklenmeyen Transact-SQL deyimleri açıklar [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0434b-103">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="0434b-104">Daha fazla bilgi için [varlık SQL farkı Transact-SQL'in](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0434b-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="0434b-105">Sayısal doğrulamaları</span><span class="sxs-lookup"><span data-stu-id="0434b-105">Quantified predicates</span></span>

<span data-ttu-id="0434b-106">Transact-SQL, yapıları aşağıdaki biçime sağlar:</span><span class="sxs-lookup"><span data-stu-id="0434b-106">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="0434b-107">, ancak bu yapıları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0434b-107">, however, does not support such constructs.</span></span> <span data-ttu-id="0434b-108">Eşdeğer ifade yazılabilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] gibi:</span><span class="sxs-lookup"><span data-stu-id="0434b-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="0434b-109">\* işleci</span><span class="sxs-lookup"><span data-stu-id="0434b-109">\* operator</span></span>

<span data-ttu-id="0434b-110">Transact-SQL kullanılmasını desteklediği \* tüm sütunları dışarı öngörülen olduğunu belirtmek için SELECT yan tümcesinde işleci. Bu desteklenmeyen [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0434b-110">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="0434b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0434b-111">See also</span></span>

- [<span data-ttu-id="0434b-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0434b-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="0434b-113">Entity SQL ile Transact-SQL Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="0434b-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
