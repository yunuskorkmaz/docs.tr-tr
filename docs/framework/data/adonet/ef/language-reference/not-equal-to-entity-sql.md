---
title: '! = (Eşit değildir) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: bebe85072f5a2cf6a133b88c6d3f5c97299aa63f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191781"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="8a77a-102">! = (Eşit değildir) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8a77a-102">!= (Not Equal To) (Entity SQL)</span></span>

<span data-ttu-id="8a77a-103">Sol ifadenin sağ ifadeye eşit olup olmadığını anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="8a77a-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="8a77a-104">! = (Eşit değildir) işleci, <> işlecine işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8a77a-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a77a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8a77a-105">Syntax</span></span>  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8a77a-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="8a77a-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="8a77a-107">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="8a77a-107">Any valid expression.</span></span> <span data-ttu-id="8a77a-108">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a77a-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8a77a-109">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="8a77a-109">Result Types</span></span>  

 <span data-ttu-id="8a77a-110">`true` sol ifade sağ ifadeye eşit değilse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="8a77a-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a77a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a77a-111">Example</span></span>  

 <span data-ttu-id="8a77a-112">Aşağıdaki Entity SQL sorgusu, sol ifadenin sağ ifadeye eşit olup olmadığını belirleyebilmek üzere iki ifadeyi karşılaştırmak için! = işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a77a-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="8a77a-113">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="8a77a-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8a77a-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="8a77a-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8a77a-115">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="8a77a-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="8a77a-116">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="8a77a-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="8a77a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a77a-117">See also</span></span>

- [<span data-ttu-id="8a77a-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8a77a-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
