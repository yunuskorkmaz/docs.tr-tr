---
title: '- Negatif (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 71749dab073fade854c2a494841e3f6b408ebd1d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204417"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="e712c-102">-(Negatif) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e712c-102">- (Negative) (Entity SQL)</span></span>

<span data-ttu-id="e712c-103">Sayısal bir ifadenin değerinin negatifini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e712c-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e712c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e712c-104">Syntax</span></span>  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e712c-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="e712c-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="e712c-106">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="e712c-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e712c-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="e712c-107">Result Types</span></span>  

 <span data-ttu-id="e712c-108">Veri türü `expression` .</span><span class="sxs-lookup"><span data-stu-id="e712c-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e712c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e712c-109">Remarks</span></span>  

 <span data-ttu-id="e712c-110">`expression`İmzasız bir tür ise, sonuç türü, türü ile en yakından ilişkili olan imzalı tür olur `expression` .</span><span class="sxs-lookup"><span data-stu-id="e712c-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="e712c-111">Örneğin, `expression` byte türünde ise, Int16 türünde bir değer döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e712c-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e712c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="e712c-112">Example</span></span>  

 <span data-ttu-id="e712c-113">Aşağıdaki Entity SQL sorgusu, bir sayısal ifadenin değerinin negatifini döndürmek için-aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e712c-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="e712c-114">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="e712c-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e712c-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="e712c-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e712c-116">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="e712c-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e712c-117">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="e712c-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="e712c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e712c-118">See also</span></span>

- [<span data-ttu-id="e712c-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e712c-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
