---
description: Hakkında daha fazla bilgi edinin:! = (eşit değildir) (Entity SQL)
title: '! = (Eşit değildir) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: a7a96606fb1834b757253948c3a0d2cde11893dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696405"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="00510-103">! = (Eşit değildir) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="00510-103">!= (Not Equal To) (Entity SQL)</span></span>

<span data-ttu-id="00510-104">Sol ifadenin sağ ifadeye eşit olup olmadığını anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="00510-104">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="00510-105">! = (Eşit değildir) işleci, <> işlecine işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="00510-105">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00510-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="00510-106">Syntax</span></span>  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="00510-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="00510-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="00510-108">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="00510-108">Any valid expression.</span></span> <span data-ttu-id="00510-109">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00510-109">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="00510-110">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="00510-110">Result Types</span></span>  

 <span data-ttu-id="00510-111">`true` sol ifade sağ ifadeye eşit değilse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="00510-111">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00510-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="00510-112">Example</span></span>  

 <span data-ttu-id="00510-113">Aşağıdaki Entity SQL sorgusu, sol ifadenin sağ ifadeye eşit olup olmadığını belirleyebilmek üzere iki ifadeyi karşılaştırmak için! = işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="00510-113">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="00510-114">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="00510-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="00510-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="00510-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="00510-116">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="00510-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="00510-117">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="00510-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="00510-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00510-118">See also</span></span>

- [<span data-ttu-id="00510-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="00510-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
