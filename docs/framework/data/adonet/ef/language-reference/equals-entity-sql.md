---
description: 'Hakkında daha fazla bilgi edinin: = (eşittir) (Entity SQL)'
title: = (Eşittir) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 500c3fdde2377b3b5160436f23d051c2bcd0ee62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786413"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="1bd66-103">= (Eşittir) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1bd66-103">= (Equals) (Entity SQL)</span></span>

<span data-ttu-id="1bd66-104">İki ifadenin eşitliğini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="1bd66-104">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd66-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1bd66-105">Syntax</span></span>  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1bd66-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="1bd66-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="1bd66-107">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="1bd66-107">Any valid expression.</span></span> <span data-ttu-id="1bd66-108">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bd66-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="1bd66-109">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="1bd66-109">Result Types</span></span>  

 <span data-ttu-id="1bd66-110">`true` sol ifade sağ ifadeye eşitse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="1bd66-110">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bd66-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bd66-111">Remarks</span></span>  

 <span data-ttu-id="1bd66-112">= = İşleci = = ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="1bd66-112">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bd66-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bd66-113">Example</span></span>  

 <span data-ttu-id="1bd66-114">Aşağıdaki Entity SQL sorgusu iki ifadenin eşitliğini karşılaştırmak için = Comparison işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1bd66-114">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="1bd66-115">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="1bd66-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1bd66-116">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="1bd66-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1bd66-117">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="1bd66-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1bd66-118">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="1bd66-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="1bd66-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bd66-119">See also</span></span>

- [<span data-ttu-id="1bd66-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1bd66-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
