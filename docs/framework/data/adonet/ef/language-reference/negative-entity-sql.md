---
title: '- Negatif (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 7716b9115587a873531be9c14b7da93c7a148ed8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319531"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="09024-102">-(Negatif) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="09024-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="09024-103">Sayısal bir ifadenin değerinin negatifini döndürür.</span><span class="sxs-lookup"><span data-stu-id="09024-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09024-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09024-104">Syntax</span></span>  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="09024-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="09024-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="09024-106">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="09024-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="09024-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="09024-107">Result Types</span></span>  
 <span data-ttu-id="09024-108">@No__t-0 ' ın veri türü.</span><span class="sxs-lookup"><span data-stu-id="09024-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09024-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09024-109">Remarks</span></span>  
 <span data-ttu-id="09024-110">@No__t-0 işaretsiz bir tür ise, sonuç türü, `expression` türü ile en yakından ilişkili olan imzalı tür olur.</span><span class="sxs-lookup"><span data-stu-id="09024-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="09024-111">Örneğin, `expression` bayt türünde ise, Int16 türünde bir değer döndürülür.</span><span class="sxs-lookup"><span data-stu-id="09024-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09024-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="09024-112">Example</span></span>  
 <span data-ttu-id="09024-113">Aşağıdaki Entity SQL sorgusu, bir sayısal ifadenin değerinin negatifini döndürmek için-aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="09024-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="09024-114">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="09024-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="09024-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="09024-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="09024-116">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="09024-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="09024-117">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="09024-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="09024-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09024-118">See also</span></span>

- [<span data-ttu-id="09024-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="09024-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
