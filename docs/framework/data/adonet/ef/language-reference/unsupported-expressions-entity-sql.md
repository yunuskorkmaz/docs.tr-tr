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
# <a name="unsupported-expressions"></a><span data-ttu-id="921e5-102">Desteklenmeyen ifadeler</span><span class="sxs-lookup"><span data-stu-id="921e5-102">Unsupported expressions</span></span>

<span data-ttu-id="921e5-103">Bu konuda ' de [!INCLUDE[esql](../../../../../../includes/esql-md.md)]desteklenmeyen Transact-SQL ifadeleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="921e5-103">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="921e5-104">Daha fazla bilgi için bkz. [Entity SQL Transact-SQL öğesinden farklı](how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="921e5-104">For more information, see [How Entity SQL Differs from Transact-SQL](how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="921e5-105">Niceleştirilmiş koşullar</span><span class="sxs-lookup"><span data-stu-id="921e5-105">Quantified predicates</span></span>

<span data-ttu-id="921e5-106">Transact-SQL aşağıdaki formun yapılarına izin verir:</span><span class="sxs-lookup"><span data-stu-id="921e5-106">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="921e5-107">Ancak, bu tür yapıları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="921e5-107">, however, does not support such constructs.</span></span> <span data-ttu-id="921e5-108">Denk ifadeler ' de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki gibi yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="921e5-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="921e5-109">\* işleci</span><span class="sxs-lookup"><span data-stu-id="921e5-109">\* operator</span></span>

<span data-ttu-id="921e5-110">Transact-SQL, tüm sütunların yansıtıldığını göstermek için SELECT yan tümcesinde \* işlecinin kullanımını destekler. Bu, içinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)]desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="921e5-110">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="921e5-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="921e5-111">See also</span></span>

- [<span data-ttu-id="921e5-112">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="921e5-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="921e5-113">Entity SQL ile Transact-SQL Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="921e5-113">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)
