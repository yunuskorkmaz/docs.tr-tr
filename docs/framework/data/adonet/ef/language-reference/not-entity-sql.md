---
title: '! (Değİl) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 0b69d4cb64adc1f9232631d50ec42af0d1ba47e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150135"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="2c9e7-103">!</span><span class="sxs-lookup"><span data-stu-id="2c9e7-103">!</span></span> <span data-ttu-id="2c9e7-104">(Değİl) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="2c9e7-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="2c9e7-105">Bir `Boolean` ifadeyi inkar eder.</span><span class="sxs-lookup"><span data-stu-id="2c9e7-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c9e7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c9e7-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a><span data-ttu-id="2c9e7-107">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2c9e7-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="2c9e7-108">Boolean döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="2c9e7-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c9e7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c9e7-109">Remarks</span></span>  
 <span data-ttu-id="2c9e7-110">Ünlem işareti (!) NOT işleciyle aynı işlevsellik te sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2c9e7-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c9e7-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c9e7-111">Example</span></span>  
 <span data-ttu-id="2c9e7-112">Aşağıdaki Entity SQL sorgusu, bir `Boolean` ifadeyi geçersiz kışuklamak için NOT işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="2c9e7-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="2c9e7-113">Sorgu AdventureWorks Satış Modeli dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2c9e7-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2c9e7-114">Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2c9e7-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2c9e7-115">[YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="2c9e7-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2c9e7-116">Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="2c9e7-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="2c9e7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c9e7-117">See also</span></span>

- [<span data-ttu-id="2c9e7-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2c9e7-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
