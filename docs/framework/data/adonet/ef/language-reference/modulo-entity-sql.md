---
description: 'Daha fazla bilgi edinin: (modül) (Entity SQL)'
title: Modül (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 8ac9bf2fa9dbee843215dcfeed13fefc7bd54796
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696639"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="1859b-103">Modül (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1859b-103">(Modulo) (Entity SQL)</span></span>

<span data-ttu-id="1859b-104">Bir ifadenin kalan kısmını başka bir ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="1859b-104">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1859b-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1859b-105">Syntax</span></span>  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="1859b-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="1859b-106">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="1859b-107">Bölünecek sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="1859b-107">The numeric expression to divide.</span></span> <span data-ttu-id="1859b-108">`dividend` , herhangi bir sayısal veri türü için geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="1859b-108">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="1859b-109">Bölüneni bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="1859b-109">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="1859b-110">`divisor` , herhangi bir sayısal veri türü için geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="1859b-110">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="1859b-111">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="1859b-111">Result Types</span></span>  

 <span data-ttu-id="1859b-112">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="1859b-112">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="1859b-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="1859b-113">Example</span></span>  

 <span data-ttu-id="1859b-114">Aşağıdaki Entity SQL sorgusu, bir ifadenin kalan kısmını başka bir ifade döndürmek için% aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1859b-114">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="1859b-115">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="1859b-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1859b-116">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="1859b-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1859b-117">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="1859b-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1859b-118">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="1859b-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="1859b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1859b-119">See also</span></span>

- [<span data-ttu-id="1859b-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1859b-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
