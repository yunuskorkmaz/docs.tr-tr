---
title: + (Ekle)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: b86d273658362c3bb204d5220ff5e9db1f8de9fe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198060"
---
# <a name="-add"></a><span data-ttu-id="fa779-102">+ (Ekle)</span><span class="sxs-lookup"><span data-stu-id="fa779-102">+ (Add)</span></span>

<span data-ttu-id="fa779-103">İki sayı ekler.</span><span class="sxs-lookup"><span data-stu-id="fa779-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa779-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fa779-104">Syntax</span></span>  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="fa779-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="fa779-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="fa779-106">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="fa779-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fa779-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="fa779-107">Result Types</span></span>  

 <span data-ttu-id="fa779-108">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="fa779-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="fa779-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fa779-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa779-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa779-110">Remarks</span></span>  

 <span data-ttu-id="fa779-111">EDM için. Dize türleri, ekleme birleştirme.</span><span class="sxs-lookup"><span data-stu-id="fa779-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa779-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa779-112">Example</span></span>  

 <span data-ttu-id="fa779-113">Aşağıdaki Entity SQL sorgusu iki sayı eklemek için + aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa779-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="fa779-114">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="fa779-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fa779-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="fa779-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="fa779-116">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="fa779-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="fa779-117">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="fa779-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="fa779-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa779-118">See also</span></span>

- [<span data-ttu-id="fa779-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fa779-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="fa779-120">Kavramsal model türleri (CSDL)</span><span class="sxs-lookup"><span data-stu-id="fa779-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
