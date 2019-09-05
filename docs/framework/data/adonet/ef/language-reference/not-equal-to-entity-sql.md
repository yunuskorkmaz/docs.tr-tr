---
title: '! = (Eşit değildir) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: c2ccadaa5801cac9c10241108f02ade223a8697f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249847"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="a65da-102">! = (Eşit değildir) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a65da-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="a65da-103">Sol ifadenin sağ ifadeye eşit olup olmadığını anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="a65da-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="a65da-104">! = (Eşit değildir) işleci, < > işlecine işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="a65da-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a65da-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a65da-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a65da-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="a65da-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a65da-107">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="a65da-107">Any valid expression.</span></span> <span data-ttu-id="a65da-108">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a65da-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a65da-109">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="a65da-109">Result Types</span></span>  
 <span data-ttu-id="a65da-110">`true`sol ifade sağ ifadeye eşit değilse; Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="a65da-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a65da-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a65da-111">Example</span></span>  
 <span data-ttu-id="a65da-112">Aşağıdaki Entity SQL sorgusu, sol ifadenin sağ ifadeye eşit olup olmadığını belirleyebilmek üzere iki ifadeyi karşılaştırmak için! = işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a65da-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="a65da-113">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="a65da-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a65da-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="a65da-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a65da-115">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="a65da-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a65da-116">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="a65da-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="a65da-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a65da-117">See also</span></span>

- [<span data-ttu-id="a65da-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a65da-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
