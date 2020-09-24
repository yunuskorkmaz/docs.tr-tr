---
title: = (Eşittir) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 31299670d9f47ed7672b980a3415b8d214463b8e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148093"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="feedf-102">= (Eşittir) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="feedf-102">= (Equals) (Entity SQL)</span></span>

<span data-ttu-id="feedf-103">İki ifadenin eşitliğini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="feedf-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feedf-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="feedf-104">Syntax</span></span>  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="feedf-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="feedf-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="feedf-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="feedf-106">Any valid expression.</span></span> <span data-ttu-id="feedf-107">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="feedf-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="feedf-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="feedf-108">Result Types</span></span>  

 <span data-ttu-id="feedf-109">`true` sol ifade sağ ifadeye eşitse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="feedf-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="feedf-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="feedf-110">Remarks</span></span>  

 <span data-ttu-id="feedf-111">= = İşleci = = ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="feedf-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feedf-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="feedf-112">Example</span></span>  

 <span data-ttu-id="feedf-113">Aşağıdaki Entity SQL sorgusu iki ifadenin eşitliğini karşılaştırmak için = Comparison işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="feedf-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="feedf-114">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="feedf-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="feedf-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="feedf-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="feedf-116">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="feedf-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="feedf-117">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="feedf-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="feedf-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="feedf-118">See also</span></span>

- [<span data-ttu-id="feedf-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="feedf-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
