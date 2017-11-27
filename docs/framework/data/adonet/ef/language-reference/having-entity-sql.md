---
title: "(Varlık SQL) sahip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a64bc0c9b5e1358046e78429780af796f60e404e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="having-entity-sql"></a><span data-ttu-id="a68f7-102">(Varlık SQL) sahip</span><span class="sxs-lookup"><span data-stu-id="a68f7-102">HAVING (Entity SQL)</span></span>
<span data-ttu-id="a68f7-103">Bir grup veya bir toplama için bir arama koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a68f7-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a68f7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a68f7-104">Syntax</span></span>  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a68f7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a68f7-105">Arguments</span></span>  
 `search_condition`  
 <span data-ttu-id="a68f7-106">Grup veya toplama karşılamak arama koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a68f7-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="a68f7-107">HAVING GROUP BY ALL ile kullanıldığında, HAVING yan tümcesi tüm geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a68f7-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a68f7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a68f7-108">Remarks</span></span>  
 <span data-ttu-id="a68f7-109">HAVING yan tümcesi bir gruplandırma sonucu üzerinde ek bir filtre koşulu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a68f7-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="a68f7-110">Hiçbir GROUP BY yan tümcesi sorgu ifadesinde belirtilirse, örtük bir tek kümesi grubu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a68f7-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a68f7-111">HAVING, yalnızca kullanılabilir [seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="a68f7-111">HAVING can be used only with the [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statement.</span></span> <span data-ttu-id="a68f7-112">Zaman [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) olan kullanılmaz, HAVING WHERE yan tümcesi gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="a68f7-112">When [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
 <span data-ttu-id="a68f7-113">HAVING yan tümcesi WHERE yan tümcesi gibi çalışır GROUP BY işleminden sonra uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a68f7-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="a68f7-114">Bu, HAVING yan tümcesi yalnızca diğer adlar ve toplamalar, gruplandırma başvurular aşağıdaki örnekte gösterildiği gibi yapabileceğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a68f7-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example.</span></span>  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="a68f7-115">Önceki grupları yalnızca için birden fazla ürün içeren kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="a68f7-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a68f7-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="a68f7-116">Example</span></span>  
 <span data-ttu-id="a68f7-117">Aşağıdaki varlık SQL sorgusunu HAVING ve GROUP BY işleçleri bir grup veya bir toplama için bir arama koşulu belirtmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a68f7-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="a68f7-118">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="a68f7-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a68f7-119">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="a68f7-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a68f7-120">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a68f7-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="a68f7-121">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a68f7-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a><span data-ttu-id="a68f7-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a68f7-122">See Also</span></span>  
 [<span data-ttu-id="a68f7-123">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a68f7-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="a68f7-124">Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="a68f7-124">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
