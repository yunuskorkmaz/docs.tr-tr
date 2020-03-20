---
title: İç İçe Geçmiş Entity SQL Sorguları Oluşturma
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 6b2fc9a32fc30d205b9c33257bf98781cfa07499
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150395"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="ad8a4-102">İç İçe Geçmiş Entity SQL Sorguları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad8a4-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="ad8a4-103">zengin bir fonksiyonel dildir.</span><span class="sxs-lookup"><span data-stu-id="ad8a4-103">is a rich functional language.</span></span> <span data-ttu-id="ad8a4-104">Yapı taşı [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir deyimdir.</span><span class="sxs-lookup"><span data-stu-id="ad8a4-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="ad8a4-105">Geleneksel SQL'in aksine, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir tabular [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sonuç kümesiyle sınırlı değildir: gerçek, parametre veya iç içe geçmiş ifadelere sahip karmaşık ifadeler oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="ad8a4-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="ad8a4-106">İfadedeki bir değer parametreli veya başka bir ifadeden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="ad8a4-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="ad8a4-107">İç Içe İfadeler</span><span class="sxs-lookup"><span data-stu-id="ad8a4-107">Nested Expressions</span></span>  
 <span data-ttu-id="ad8a4-108">İç içe bir ifade, döndürdettiği türün değerinin kabul edildiği herhangi bir yere yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ad8a4-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="ad8a4-109">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ad8a4-109">For example:</span></span>  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="ad8a4-110">İç içe bir sorgu bir projeksiyon yan tümcesine yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ad8a4-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="ad8a4-111">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ad8a4-111">For example:</span></span>  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="ad8a4-112">İç [!INCLUDE[esql](../../../../../../includes/esql-md.md)]içe gelen sorgular her zaman parantez içinde eklenmelidir:</span><span class="sxs-lookup"><span data-stu-id="ad8a4-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="ad8a4-113">Aşağıdaki örnek, ifadelerin düzgün bir şekilde [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nasıl yuvaya yerleşdirilir: [İki Sorgu Birliği'ni sırala.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ad8a4-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="ad8a4-114">Projeksiyonda İç Içe Sorgular</span><span class="sxs-lookup"><span data-stu-id="ad8a4-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="ad8a4-115">Proje yan tümcesindeki iç içe sorgular, sunucudaki Kartezyen ürün sorgularına çevrilebilir.</span><span class="sxs-lookup"><span data-stu-id="ad8a4-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="ad8a4-116">SQL Server da dahil olmak üzere bazı arka uç sunucularında, bu durum TempDB tablosunun çok büyük olmasını sağlayabilir ve bu da sunucu performansını olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="ad8a4-116">In some backend servers, including SQL Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="ad8a4-117">Aşağıdaki tür bir sorgu örneğidir:</span><span class="sxs-lookup"><span data-stu-id="ad8a4-117">The following is an example of such a query:</span></span>  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="ad8a4-118">İç Içe Sorguları Sıralama</span><span class="sxs-lookup"><span data-stu-id="ad8a4-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="ad8a4-119">Varlık Çerçevesi'nde, iç içe bir ifade sorgunun herhangi bir yerine yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ad8a4-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="ad8a4-120">Entity SQL sorguları yazarken büyük esneklik sağladığından, iç içe sorgu sırasını içeren bir sorgu yazmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ad8a4-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="ad8a4-121">Ancak, iç içe sorgu sırası korunmaz.</span><span class="sxs-lookup"><span data-stu-id="ad8a4-121">However, the order of a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad8a4-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad8a4-122">See also</span></span>

- [<span data-ttu-id="ad8a4-123">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ad8a4-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
