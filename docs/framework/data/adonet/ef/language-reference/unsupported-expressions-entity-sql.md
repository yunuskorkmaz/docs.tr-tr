---
description: 'Daha fazla bilgi edinin: desteklenmeyen ifadeler'
title: Desteklenmeyen Ifadeler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: ceb57dc78f9685a79de987d15f7fd57a583b75a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673303"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="5f13c-103">Desteklenmeyen ifadeler</span><span class="sxs-lookup"><span data-stu-id="5f13c-103">Unsupported expressions</span></span>

<span data-ttu-id="5f13c-104">Bu konuda ' de desteklenmeyen Transact-SQL ifadeleri açıklanmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5f13c-104">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="5f13c-105">Daha fazla bilgi için bkz. [Entity SQL Transact-SQL öğesinden farklı](how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5f13c-105">For more information, see [How Entity SQL Differs from Transact-SQL](how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="5f13c-106">Niceleştirilmiş koşullar</span><span class="sxs-lookup"><span data-stu-id="5f13c-106">Quantified predicates</span></span>

<span data-ttu-id="5f13c-107">Transact-SQL aşağıdaki formun yapılarına izin verir:</span><span class="sxs-lookup"><span data-stu-id="5f13c-107">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5f13c-108">Ancak, bu tür yapıları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5f13c-108">, however, does not support such constructs.</span></span> <span data-ttu-id="5f13c-109">Denk ifadeler ' de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki gibi yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="5f13c-109">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="5f13c-110">\* işleci</span><span class="sxs-lookup"><span data-stu-id="5f13c-110">\* operator</span></span>

<span data-ttu-id="5f13c-111">Transact-SQL, tüm sütunların yansıtıldığını göstermek için SELECT yan tümcesinde \* işlecinin kullanımını destekler. Bu, içinde desteklenmez [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5f13c-111">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="5f13c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f13c-112">See also</span></span>

- [<span data-ttu-id="5f13c-113">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5f13c-113">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="5f13c-114">Entity SQL ile Transact-SQL Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="5f13c-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)
