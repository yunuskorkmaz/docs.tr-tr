---
description: Hakkında daha fazla bilgi edinin:-(negatif) (Entity SQL)
title: '- Negatif (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: f3d30ce36b95e44755d148dc06279f67f15b0664
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712889"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="e9302-103">-(Negatif) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e9302-103">- (Negative) (Entity SQL)</span></span>

<span data-ttu-id="e9302-104">Sayısal bir ifadenin değerinin negatifini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9302-104">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9302-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e9302-105">Syntax</span></span>  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e9302-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="e9302-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="e9302-107">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="e9302-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e9302-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="e9302-108">Result Types</span></span>  

 <span data-ttu-id="e9302-109">Veri türü `expression` .</span><span class="sxs-lookup"><span data-stu-id="e9302-109">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9302-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9302-110">Remarks</span></span>  

 <span data-ttu-id="e9302-111">`expression`İmzasız bir tür ise, sonuç türü, türü ile en yakından ilişkili olan imzalı tür olur `expression` .</span><span class="sxs-lookup"><span data-stu-id="e9302-111">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="e9302-112">Örneğin, `expression` byte türünde ise, Int16 türünde bir değer döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e9302-112">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9302-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9302-113">Example</span></span>  

 <span data-ttu-id="e9302-114">Aşağıdaki Entity SQL sorgusu, bir sayısal ifadenin değerinin negatifini döndürmek için-aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9302-114">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="e9302-115">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="e9302-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e9302-116">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="e9302-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e9302-117">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="e9302-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e9302-118">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="e9302-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="e9302-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9302-119">See also</span></span>

- [<span data-ttu-id="e9302-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e9302-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
