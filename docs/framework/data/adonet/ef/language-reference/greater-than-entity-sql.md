---
description: 'Hakkında daha fazla bilgi edinin: > (büyüktür) (Entity SQL)'
title: '> (Büyüktür) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: e14470d477336fd719bb419657af3fdadcd54d98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786296"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="6fd9f-103">> (büyüktür) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6fd9f-103">> (Greater Than) (Entity SQL)</span></span>

<span data-ttu-id="6fd9f-104">Sol ifadenin sağ ifadeden daha büyük bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="6fd9f-104">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fd9f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6fd9f-105">Syntax</span></span>  
  
```sql  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="6fd9f-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="6fd9f-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="6fd9f-107">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="6fd9f-107">Any valid expression.</span></span> <span data-ttu-id="6fd9f-108">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6fd9f-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="6fd9f-109">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="6fd9f-109">Result Types</span></span>  

 <span data-ttu-id="6fd9f-110">`true` sol ifade sağ ifadeden daha büyük bir değere sahipse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="6fd9f-110">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fd9f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="6fd9f-111">Example</span></span>  

 <span data-ttu-id="6fd9f-112">Aşağıdaki Entity SQL sorgusu, sol ifadenin sağ ifadeden daha büyük bir değere sahip olup olmadığını belirleyecek iki ifadeyi karşılaştırmak için > karşılaştırma işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6fd9f-112">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="6fd9f-113">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="6fd9f-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6fd9f-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="6fd9f-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6fd9f-115">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="6fd9f-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6fd9f-116">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="6fd9f-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="6fd9f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fd9f-117">See also</span></span>

- [<span data-ttu-id="6fd9f-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6fd9f-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
