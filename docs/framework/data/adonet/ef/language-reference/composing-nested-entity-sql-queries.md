---
title: İç içe geçmiş Entity SQL sorguları oluşturma
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: b5fc39a25b5b8592117348b150da9d82454a1562
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827324"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="f824c-102">İç içe geçmiş Entity SQL sorguları oluşturma</span><span class="sxs-lookup"><span data-stu-id="f824c-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f824c-103">bir zengin işlevsel bir dildir.</span><span class="sxs-lookup"><span data-stu-id="f824c-103">is a rich functional language.</span></span> <span data-ttu-id="f824c-104">Yapı bloğu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="f824c-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="f824c-105">Geleneksel SQL aksine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tablosal sonuçtaki kümesine sınırlı değildir: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değişmez değerleri, parametre veya iç içe geçmiş deyimler olabilir karmaşık ifadeleri oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="f824c-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="f824c-106">İfade bir değer parametreli veya başka bir ifadenin oluşur.</span><span class="sxs-lookup"><span data-stu-id="f824c-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="f824c-107">İç içe geçmiş deyimler</span><span class="sxs-lookup"><span data-stu-id="f824c-107">Nested Expressions</span></span>  
 <span data-ttu-id="f824c-108">İç içe geçmiş bir ifade kabul döndürür türünde bir değer herhangi bir yerde yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f824c-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="f824c-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f824c-109">For example:</span></span>  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="f824c-110">İç içe yerleştirilmiş sorguda projeksiyon yan tümcesinde yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f824c-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="f824c-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f824c-111">For example:</span></span>  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="f824c-112">İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)], iç içe geçmiş sorgular parantez içinde her zaman alınmalıdır:</span><span class="sxs-lookup"><span data-stu-id="f824c-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="f824c-113">Aşağıdaki örnek düzgün ifadeleri iç içe gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [Nasıl Yapılır: UNION iki sorgunun sipariş](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f824c-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="f824c-114">İç içe geçmiş sorgularda projeksiyonu</span><span class="sxs-lookup"><span data-stu-id="f824c-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="f824c-115">Proje yan tümcesi iç içe geçmiş sorgularda sunucuda Kartezyen ürün sorgulara çevrilmiş.</span><span class="sxs-lookup"><span data-stu-id="f824c-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="f824c-116">SQL Server dahil olmak üzere bazı arka uç sunucular bu sunucu performansını olumsuz etkileyebilir, çok büyük almak TempDB tablodaki neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f824c-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="f824c-117">Bu tür bir sorgu örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f824c-117">The following is an example of such a query:</span></span>  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="f824c-118">İç içe geçmiş sorgular sıralama</span><span class="sxs-lookup"><span data-stu-id="f824c-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="f824c-119">Varlık Çerçevesi'nde, iç içe geçmiş bir ifade herhangi bir sorguda yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f824c-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="f824c-120">Entity SQL sorguları yazma büyük esneklik izin verdiğinden, bir iç içe geçmiş sorguları sıralamasını içeren bir sorgu yazmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f824c-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="f824c-121">Ancak, iç içe bir sorgu sırasını korunmaz.</span><span class="sxs-lookup"><span data-stu-id="f824c-121">However, the order of a nested query is not preserved.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f824c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f824c-122">See also</span></span>
- [<span data-ttu-id="f824c-123">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f824c-123">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
