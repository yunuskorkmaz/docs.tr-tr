---
title: İç İçe Geçmiş Entity SQL Sorguları Oluşturma
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 3aa2e53b584eece9cc5e2d26791c78ffe33f9e35
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251143"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="b96aa-102">İç İçe Geçmiş Entity SQL Sorguları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b96aa-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b96aa-103">, zengin bir işlevsel dildir.</span><span class="sxs-lookup"><span data-stu-id="b96aa-103">is a rich functional language.</span></span> <span data-ttu-id="b96aa-104">Yapı Taşı [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="b96aa-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="b96aa-105">Geleneksel SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 'den farklı olarak tablosal sonuç kümesiyle sınırlı değildir: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değişmez değerler, parametreler veya iç içe geçmiş deyimlere sahip karmaşık ifadeler oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="b96aa-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="b96aa-106">İfadedeki bir değer parametreli olabilir veya başka bir ifadeden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="b96aa-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="b96aa-107">İç içe geçmiş Ifadeler</span><span class="sxs-lookup"><span data-stu-id="b96aa-107">Nested Expressions</span></span>  
 <span data-ttu-id="b96aa-108">İç içe geçmiş bir ifade, döndürdüğü türden bir değerin kabul edildiği her yerde yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b96aa-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="b96aa-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b96aa-109">For example:</span></span>  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="b96aa-110">İç içe geçmiş bir sorgu, bir izdüşüm yan tümcesine yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b96aa-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="b96aa-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b96aa-111">For example:</span></span>  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="b96aa-112">İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)], iç içe sorguların her zaman parantez içine alınması gerekir:</span><span class="sxs-lookup"><span data-stu-id="b96aa-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="b96aa-113">Aşağıdaki örnek, içindeki [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ifadelerin nasıl düzgün bir şekilde iç içe alınacağını gösterir: [Nasıl yapılır: Iki sorgunun](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))birleşimini sıralayın.</span><span class="sxs-lookup"><span data-stu-id="b96aa-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="b96aa-114">Yansıtmada iç içe geçmiş sorgular</span><span class="sxs-lookup"><span data-stu-id="b96aa-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="b96aa-115">Project yan tümcesindeki iç içe geçmiş sorgular, sunucuda Kartezyen ürün sorgularına çevrilebilir.</span><span class="sxs-lookup"><span data-stu-id="b96aa-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="b96aa-116">SLQ sunucusu dahil bazı arka uç sunucularında, bu, TempDB tablosunun çok büyük sürmesine neden olabilir ve bu da sunucu performansını olumsuz yönde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="b96aa-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="b96aa-117">Bu tür bir sorgunun örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b96aa-117">The following is an example of such a query:</span></span>  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="b96aa-118">Iç Içe sorguları sıralama</span><span class="sxs-lookup"><span data-stu-id="b96aa-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="b96aa-119">Entity Framework, iç içe geçmiş bir ifade sorgunun herhangi bir yerine yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b96aa-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="b96aa-120">Entity SQL sorguları yazarken harika esneklik sağladığından, iç içe geçmiş sorguların sıralamasını içeren bir sorgu yazmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b96aa-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="b96aa-121">Ancak, iç içe geçmiş bir sorgunun sırası korunmaz.</span><span class="sxs-lookup"><span data-stu-id="b96aa-121">However, the order of a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a><span data-ttu-id="b96aa-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b96aa-122">See also</span></span>

- [<span data-ttu-id="b96aa-123">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b96aa-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
