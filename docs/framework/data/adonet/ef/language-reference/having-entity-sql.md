---
title: (Varlık SQL) sahip
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 75f30c19fb54d66be0e460ab64b61d283d650005
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764391"
---
# <a name="having-entity-sql"></a><span data-ttu-id="915a3-102">(Varlık SQL) sahip</span><span class="sxs-lookup"><span data-stu-id="915a3-102">HAVING (Entity SQL)</span></span>
<span data-ttu-id="915a3-103">Bir grup veya bir toplama için bir arama koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="915a3-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="915a3-104">Syntax</span></span>  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="915a3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="915a3-105">Arguments</span></span>  
 `search_condition`  
 <span data-ttu-id="915a3-106">Grup veya toplama karşılamak arama koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="915a3-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="915a3-107">HAVING GROUP BY ALL ile kullanıldığında, HAVING yan tümcesi tüm geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="915a3-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="915a3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="915a3-108">Remarks</span></span>  
 <span data-ttu-id="915a3-109">HAVING yan tümcesi bir gruplandırma sonucu üzerinde ek bir filtre koşulu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="915a3-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="915a3-110">Hiçbir GROUP BY yan tümcesi sorgu ifadesinde belirtilirse, örtük bir tek kümesi grubu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="915a3-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="915a3-111">HAVING, yalnızca kullanılabilir [seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="915a3-111">HAVING can be used only with the [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statement.</span></span> <span data-ttu-id="915a3-112">Zaman [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) olan kullanılmaz, HAVING WHERE yan tümcesi gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="915a3-112">When [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
 <span data-ttu-id="915a3-113">HAVING yan tümcesi WHERE yan tümcesi gibi çalışır GROUP BY işleminden sonra uygulanır.</span><span class="sxs-lookup"><span data-stu-id="915a3-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="915a3-114">Bu, HAVING yan tümcesi yalnızca diğer adlar ve toplamalar, gruplandırma başvurular aşağıdaki örnekte gösterildiği gibi yapabileceğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="915a3-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example.</span></span>  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="915a3-115">Önceki grupları yalnızca için birden fazla ürün içeren kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="915a3-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="915a3-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="915a3-116">Example</span></span>  
 <span data-ttu-id="915a3-117">Aşağıdaki varlık SQL sorgusunu HAVING ve GROUP BY işleçleri bir grup veya bir toplama için bir arama koşulu belirtmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="915a3-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="915a3-118">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="915a3-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="915a3-119">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="915a3-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="915a3-120">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="915a3-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="915a3-121">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="915a3-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a><span data-ttu-id="915a3-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="915a3-122">See Also</span></span>  
 [<span data-ttu-id="915a3-123">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="915a3-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="915a3-124">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="915a3-124">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
