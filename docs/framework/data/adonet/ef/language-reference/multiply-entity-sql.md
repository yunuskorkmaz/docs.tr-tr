---
title: '* Bilirsiniz (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 3dd77270e6765a0431dc473bbbcadeb6481a4699
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175661"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="81729-102">\* (Çarp) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="81729-102">\* (Multiply) (Entity SQL)</span></span>

<span data-ttu-id="81729-103">İki ifadeyi çarpar.</span><span class="sxs-lookup"><span data-stu-id="81729-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81729-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="81729-104">Syntax</span></span>  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="81729-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="81729-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="81729-106">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="81729-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="81729-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="81729-107">Result Types</span></span>  

 <span data-ttu-id="81729-108">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="81729-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="81729-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="81729-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81729-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="81729-110">Example</span></span>  

 <span data-ttu-id="81729-111">Aşağıdaki Entity SQL sorgusu iki sayıyı çarpmak için \* aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="81729-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="81729-112">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="81729-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="81729-113">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="81729-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="81729-114">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="81729-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="81729-115">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="81729-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="81729-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81729-116">See also</span></span>

- [<span data-ttu-id="81729-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="81729-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
